---
title: "[SOLVED] GDM locks on boot in kernel 2.6.24-21"
date: 2008-10-22
forum: General Help
---

### Post by wyth on 2008-10-22
I'm not quite sure when this started, because kernel 2.6.24-21-generic was working fine for me for some time.  Then a few updates later, and I could not get to the desktop upon login.  

Back to 2.6.24-20-generic, and everything was dandy.  A few more updates later, and I could get to the desktop, but the first time I click on anything, the desktop locks up.  I've checked after every handful of updates, and still no joy.

Not quite sure where to start with this one.  Ideas?

EDIT: Of course now I'm finding [some others are having the same problem]("http://ubuntuforums.org/showthread.php?t=948584"). Seems to be wifi related?

---

### Post by dagoth_pie on 2008-10-22
Restricted drivers can get stuffed up by kernel updates, since the kernel developers don't have access to the source of the proprietary drivers, they can't adjust either the kernel source, or the driver source to better cope, do you have an Nvidia or Ati graphics card? or does your wifi run restricted drivers?

---

### Post by wyth on 2008-10-23
No Nvidia or ATI, it's a pretty simple machine.  I do have the wireless driver from Intel, and that may be doing something, because since the 2.6.24-20 kernel it fails to start (or rather shuts down) when the login screen comes up.    

So I reinstalled all the 2.6.24-21 elements -- couldn't get to the desktop, just a big white box in the upper-left corner.  One bit of advice was to run ```
sudo dpkg --configure -a
```.  That at least started to get me to the desktop.  

Then I found that I had linux-headers-lum (and the attending linux-headers-lbm) files installed.  I don't have those installed for any other kernels -- I believe I tried those when I first couldn't get in.  I removed those, and am about to try again.

---

### Post by wyth on 2008-10-23
HEYO!

Removing linux-headers-lum and linux-headers-lbm for the 2.6.24-21-generic kernel did the trick; I'm writing this from the latest kernel.

---

### Post by wyth on 2008-10-23
Nope, I was mistaken -- I thought I was booting into 2.6.24-21-generic, but I'd commented that out in my menu.lst.  The problem still persists, however it works fine if I boot into recovery and start X as root -- no issues there.  I have a feeling this has to do with the wireless, since that's not started in recovery mode.  

I'm attempting the 2.6.24-22 kernel found in [Tim Gardner's PPA]("https://launchpad.net/%7Etimg-tpi/+archive") (he's an Ubuntu kernel developer).  I've also commented out iwl3945 and snd-hda-intel in /etc/modules; I had to use those in the past, but there have been some kernel updates since, I've also read of people having problems with 2.6.24-21 and sound causing kernel panic, and I'm just trying for anything.

---

### Post by wyth on 2008-10-23
No go on 2.6.24-22-generic -- same issues as with 2.6.24-21-generic.  One thing I'll be doing for sure is a clean install of Intrepid to see if this persists.

Any more ideas would be appreciated.

---

### Post by wyth on 2008-10-25
We can call this one solved.

One thing I learned: When I booted with an ethernet connection rather than to wifi, 2.6.24-21 started.

But I updated to a clean install of the 8.10 release candidate, and everything works just fine.

---

