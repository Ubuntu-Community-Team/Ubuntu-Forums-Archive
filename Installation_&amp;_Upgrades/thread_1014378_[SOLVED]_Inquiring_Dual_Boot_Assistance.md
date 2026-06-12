---
title: "[SOLVED] Inquiring Dual Boot Assistance"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Rylin on 2008-12-17
Hey guys,

I currently have Vista installed on my main internal drive and I'd like to dual boot with Ubuntu. The catch is that I'd like to install it on another internal 250gb drive I'm about to install inside my rig.

My question is if its the same procedure as if I were doing a dual boot with only one drive and making a partition? How does it still create the dual boot screen if you have ubuntu installed on another internal drive and not from a partition thats apart of the Vista drive?

Many thanks guys :popcorn:

---

### Post by jenkinbr on 2008-12-17
Grub is installed on the master boot record of the first bootable hard drive, unless you explicity tell it otherwise. You don't have to worry about changing anything - Ubuntu will leave the vista partition alone.  I run my computer in a similar way, with winXP on hd0 and ubuntu on hd1.  Never, ever had a problem with it in terms of bootloader (other than the occasional GRUB ERROR 18, which is overcome by pressing the reset button).

---

### Post by Rylin on 2008-12-17
Well I successfully installed Vista and Ubuntu on seperate internal drives but the grub menu doesn't pop up when booting up the computer.. it loads up Vista automatically now.

I'm about to put gparted iso on a cd and boot from that. Any tips on what to do to make it bring up the grub menu every time I boot?

---

### Post by Yardarm on 2008-12-17
Here's a HOWTO on restoring grub after a windows install.  It's a quick fix involving a live CD and a few quick terminal commands.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Rylin on 2008-12-17
That did the trick. 

Thanks a bunch for the help guys. :popcorn:

---

