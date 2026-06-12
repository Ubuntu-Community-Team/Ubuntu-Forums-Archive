---
title: "Wireless card disabled"
date: 2009-01-23
forum: Hardware
---

### Post by Digitbig on 2009-01-23
I just installed Ubuntu 8.10 through Wubi and I just can't seem to get my wireless card working. I used ndiswrapper to install the drivers, but I can't figure out how to turn on the card. There's no external power switch, and enabling the card in Windows has no obvious effect on Ubuntu. Is there something I'm doing wrong?

---

### Post by jayekaiser on 2009-01-23
If I remember correctly I had the same problem, and I fixed it by disabling the Atheros wireless drivers that are enabled by default in Ubuntu, and then installing the "madwifi" drivers that I found online.  Let me see if I can find that for you.

EDIT: Here's a post I found with some information about it, it says that the ath5 and ath9 drivers should be able to replace madwifi, but I think I still had trouble.  There should be an installation script at the bottom of the post if you want to give it a try.

[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

---

### Post by Digitbig on 2009-01-23
Are you sure this is what I need to do? I don't have an Atheros card. I have a Broadcom card, and I couldn't find Broadcom in the compatibility list.

---

### Post by jayekaiser on 2009-01-23
You may want to hold off on trying that, then.  From what I can see it looks like the madwifi drivers are mostly for Atheros devices.

---

