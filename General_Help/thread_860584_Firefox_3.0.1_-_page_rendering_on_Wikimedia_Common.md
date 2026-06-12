---
title: "Firefox 3.0.1 - page rendering on Wikimedia Commons"
date: 2008-07-15
forum: General Help
---

### Post by prs on 2008-07-15
All of a sudden Firefox has problems rendering some of the pages on Wikimedia Commons. I use the proposed repositories, so Firefox was updated to 3.0.1 the other day.

Some of the pages that are affected are the Welcome page, the Village pump and a template (but I guess other pages are too):
[http://commons.wikimedia.org/wiki/Template:GFDL](http://commons.wikimedia.org/wiki/Template:GFDL)
[http://commons.wikimedia.org/wiki/Commons:Welcome](http://commons.wikimedia.org/wiki/Commons:Welcome)
[http://commons.wikimedia.org/wiki/Commons:Vilage_pump](http://commons.wikimedia.org/wiki/Commons:Vilage_pump)

If I switch the character encoding from UTF-8 to ISO-8859-1 the pages are rendered, although with some weird characters as a result. If not the pages sometimes appear sporadically, and sort of overlayed over the previous page rendered, as I move the mouse around.

I have no idea what could be causing the problem - is it an error in the installed build, something with xulrunner (that had some problems yesterday) or something else altogether? The pages works fine in Epiphany and Opera as well as in a 3.0.1 install in Windows.

Anyone who can reproduce the problems?

---

### Post by prs on 2008-07-15
After a whole lot of digging around and testing, it seems that the problem is a known bug with rendering eastern asian characters (simplified chinese zh mostly I think). It's described in bug [#235985](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/235985).

I don't know if this problem was present pre-3.0.1 for me, since I just switched from a 19" CRT to a 22" TFT which made it possible for me to change font settings.

Right now the Firefox font settings are western with proportional set to sans-serif size 15 and 12 for monospace with no minimum limit. Does anyone else with similar settings find the same problems with some of the links above, any of Wikimedias images with templates containing chinese characters or any other web pages for that matter?

If I set a minimum font of 11, the problem goeas away (unless I zoom out), but still it's a bit annoying.

---

