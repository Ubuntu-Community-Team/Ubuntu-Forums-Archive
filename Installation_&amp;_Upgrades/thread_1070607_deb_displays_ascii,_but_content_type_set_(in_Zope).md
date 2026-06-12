---
title: "deb displays ascii, but content type set (in Zope)"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by relay23 on 2009-02-15
Hi, I hope this is the right place for this question. Please advise if it is not.

I have built a deb package that simply upacks directories and scripts and does a little bit in a postinst script; VERY simple. 

The package builds just fine and I can run it without a problem by doubleclicking in the desktop environment. When i upload the file through the Zope management interface it prompts with a dialog for what to do with the file (including open with GDebi). When I access the file through LocalFS it just displays ascii text. I thought it was that localfs sets the content-type to "application/x-deb" while LocalFS sets it as "application/x-debian-package". Here's the kicker though, when i mv a random deb package to the directory i'm exposing using LocalFS it has the same content type and it prompts to do something with it, while the package i created myself just displays the raw content of the deb package. I compare the 2 headers of the deb files and they are apparently syntactically identical. I figured it was a problem with LocalFS but since that other one works no problem i think it has to do with my dpkg build.

Can someone more knowledgeable than me about content types and deb files try to help? this is driving me nuts!

thanks in advance,
Chris

---

### Post by relay23 on 2009-02-15
By the way, I tried to build it with the --old and --new formats. I see the headers are different, was hoping it would make a difference. No avail :(

---

### Post by relay23 on 2009-02-16
I think it might have something to do with the fact that there are no source files, no Makefile?? I know I can install this package manually with dpkg -i or with GDebi directly but do i have to build a source installation package in order to have it prompt in a browser? I'm trying to make this question as specific as possible so as to illicit some response. thanks

---

