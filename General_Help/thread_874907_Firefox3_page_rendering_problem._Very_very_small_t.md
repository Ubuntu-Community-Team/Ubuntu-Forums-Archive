---
title: "Firefox3 page rendering problem. Very very small text."
date: 2008-07-30
forum: General Help
---

### Post by darkal on 2008-07-30
Firefox 3 does not render properly css anymore (look at attached screenshot). Almost all web page text looks like 1px thin lines.
I temporarily turned off "allow pages to choose their own fonts, instead of my selections above" option in preferences to be able to see text on web pages.
I also tried changing layout.css.dpi -1 to 0 in firefox config, but it did not do the trick.

I guess it happened after yesterdays update of the system. According to apt history, these are the firefox packs that got updated:

firefox (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 3.0.1+build1+nobinonly-0ubuntu0.8.04.3
firefox-3.0 (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 3.0.1+build1+nobinonly-0ubuntu0.8.04.3
firefox-3.0-gnome-support (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 3.0.1+build1+nobinonly-0ubuntu0.8.04.3
firefox-gnome-support (3.0.1+build1+nobinonly-0ubuntu0.8.04.2) to 3.0.1+build1+nobinonly-0ubuntu0.8.04.3

I use ubuntu hardy, compiz and default kernel.

Anyone got an idea how to fix this rendering problem?

---

### Post by silkstone on 2008-07-30
Very strange. Have you tried setting the minimum font size to 12 in Preferences > Content > Fonts & Colors > Advanced?

---

### Post by darkal on 2008-07-30
I am afraid it has nothing to do with font size options in firefox. I tried 16 and larger.
I can press Ctrl+ as many times as I wish and the texts still looks like that 1px line. As long as I keep "ON" that Preferences > Content option "allow pages to choose their own fonts, instead of my selection above" the text is unreadable.

---

### Post by silkstone on 2008-07-30
Character encoding set to 'Western (ISO-8859-1)' ?

Sorry - clutching at straws here. Does it make any difference is you turn off Desktop Effects?

I have the same updates and don't get the problem, although compiz is off.

---

### Post by vpsville on 2008-07-30
FF3 also has text sizing issues in Windows so its not just a Linux issue.  They changed the text sizing engine to be more like Opera but I don't think that was a good idea.

---

