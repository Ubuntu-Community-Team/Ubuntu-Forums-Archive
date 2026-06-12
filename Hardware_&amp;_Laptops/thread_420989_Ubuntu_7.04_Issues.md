---
title: "Ubuntu 7.04 Issues"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by Matt Jones on 2007-04-24
Ubuntu 6.10 worked PERFECTLY on my Comaq laptop.  I decided to upgrade to 7.04 via means of a FRESH INSTALL using the LIVE CD.

Everything works OK except from:

- I can't change the wallpaper. Well, I can, but as soon as I reboot it reverts back to the original. I've tried images saved on my Ubuntu partition and also those from Firefox (i.e. "Set as Wallpaper").

- Wireless - worked fine on Ubuntu 6.10. Worked fine the first time I booted into Ubuntu 7.04. Won't work anymore.  The card is Intel Pro/Wireless 3945ABG

- Since rebooting, I have now also lost my window controls (maximise, minimise, close). I am still using the default theme. Tried changing themes, window decorations etc but I still cannot get my controls back!

I then did another fresh install, this time using the Alternate CD.  Not tried changing wallpaper yet, but wireless doesn't work at all.

Any ideas?

---

### Post by BoneKracker on 2007-04-24
If you're using desktop effects, try turning it back off.

---

### Post by Matt Jones on 2007-04-24
Not used desktop effects at all on this laptop yet.

With the install of the alternate CD, I have controls at the moment but then again I did on my previous install! They just dissappeared on a reboot.

---

### Post by hyperair on 2007-04-24
If you boot into the LiveCD does it work? Also check if you have linux-restricted-modules package installed (apt-cache policy linux-restricted-modules-`uname -r`).

---

### Post by Matt Jones on 2007-04-24
It worked off the Live CD and worked when I first booted into my new system.   Since then it refused to work.

Restricted drivers are installed and working according to the system

---

### Post by hyperair on 2007-04-24
This is really weird. Could you post the output of "dmesg" without the quoatation marks in the terminal here?

---

### Post by Matt Jones on 2007-04-24
I can do in about 6 hours time when I get home.

---

### Post by BungaMan on 2007-04-24
> **Matt Jones said:**
> - Since rebooting, I have now also lost my window controls (maximise, minimise, close). I am still using the default theme. Tried changing themes, window decorations etc but I still cannot get my controls back!
Can you attach a screenshot of this?  That could give a better idea of what goes wrong.

---

