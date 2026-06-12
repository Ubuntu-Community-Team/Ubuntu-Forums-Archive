---
title: "missing charsets"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by swong1 on 2006-01-26
Hi,

Whenever I run xemacs or xfig, I get the warning message:

Warning: Missing charsets in String to FontSet conversion
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

I can still use xemacs and xfig, so I don't know what the warning is for. It is a nuisance though. 

I have searched the forums for similar posts, but none are helpful. Please help. Thanks!

---

### Post by swong1 on 2006-01-27
On a related note, scilab fonts changes from English to Hindi (or something similar) after upgrade. How do I change it back? I tried removing and reinstalling scilab, but nothing works.

Okay, found similar post here:

[http://www.ubuntuforums.org/showthread.php?t=87368&highlight=scilab+font](http://www.ubuntuforums.org/showthread.php?t=87368&highlight=scilab+font)

Removed the following fonts (using synaptic):
Gujarati
Indic
Kannada
Malayalam
Oriya
Punjabi
Tamil
Telugu

Now Scilab font is back to English.
The funny thing is, ubuntu-desktop is also automatically marked for removal. Synaptic says it is save to remove, but recommended that we keep it.

---

### Post by kaamos on 2006-01-27
ubuntu-desktop is only a metapackage (it install a lot of other packages). The only harm from removing it is that if you wish to dist-upgrade to a newer version of ubuntu later, doing that without ubuntu-desktop could cause some trouble.

---

### Post by swong1 on 2006-01-28
Thanks kaamos.

I found a temporary solution to the problem about the "missing charsets in strings to fontset conversion".

Issue ```
LANG=C
```
before running xemacs and xfig eliminates the warning messages.

---

