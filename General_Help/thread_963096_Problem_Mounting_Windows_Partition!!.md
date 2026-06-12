---
title: "Problem Mounting Windows Partition!!"
date: 2008-10-29
forum: General Help
---

### Post by vincentjames501 on 2008-10-29
Hello, I'm trying to help out a friend of mine with his new ubuntu.  We have downloaded NTFS configuation tool but it doesn't even list his windows partition.  It only list his RECOVERY partition.  I've gone to sudo fdisk -l and it doesn't even list his partition.  What could be the problem?  It is a dell inspiron 1525.  

Thank You All

---

### Post by vincentjames501 on 2008-10-30
can anybody help me out?

---

### Post by owen_cook on 2008-10-30
are you able to use a live cd and then run gparted to see what it says?

I am surprised fdisk -l didn't show anything, was the command

# sudo fdisk -l 

as fdisk doesn't work on my machine without sudo

Owen

---

### Post by vincentjames501 on 2008-10-30
I will try my cd.  I just downloaded the ISO from the net and burned it.  Is that the same as the live cd?  Also i did use sudo fdisk -l as i said previously.

thanks,
vince

---

### Post by caljohnsmith on 2008-10-30
Can you post the output of the "sudo fdisk -l" command? It would help to see the configuration of the HDD partitions.

---

### Post by pmooney78 on 2008-10-31
Yes, burning the .iso file to a CD produces the LiveCD. Same thing.

Try installing GParted (use "sudo apt-get install gparted"), open it, and see whether your friend's disk appears.

Also, make sure you're checking the obvious stuff: Try plugging it into a different USB port, check to see whether the disk works in Windows, try booting Windows and running checkdisk on it.

---

