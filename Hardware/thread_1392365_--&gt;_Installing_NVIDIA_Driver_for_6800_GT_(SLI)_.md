---
title: "--&gt; Installing NVIDIA Driver for 6800 GT (SLI) &lt;--"
date: 2010-01-28
forum: Hardware
---

### Post by RRF2525 on 2010-01-28
Last night I couldn't figure-out why my new installation kept dying on reboot...that has been figured-out and charged to the NVidia drivers included w/the PM.  I have tried the 96, 173 and 185 (Recommended) drivers for my 9.10 build but no soap.  I have tried d/l'ing the latest 190 build from NVidia and no soap (running the .run pkg don't see that anything happened save H/W Drivers reports no proprietary drivers installed while before it showed the three drivers mentioned previously).  

I'm new to Linux can you tell?  Enough with Windows...

I have read-up on man pages for command-line and gdm.  I switched users to root and stopped x then tried to follow instructions given...this is what happens:

1.  Select System > Preferences > Display
2.  Get msg: "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"
3.  I also get an "Unknown" box in upper-left corner of monitor (Sceptre X20 - want to run at 1680x1050 WSXGA+)
4.  Clicking "Yes" to the dialog provides the following message: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  So far that I can tell I've already done this.
5.  Clicking "OK" closes dialog and I'm back to a NVIDIA X Server Settings dialog that is gutted and of no use.

I must be missing something here and am way too new to Linux thus my question.  How to get the drivers properly installed for my XFX 6800 GT SLI GPU's?  I've already been beating-up the web on this one, the man pages and Ubuntu help docs.

System specs:  AMD X2 4200+, 2GB/250GB/1TB (no-RAID), dual-boot x64 XP on /dev/sda1 and 9.10 on /dev/sdb5 w/swap on /dev/sdb6.

What say ye?  : )

---

### Post by RRF2525 on 2010-02-12
Wow...lots of lookie-doos but no responses...hmm...

I've REALLY gotten hooked on Ubuntu and have spent the last two weeks living in it as much as possible.  In that time I've found the following answers to my own question.  In the event that another newbie runs into this same issue; I'm documenting what I learned...

1.  NVIDIA 6800GT dual-GPU's (SLI) w/SLI feats. off in BIOS (for now...)
2.  Restricted drivers are older than new features in 9.10 
3.  Restricted drivers create /etc/X11/xorg.conf 
4.  xorg.conf file is DEPRECIATED in Karmic in lieu of auto config by HAL
5.  Video driver is "suppose" to properly handle device..."but"...it doesn't in this case
6.  NVIDIA drivers (96, 173 & 185) all apparently incompatible by my "testing"
7.  Driver created xorg.conf is parsed during boot as per 9.10 design...but...
8.  Settings cause X server to crash and system comes to a halt
9.  To redeem your machine simply boot to recovery console and do the following
     a.  login as "root"
     b.  cd /etc/X11
     c.  ls xorg.conf  
     d.  is "xorg.conf" found?  If yes then...
     e.  rm xorg/conf
     f.   ctrl+alt+del and reboot the system

This time the machine should boot as before.

I still have yet to get proper performance from my GPU...I still haven't gotten the driver to work properly and haven't gotten the NVIDIA driver (190) to work at all (but that's still a WIP).

Hope this helps someone someday!  Ubuntu rocks!!  I've found a home in Gnome!!!  : )

---

### Post by lukaszr on 2010-02-12
Here's what I did to get my Nvidia 9800 GTX in SLI to work on Ubuntu 9.10 64bit. 

This should work for you as well...

1) Install Ubuntu (duh)

2) boot ubuntu for the first time and do ALL the updates! (DO NOT ACTIVATE THE RESTRICTED DRIVERS)

3) Reboot and Log-in into the Ubuntu

4) Select "Ubuntu Software Center" from Applications

5) Search "Nvidia" and install "NVidia binary X.Org Driver ('version 185' driver)

6) DO NOT REBOOT!! and open terminal and type "sudo nvidia-xconfig" followed by "sudo service gdm restart"

7) Login and open terminal and type "sudo nvidia-settings" and select GPU 0 and click the DFP-0 and click "Acquire EDID"

8) Reboot Ubuntu and it should work!!


*PM me if you still need any further help!!*

Enjoy Ubuntu!! :D

---

