---
title: "installing new video card"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by uc50_ic4more on 2005-09-16
Hello -

I have been an Ubuntu/ Kubuntu user for a few months now, and am about to perform my first addition of hardware: I will adding an old Matrox G450 card. At present, I am using the on board video (I do not recall the chipset exactly - It is an AMD64 system...) My question is this: Will the new card be "auto detected" and will the xorg config file be "auto updated" to reflect the new display adapter, or should I *first* manually edit the xorg config file?

I am just a little gun shy about specifying the AGP slot as the primary video display device in my BIOS for fear of some trouble with xorg.

Thank you!

---

### Post by uc50_ic4more on 2005-09-17
In case anyone stumbles across this thread in the future, here is where I found a solution:

[http://www.linuxjournal.com/article/4817](http://www.linuxjournal.com/article/4817)

So, for reference, I *did* alter the xorg.conf file, then shut the system down, installed the G450, re-booted and all was well!

---

