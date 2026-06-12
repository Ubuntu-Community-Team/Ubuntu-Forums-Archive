---
title: "Upgrade to 9.10 messes up fonts"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by strange_cathect on 2009-10-30
Hello,

Has anyone else had their fonts get completely messed up by the upgrade from 9.04 to 9.10? 

My firefox fonts are completely weird: incredibly small and they aren't rendering in the correct font. I can't seem to fix it by changing the fonts or settings in firefox.

In the attached images, you'll see the old font rendered compared to the new font rendering.

Any ideas? 

Thanks.

---

### Post by hellfeuer on 2009-10-31
I haven't upgraded yet, but have you tried the Fonts tab in Appearance?

---

### Post by coffeecat on 2009-10-31
> **hellfeuer said:**
>  have you tried the Fonts tab in Appearance?

Agreed - that second screenshot looks as though the 'Monochrome' option has been ticked under rendering in the fonts tab.

@strange_cathect, you need to restart Firefox after you change the font setting in Appearance

---

### Post by strange_cathect on 2009-10-31
I have. Thanks for the suggestion. But the point is that the settings are identical to what I had before, and the fonts are not being rendered properly. It looks like my TrueType fonts are messed up somehow. The pictures I attached should be rendering the Georgia font. But my Ubuntu machine isn't even close.

---

### Post by strange_cathect on 2009-10-31
Weird: If I go to, say, the NY Times, the font is so tiny that I can barely read it. I am letting websites choose their own fonts and font size through my settings in Firefox. Yet, I get this (see screenshot of today's NY Times)

---

### Post by strange_cathect on 2009-10-31
There is a bug report on this issue:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/67226](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/67226)

---

### Post by Nyas on 2009-10-31
I have made a fresh 9.10 install and have the very same problem with fonts in Firefox. They seem to be very small, almost unreadable in some pages (e.g. Google search results).

I tried to change all the settings in *Pref>Appearance* but nothing seemed to affect this. 

In Firefox *Edit>Preferences* found a temporary solution by unchecking the *Allow pages to choose their own fonts...* and setting the *Minimum font size* to 13. 

However, this changes fonts quite randomly in different pages. Google results bacame slightly bigger, although they still cause tension to the eyes. Ubuntu forum contents are just fine. However, YouTube video descriptions are too large, and I have also seen a couple of other sites where text becomes too big to fit into frames, menus and everything becomes chaotic.

I do not really know where so start looking in order to fix this. Is it really a bug? 

Is it really this one?
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/67226](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/67226)
I got the impression the above is about Firefox menu fonts, not the ones that are used to display the actual web pages. No idea if these two can be somehow connected:-k

---

### Post by Nyas on 2009-10-31
Btw, simple zoom (text only) function in Firefox can correct these issues. But it is rather tedious to adjust every page, so it would be nice to have a more permanent solution. Never had such problems even with old versions of fox on Windows...

---

### Post by bgreenaway on 2009-10-31
I have got the same problem and I cannot change my fonts at all in Firefox. Looks really bad Very frustrating. Glad I Cloneziila'd my workstation beforehand.

---

### Post by moxie3 on 2009-11-01
Same problem here, with a fresh install.
I also checked with Galeon and Konqueror, but all these browsers seem to have the same problem with the fonts. OpenOffice seems ok with Arial for example, but not the browsers.
Also, at least on my website, it seems that arial italic renders ok, but normal arial doesn't.

Very anoying, hope there will be a solution for this soon :(

Screenshot of arial normal and arial italic (sorry, my site is on dutch):

[IMG]http://www.spoenk.nl/public/fonts.jpg[/IMG]

---

