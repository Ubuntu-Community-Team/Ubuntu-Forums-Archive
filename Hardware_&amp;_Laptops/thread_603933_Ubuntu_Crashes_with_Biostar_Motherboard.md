---
title: "Ubuntu Crashes with Biostar Motherboard"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by tux_yota on 2007-11-05
Hello folks, I've had this problem for a while and thought I'd post this in case anyone else has seen it.
I have a Biostar M9 motherboard (6100/410 chipset) with 1Gig of memory. I am using the built in video.

The problem is - Randomly, I will see a screen of several columns of short (white & black) horizontal lines.  It happens MUCH more frequently with Compiz or Beryl turned on, though even without it will still crash. It's hard to say what triggers it. Sometimes opening a streaming video, sometimes just clicking of a normal link. (even with Compiz disabled)

After it does this, the system stops dead. The only thing that works is a reboot.(via the reset or power button)

I've tried ALL the avail Nvidia drivers in the repository with the same result. This happens in Ubuntu, Kubuntu, Mandriva, Fedora, PCLinuxOS and most recently in Linspire.

I do have a pic of the screen on my local HD but I have no online pics....sorry. I've attached a JPG image.

Just wondering if this is a onboard video issue or a nforce motherboard issue. The board is new.

Would I be better off getting a new (Nvidia?) 7500 or 8400 graphics card, or just replacing the motherboard with one using a VIA chipset?

---

### Post by psusi on 2007-11-05
Sounds like overheating... or bad ram... try running memtest.

---

### Post by dabl on 2007-11-05
Sure sounds like hardware trouble in the video domain.  Maybe thermal-related, since it seems to show up when the video system is pushed with compiz or streaming stuff.  Probably not a fixable thing ....  :(

---

### Post by tux_yota on 2007-11-05
I will run MEMtest this evening.

The RAM is new also.

Would any of you try a new video card & disable the internal video?

---

### Post by dabl on 2007-11-06
Personally I'd try a different video card first -- if the problem goes away, you'll know that was the problem.  I think a main RAM problem is less likely, but also possible.  :)

---

### Post by tux_yota on 2007-12-08
PROBLEM FIXED!

Apparently, the problem was the nvidia built in video.

Added a Nvidia 7600 PCIe card and switched the BIOS over to default to that PCIe card, everything works flawlessly, in all distros. Even Compiz-Fusion works perfect. No crashes as all.....none, zip. Now I can witness how stable Linux can be.


Thanks to all.

---

### Post by Cubby on 2007-12-08
That's great news.  

I'm a firm believer in using a video/graphics card instead of the on-board graphics.  Even if it's a low end card and you don't run 3-D CAD programs or go at games, it is always easier to have hardware that is seperate if the choice is available.  Your CPU will be happier, too!

Regards.

---

### Post by Linuxratty on 2007-12-21
> **tux_yota said:**
> PROBLEM FIXED!

Apparently, the problem was the nvidia built in video.

Added a Nvidia 7600 PCIe card and switched the BIOS over to default to that PCIe card, everything works flawlessly, in all distros. Even Compiz-Fusion works perfect. No crashes as all.....none, zip. Now I can witness how stable Linux can be.


Thanks to all.

Iive also had overheating problems with my Biostar mb...The first one committed suicide.
 The second one is running hotter than I like,but it's not crashing...
 Have you noticed feeling heat,like when you open the disk drive?

---

