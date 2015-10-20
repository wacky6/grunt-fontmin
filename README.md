grunt-fontmin
===
grunt plugin to minimize Chinese fonts

## Configuration
```JavaScript
grunt.initConfig({
  fontmin: {
    options: {
      dest:    'www-bin/fonts/',  // default './'
      basedir: 'fonts/'           // default './'
    },
    '{Source-hans*.otf}': {
      /* getText: (html) => string_of_characters_to_include
       * if not specified, use html-to-text
       */
      getText: getBody,
      src:  'www-bin/**/*.html'
    },
    'cn-cursive.ttf': {
      getText: getHeadings,
      src:  'www-bin/**/*.html'
    }
  }
})

grunt.loadNpmTasks('grunt-fontmin')
```

### options (task-wide)
* dest:
  * destination directory, include trailing slash
  * default: `./`
* basedir:
  * source font directory, include trailing slash
  * default: `./`

### target options
* grunt's target name
  * relative to `basedir`, pattern of fonts to minimize
  * pass to `grunt.file.expand()`
* src:
  * pattern of files, relative to `Gruntfile`
  * src's content is passed to getText, it returns characters to included in minimized font
* getText:
  * filter function: (htmlContent) => string_of_chars_to_include
  * if not provided, use builtin `html-to-text`
  * you can write your own
* woff:
  * output compressed woff, anything other than `undefined`
  * default if no other output option is provided (like `css`)
* css:
  *  **NOT IMPLEMENTED!!**
  *  this is planned for future, css with inlined base64 font


## Caveat!
It's hard to include texts in css `content:attr('')`

Not formally tested, so it can be buggy

You can't change output filename

**You are responsible to get proper license of fonts you minify!**  
or consider [free fonts](http://zenozeng.github.io/Free-Chinese-Fonts/).



## License
MIT (C) wacky6
