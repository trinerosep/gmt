# Features changes based on David's feedback

# Before changes based on David's feedback

## General:
Use SVG images for all your vector artwork wherever you can. SVGs are supported by all browsers (except ancient IE or ancient Android, which Bootstrap doesn't support anyway).  It'll avoid pixellation or scaling issues, especially on retina devices and avoid the need to ever resize an image by hand.  For your collaborator logos, converting EPS/AI/etc files to SVG is straightforward with Illustrator or Inkscape and for optimisation try the SVGO Node tool.
For accessibility, make sure acronyms like MYGMT are explained with an abbr tag and all your images have reasonably detailed alt text (eg "Generalist Medical Training at James Cook University logo" vs "logo")
Add a 'skip to content' link for screen readers at the top of the page and a 'back to top' link at the bottom (eg in the footer).  You can just snag the HTML from an example like https://web.jcu.io/examples/jcu-landing/content.html.  That means the first link screen readers or those browsing with a keyboard allows them to skip to the content and jump back to the beginning.
To make sure focussing works, reload your page and keep hitting Tab to shift your focus.  Make sure you can see the focus outline as this'll be what someone who's vision impaired or has limited mobility will do.
Try using tota11y on your page -- that's the glasses in the bottom left on my Web Framework examples.  You can either just apply tota11y to your page temporarily with the bookmarklet (see the link under Installation) or link in the JavaScript on a semi-permanent basis. It'll help with ordering headings, colour contrast etc; there's a few suggestions it's making about your page.  The screen reader wand is particularly cool.
## Top nav:
I'd suggest shifting the hamburger menu to the top fixed nav.  The page nav is likely to be lost/missed otherwise on mobile devices, especially once they scroll.
The icons on the orange fixed nav (on mobile) don't have a lot of meaning for me as a visitor.  I'm not necessarily the target audience but you might want to do a quick test with some users to make sure they understand what are are without text.
## Left nav:  I'm wondering whether a continuation of the orange colouring would work here to keep the vibrancy of the page.  See the attached screenshots for an example, though you may want to dull it down for accessibility.  It's nit-picking, but I kind of feel the left nav gets a little lost otherwise with the grey.
## Breadcrumbs: Bootstrap's got a Breadcrumb component that you can build off; it avoids the need to manually insert separators into the HTML, which is better for accessibility / developers editing later.  It also makes the divider customisable with just CSS.
## HTML:
Make sure your <head>'s <meta> tags come in the exact order shown in examples like https://web.jcu.io/examples/jcu-login/ (see the comment on line 12).  Internet Explorer is particularly picky about the tag from line 10 so you should shift your <title> element after the 3 suggested tags.
It's best to put your JavaScript <script> tags just before the closing </body> tag.  This means the browser loads the page first then executes the JS, rather than blocking rendering while loading JS.  It also means that you can add any per-page customisations at the end of the document and avoid the need for jQuery $(document).ready() calls, making your page even faster.
Use a <main> HTML5 element on the page for better semantics; you can just switch your <div class="container-fluid"> to <main class="container-fluid"> and it'll just 'mean' more to a screen reader etc.
Make sure you're using the jcu.min.css CSS file in production.
Your images are all good on this page as they don't need to be responsive, but in case you need them, use img-fluid 



