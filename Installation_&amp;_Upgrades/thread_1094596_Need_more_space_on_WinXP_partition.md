---
title: "Need more space on WinXP partition"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by pedromartins on 2009-03-12
Guys,

I'm having some trouble and some help is welcome.

I have 5Gb for win-ex-pee and 75Gb for Ubuntu and now I need to change to 10Gb/70Gb.
I read here I can use "SoftStart" to backup Ubuntu but I think I missed something.
I'm using 8.04 LTS and an used space of about 6Gb.
I have this in mind: Full Backup Ubuntu, delete all Ubuntu partitions, expand win-ex-pee partition, install again Ubuntu and restore my previous install.

That's why I ask here:
- How can I create an image of Ubuntu install/definition/etc. to be able to save it to an USB pendrive?
- How can I restore that image to new partition/install?

Thanks in advance.

Pedro

---

### Post by logos34 on 2009-03-12
You can use Gparted for that.  But you need to work from the Ubuntu live cd because / cannot be mounted during resize. (live cd desktop-->System>Admin>Partition Editor)

---

### Post by pedromartins on 2009-03-21
I've just killed Ubuntu...

I resized the partition (shrinked) and then moved it to right to be able to get some free space 'before' linux. After it I expanded ntfs partition.
All ok here... about 30min to finish it.

After restart, I entered Ubuntu and realized it was 'hibernated'...
I worked with it and when I tried to open some programs including console, they simply didn't open.
Filesystem showed me the size I had before resizing...

I shut down the pc and after power up, I choose Ubuntu. The progress bar filled up but when it was the time to appear the login screen... nothing 'sympathic' appear. only a erros message saying a problem occured.

Is there any way to fix this, or I must reinstall Ubuntu?

---

### Post by logos34 on 2009-03-21
ouch...

maybe boot the live cd and run a file system check from the terminal:

sudo fsck /dev/sda2

(replace sda2 with your ubuntu / partition)

---

### Post by pedromartins on 2009-03-22
Done that. Result: 'clean'

I saw some error with 'sda5 » journal', but the screen disappeared very fast and I couldn't read more...

I think I'll reinstall Ubuntu

---

