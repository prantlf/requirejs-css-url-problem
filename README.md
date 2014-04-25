requirejs-css-url-problem
=========================

Shows a problem of URL resolution if the module ID has a configurable prefix.
How to build the project and check the results:

    cd build
	node r.js -o build-debug.js
	cat out/styles/normal.css
    # prints: background-image: url("../images/czech.gif");
	cat out/styles/prefixed.css
    # prints: background-image: url("../images/czech.gif");
	cat out/sample.css
    # prints: background-image: url("images/czech.gif");
    # prints: background-image: url("../../images/czech.gif");

If the `build/css-builder.js` is replaced by `build/css-builder-fixed.js` the
image URLs are computed correctly; the two URLs in sample.css are the same.

This workaround is available at [the fix-url-rebase branch](https://github.com/prantlf/require-css/tree/fix-url-rebase)
for the time being, in case someone else encounters the same problem.
