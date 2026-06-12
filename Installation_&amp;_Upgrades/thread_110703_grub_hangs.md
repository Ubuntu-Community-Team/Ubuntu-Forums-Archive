---
title: "grub hangs"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by green lizard on 2005-12-31
hello ubuntonians!

Hopefully you can help me out...  I'm completely new to linux and ubuntu (but seasoned in windows ;-) I decided to install ubuntu 5.10 some days ago. First part of the installation runs fine, but on reboot the system hangs with "grub" in the upper left corner of the screen. Here's what I did:

Background: Hardware is Pentium 2,8 GHz on Asus board. I've 3 harddrives installed:
(1) IDE - NTSF, contains xp and programms and lots of stuff
(2) SCSI - NTSF, contains my valuable files 
(3) SCSI - which I have wiped and partitioned for ubuntu. There's 5 GB for /root, 10GB for /home, 2 GB for Swap and about 20 GB in FAT32 to share files with XP. I used ext3 as filesystem for ubuntu.

When asked where to but GRUB, I first tried MBR. But this got messed up and I could not boot neither xp nor ubuntu. I restored the MBR for XP and followed the guide from Matthew Miller to install GRUB to /root of my ubuntu partition (see "http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/" for this guide)
Now the XP boot loader gives me the choice to boot xp or ubuntu. While xp works fine, ubuntu just hangs with the word "grub" in the upper left corner of the screen. What can I do? Already tried reinstall to make sure I really went "by the book" - same result.

Just in case, heres my menu.lst:
snip 8<-----------------------------------------------
# ... I've cut out all the comments here ...
default		0
timeout		10

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1
snap ---------------------------------------------->8

Did I take the time to wish you all a happy new year? Shame on me! But here it comes: Happy new Year to all of you!

---

### Post by green lizard on 2006-01-21
pleaze! I'm still having this problem and no idea how to tackle it.

---

### Post by lha on 2006-01-21
Your situation is essentially different from what is discussed in Miller's how-to. You are installing Ubuntu on a separate drive, so things are easier to set up. (I'm not sure if scsi causes troubles here.) Are you able to boot into Ubuntu if you change boot order from bios? Are you able to boot from scsi drives at all? Is your Ubuntu installation incomplete at the moment?

---

