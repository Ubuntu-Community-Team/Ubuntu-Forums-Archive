---
title: "fakeraid howto help"
date: 2009-06-30
forum: Hardware
---

### Post by santana on 2009-06-30
Hi I have followed the procedure in the ubuntu fakeraidhowto to get up and running. 4x raid 5. I am "certain" (TM) that I did all the steps correctly and have no typos etc...

Problem 1: 
The only way I can boot after following the fakeraid howto is using the live cd, selecting "boot from first hard disk". This loads the newly installed grub and I can boot up the new install. But how to fix so I don't need the cd rom?

Problem 2:
Windows no longer boots. Grub spits back: "Error 1: Filename must be either an absolute path name or block list." When I edit from the boot prompt I can use the tab completion and I see the following info on (hd0,0) where windows lives:  "Filesystem type unknown, partition type 0x7" How can I get grub to load windows? This is the bigger issue, having the live cd in the tray is only a minor inconvenience if I can boot xp.


I did boot up the windows repair console and I can still see the windows install so I think it's just a grub thing.

I have the bios set up to boot from the fake raid, and xp was correctly installed prior to my fakeraid howto adventure.

please help, I am over my head!!!

---

### Post by ronparent on 2009-06-30
Post the output of **fdisk -l** run from a terminal. Also post the /boot/grub/menu.lst. It looks like you put a lot of effort in this and might have done everything right. There may be a quick in your bios that is by-passing the set boot order.

---

