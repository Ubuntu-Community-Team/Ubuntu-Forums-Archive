---
title: "Stuck in 9.04 Install - Formatting Swap Space"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by skicrazer on 2009-05-21
Hi,

I am trying to install Ubuntu on an old Win 2000 machine. I'm fine with a clean install and wiping 2000 off of the machine, but I have had trouble with the boot disk having file errors when I run the check disk utility (from the list of 5 menu items presented before the install) - 2 the first time I ran the check, and 10 the second time (on the same disk!). 

I have also tried Wubi, and it eventually ends up hanging on the install.  The most recent attempts, I got through the Wubi part on Windows, then restarted as they suggested, chose Windows as I wasn't sure which to choose at this point in the install, but nothing happened, so restarted again to Ubuntu.  Installation began and now I'm stuck at for the last 3-3.5 hours 

Checking the installation (window title)
Installing System
Formatting swap space in partition #1 of /host/unbuntu/disk...
0% complete


I have a 13.5 GB HD, and allocated 7 GB out of 7.85 free to Ubuntu. Should this be enough? I was successful loading 8.10 through Wubi a few days ago, but when it tried to update to 9.04, it hung and was unresponsive and I had to do a hard boot.  Uninstalled wubi and ubuntu, then downloaded wubi again and it grabbed 9.04. But, again, it hung on the install, at 50% something or another (sorry, can't remember the exact point - had the wallpaper, etc, but no icons - just the install box), and another time it hung when creating the virtual disk while still on the windows screen (I think that was with the 129 release - most recent attempt is with 134).  Should I just go with 8.10 and reject the 9.04 updates?

I've also noticed that this PC is a bit below the recommended CPU - it's a P3 700MHz and 1GHz is recommended.  I've also got 384MB RAM, so that is above the minimum 256 and the 7 allocated is over the 5GB HD space.  ??  Do you think I should go with Xbuntu due to the CPU issue?

I'm also wondering if I should try LinuxMint or Fedora.  Any thoughts on those options?  (I burned a Fedora boot disk with F10-i686-Live, but the PC wouldn't boot from it.  Would that be the correct Fedora iso file... or do you not deal with Fedora at all?)  

What's a Linux newbie to do? 

Thanks!!

---

### Post by skicrazer on 2009-05-21
OK, I tried Demo Mode and it came up (not a very nice screen resolution, though :p).  Normal, Safe graphic, and Verbose modes  result in the same sticking point:

"Checking the installation" window title
Installing the system
0% (progress)
Formatting swap space in partition #1 of /host/ubuntu/disk...

and it just sits there.

Any advice? 

Thanks!

---

### Post by altocumulus on 2009-06-04
mmmm

I have 'same' problem - **stuck formatting swap space**. :(

Went straight into creating partition without asking me how much to allocate and then suggested I hadn't allocated sufficient - but would not then allow me to make any adjustment ....

fed up - though I bet it's Toshiba junk on the laptop that is causing me angst ...... :(

---

### Post by bol0 on 2009-06-04
Try to run some HDD diagnostic tools as it looks like a hardware issue. You can try to get some bootable diagnostic software like SeaTools or Lifeguard likes.

---

### Post by altocumulus on 2009-06-05
> **bol0 said:**
> Try to run some HDD diagnostic tools as it looks like a hardware issue. You can try to get some bootable diagnostic software like SeaTools or Lifeguard likes.


thanks for your suggestion :popcorn:

- I've tried SeaTools, both the windows and the DOS versions and nothing has emerged as a failure.

However, after using the DOS version I could not get my lappie to boot up on Ubuntu option, it kept giving an error of a missing .DLL file. Replacing the file made no difference....

---

### Post by jscc on 2009-06-05
i would try to install the xubuntu distro if ubuntu is not working for you, once it loads up and you get to the partition section you can either go the guided route or do it manually

---

### Post by skicrazer on 2009-06-10
Just a note - I started looking at Linux Mint and had problems with it not responding to the Install commands.  Through their forums, I figured out that I had no RAM left for the install when running from the demo mode.  I didn't take the logical step of seeing if I could skip the demo mode (should have, I guess), but I burned another iso disk with the XFCE community version and it installed fine.  As I understand it, Mint XFCE is based on Xbuntu (?), so maybe we should just try that version.  (I'm still trying to figure out how to get the screen resolution up from 800x600 to 1024x768, out of my KVM switch.  Apparently, the monitor specs aren't being passed to Mint, so it's defaulting to 800x600.  I need to figure out a way to up the default to 1024x768, which it *will *display when the monitor is directly connected to the box.)

Anyway, I wanted to bump up the Xbuntu suggestion as a viable option.:KS

---

