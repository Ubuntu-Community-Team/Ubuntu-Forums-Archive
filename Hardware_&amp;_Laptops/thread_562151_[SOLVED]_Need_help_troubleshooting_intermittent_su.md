---
title: "[SOLVED] Need help troubleshooting intermittent suspend failure"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by peabody on 2007-09-28
I just install Feisty Fawn on this compaq presario C571NR last week and for the most part got everything to work.  However, one thing that's come up is that the suspend seems to randomly fail on me.  It'll usually work several times in a row, but then  I'll close the lid but the power light won't end up doing the assured blink that tells me the hard drive has spun down.  Upon opening up the laptop, to try and investigate, several things have a tendency not to work including (sometimes) the keyboard and any attempt to login through a VT or the network.

My guess is that it is either related to the broadcom wireless doing something weird, or the video card.  I have an intel i950 adapter on this thing which I am using the i810 xorg driver with the 915resolution package to get to work and the broadcom is a Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) which I got up and running via the instructions at  this wiki page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28c571nr%29)

All I'd like to discover is some sort of consistent work around (disable the broadcom, logout of X, etc, etc).  Any and all help appreciated.

---

### Post by por100pre1 on 2007-09-29
It is possible... Have you tried [this]("http://ubuntuforums.org/showthread.php?t=471855")?

---

### Post by peabody on 2007-09-29
I forgot about this post.  I think I may have solved the problem.  It appears to be related to desktop effects/compiz.  So far suspend has worked flawlessly as long as compiz is not enabled.  If it's enabled it works sometimes, but it does seem to fail half the time.  I'll have to take a look at your link.

---

