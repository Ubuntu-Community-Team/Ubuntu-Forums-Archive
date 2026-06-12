---
title: "How to comoletely remove .net 1.1 in wine in Karmic?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by darkod on 2009-11-12
Hello.
I was trying to see if one windows app will work in wine. It requires .net 1.1 so i tried to install that first. To make a very long story short, it can't work that way so I gave up.

But now .net 1.1 doesn't wanna go away. :(
1. I tried Uninstall Wine Software option, it starts to uninstall and then there is a message ".net 1.1 setup ended prematurely".
2. I have deleted the .wine folder.
3. I have removed wine.

Nothing helped. In Applications there is a structure wine/programs/administrative tools and .net 1.1 configuration option in there.
Even with wine removed and folder .wine deleted, it's still there.

How do I make it completely go away? I don't mind removing every trace of wine, I have nothing there anyway. Thanks in advance.

---

### Post by darkod on 2009-11-13
bump :(

---

### Post by darkod on 2009-11-13
Solved. In case someone else has a similar problem with any wine application:

[http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8](http://wiki.winehq.org/FAQ#head-82f00d009961866727f7e2d46e99d60f82e84cd8)

FAQ number 5, Uninstalling Applications. Do the manual commands and everything is gone. Of course, you need to enter sudo in front of every rm command, at least I did.

---

