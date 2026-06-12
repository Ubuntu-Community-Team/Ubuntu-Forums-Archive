---
title: "Yet another resolution problem, drivers for my card?"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by N Clement on 2007-04-14
Well, this complaint seems to be pretty standard by now, but I just can't stand this screen resolution.

I would be happy with a link or two to a tutorial or something, but I'm also wondering if my card might be the real issue.

So in case anyone recognizes my card, here is what the Ubuntu Device manager calls it:

Mobile 945GM/GMS/940GML Express Integrated Graphics Controller

and it has this listed twice.

Thanks for any help.

---

### Post by Stan Dixon on 2007-04-14
Hi,

I've got the same hardware. I solved my problem by searching for Intel 945 graphics. Read through the threads and you'll find various solutions. 

Have fun

---

### Post by N Clement on 2007-04-14
Ok, for anyone listening out there with the same card as me, I got this to work VERY easily with some instructions from this thread:

[http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+945+resolution]("http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+945+resolution")

I followed the more simplified version:

   sudo apt-get install 915resolution

that patched the stuff, so then all I did was restart 'X' with:

   <ctl><alt><bksp>

---

### Post by Matchless on 2007-04-14
> **N Clement said:**
> Ok, for anyone listening out there with the same card as me, I got this to work VERY easily with some instructions from this thread:

[http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+945+resolution](http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+945+resolution)

I followed the more simplified version:

   sudo apt-get install 915resolution

that patched the stuff, so then all I did was restart 'X' with:

   <ctl><alt><bksp>

Yes it seems as if the correct driver is already available in Kubuntu Edgy (i810) and only the 915resolution is needed to be installed, then a nice 1280 x 800 screen is available!  Mine was on a Quanta TW3m barebones

---

