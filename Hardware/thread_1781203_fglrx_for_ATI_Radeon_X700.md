---
title: "fglrx for ATI Radeon X700"
date: 2011-06-13
forum: Hardware
---

### Post by Salim on 2011-06-13
Hi all,
I've installed Ubuntu 11.04 on an old laptop of mine, which has a ATI Radeon X700 graphics card. So far everything is fine, but Nexuiz is hardly playable with the standard graphics driver (radeon).
So I would like to install the proprietary fglrx driver. I did it a few years ago and it worked. However, now that graphic card is not supported by the newer fglrx drivers. So, I downloaded an older one, where my card is supported. However, the ati-installer has only listed Ubuntu up to version 9.04.
What can I do to make it work?

I would be grateful for any help.

---

### Post by DirtyPC on 2011-06-13
You might need to compile your xorg.conf! Give me 2 mins!

---

### Post by DirtyPC on 2011-06-13
I'm not sure, as I did this a while back. User: Grenage has a great how to here: [http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

---

### Post by cascade9 on 2011-06-13
You cant run the fglrx drivers with newer ubuntu versions and that card. You have to use the open source drivers.

---

### Post by Yellow Pasque on 2011-06-13
> **Salim said:**
> What can I do to make it work?
You can't, unless you use an old distro. [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)

What you can do is try xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
Make sure to turn off SwapBuffersWait in xorg.conf for max 3D fps.

---

