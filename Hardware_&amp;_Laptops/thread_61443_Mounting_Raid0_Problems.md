---
title: "Mounting Raid0 Problems"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by moffa on 2005-08-31
What I've done so far is outlined here:
[http://ubuntuforums.org/showthread.php?t=2557&highlight=silicon+image](http://ubuntuforums.org/showthread.php?t=2557&highlight=silicon+image) 

When I run "ls /dev/mapper" from root terminal I get:

control  sil_aebhddcddeej  sil_aebhddcddeej1

I have activated the raid using "dmraid -ay -v" and when I run "dmraid -r" I get:

/dev/hde: sil, "sil_aebhddcddeej", stripe, ok, 156298368 sectors, data@ 0
/dev/hdg: sil, "sil_aebhddcddeej", stripe, ok, 156298368 sectors, data@ 0

So I believe my raid has been detected properly.

The Problem is when I try to mount it using: " mount -t ntfs -o users,owner,ro,unmask=000 /dev/mapper/sil_aebhddcddeej /mnt/raid/"

I get:

mount: /dev/mapper/sil_aebhddcddeej already mounted or /mnt/raid/ busy

I dont know what else to do.  I am so close to getting this working.

Edit: When I try running "umount /dev/mapper/sil_aebhddcddeej"
I get: umount: /dev/mapper/sil_aebhddcddeej: not mounted
So it must be that /mnt/raid is busy; whatever that means

---

### Post by moffa on 2005-09-01
bump... burried on 3rd page.
Would really appreciate some help.

---

### Post by moffa on 2005-09-01
After countless hours looking for help and experimentation I have figured out what the problem was.

You have to mount sil_aebhddcddeej1 instead of sil_aebhddcddeej.

Thats it...

---

### Post by uGLy on 2005-09-05
i found the same problem 2  ](*,) 
can u help me 4 solving that problem

TB4

---

