---
title: "USB External HDD and DVD Burner Support"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by wapowell on 2005-02-18
Hello world,

I am running warty on a Dell laptop and have been thinking of buying an external HDD (USB) and an external DVD burner (USB). 

I'm wondering if anyone can share any difficulties they have had in ubuntu recognizing and using these devices.

I am quite new to linux, so I am also wondering if they should be recognized on bootup since they are USB or are there specific driver concerns that I should iron out before purchase.

Thanks!

-Bill

---

### Post by sunscape on 2005-02-18
I know they will both work under warty.

My external usb drive works perfectly. It is auto mounted (seach for auto mount at ubuntulinux.com for wiki) during boot. And my external cdrw drive also works nicely and is recognized at boot.

Curiously, my upgrade to hoary made some things a little "funny". My usb drive will mount, but it, for some reason, opens a nautilis window at random after boot. Go figure... at least it works  \\:D/

---

### Post by wapowell on 2005-02-18
Thanks for the reply Sunscape!  I appreciate it.  I am not planning on upgrading to hoary on this machine until it moves into stable, so as long as these work in warty I think I'll be fine.   :-D 

Thanks again!

-Bill

---

### Post by Tiede on 2005-02-19
Hellol, wapowell
I am also running a fresh Warty install.
I have a New USB Flash Drive (3 days old - so it ought to be fine) that I tried on Ubuntu when  I bought it.  For a strange reson, if I slide the write protect tab 'on', Ubuntu does not miunt it. It is in dmesg, it is in fdisk -l, but it won't mount. If I try booting the computer with it on, it  displays about a page of I/O errors...
Interestingly thought, if the tabn is slided to off, it workd just find and automagically appears on the desktop. So I have to leave it on RW mode, then RO it manually after mount.

Just thought you 'd like to know in case you run in the same problem.

---

### Post by jerome bettis on 2005-02-19
this is a pretty good guide on howto setup a usb hard disk: [http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561](http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561)

once i did that, i just plug the drive in and it pops right up.  but if you right click on it and select unmount volume, sometimes it says device is busy (even though it's not busy).  typing the command sudo umount -l /dev/whateverdevice will unmount it.  make sure you unmount it before you disconnect it.

---

### Post by gangalee on 2005-02-21
Good to see people have this working.
Maybe you can help me with [my problem](http://www.ubuntuforums.org/showthread.php?t=15663)  at [http://www.ubuntuforums.org/showthread.php?t=15663](http://www.ubuntuforums.org/showthread.php?t=15663)

troubleshooting output is included

---

