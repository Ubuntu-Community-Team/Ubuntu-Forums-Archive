---
title: "Ubuntu 9.10 stuck in a loop"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by ben44b on 2009-10-28
I've "upgraded" to 9.10. It still hasn't booted up once. I get the splash screen, a flicker, and after a few seconds, the splash screen comes up again...and again... 

I saw a brief message about it trying to find the proper resolution. I use 1440*900. I have embedded Brookdale Intel chipset. 

Previously, my computer wouldn't load until it said "Unable to load Description Tables". That message does not appear now at boot-up.

Thank you.

:mad:

---

### Post by mick222 on 2009-10-28
have you tried changing the resolution at start up press e at grub and add 
vga=1280*1024 or whatever reolution you want to try then ctrl+x to boot

---

### Post by quickvfr on 2009-10-30
I am having the exact same problem with a machine running the 32bit version of 9.10 with an older, Intel820 video driver.  I tried the solution listed, but it did not work.  I seem to remember having to go through this a couple of versions back.  Any other ideas would be greatly appreciated.  I have another, AMD64 system that upgraded without issue.

---

### Post by quickvfr on 2009-11-01
To fix my machine, I uninstalled my video drivers from the command line and reverted to the 9.04 drivers.  It boots a little slow, but it works without losing any of my data.  I hope that helps!

---

### Post by tryingtoboot on 2009-11-01
I might be getting a similar problem, but it happens in the Live CD so I don't get a chance to install in the first place. I can get into the live cd desktop but I can't make it to the point where I begin install, it just goes back to the splash screen and won't leave it.

---

### Post by johnnycasher on 2010-04-21
i have this exact LOOP problem:

Acer 6930G / ati hd 4650

installed Karmic

Everything's fine

i installed the propriety drivers from ATI 

Suddenly i have this loop problem and i can't stuck out of this..

---

