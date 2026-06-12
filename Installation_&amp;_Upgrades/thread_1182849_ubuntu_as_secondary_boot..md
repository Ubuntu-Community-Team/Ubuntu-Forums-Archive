---
title: "ubuntu as secondary boot."
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by rakashu on 2009-06-09
Hi guys, just got my Ubuntu boot disk ready, and I have a question as to how to go about setting up a installation method having Ubuntu as the operating system on my partitioned hard drive.  I currently have Windows Vista (64 bit) as the operating system on the first partition, and when I had originally gone to install Ubuntu I didn't see an option to put it on the second.  To be honest I've never installed an operating system on a computer before, and have only done a restore once.  The laptop I have came with the hard drive pre-partitioned, I'm not sure if that's helpful or not.  thanks in advance!

---

### Post by raymondh on 2009-06-09
Hope this helps you

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Also, check the liveCD and see how it reacts to your system specs.  Wifi, sound, keyboard, F keys, etc.

you said your laptop came with a second partion pre-installed.  Are you sure you were not referring to both/either the recovery partition and the install partition (known as C:drive)?  Just checking.

Good luck.

---

### Post by raymondh on 2009-06-09
More links to reference and ponder on:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by rakashu on 2009-06-09
> **raymondhenson said:**
> Hope this helps you

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Also, check the liveCD and see how it reacts to your system specs.  Wifi, sound, keyboard, F keys, etc.

you said your laptop came with a second partion pre-installed.  Are you sure you were not referring to both/either the recovery partition and the install partition (known as C:drive)?  Just checking.

Good luck.

  thanks for the help guys!  Going to look this over later tonight when I have some free time.  to answer your question.  I have a C drive which has vista on it, and than I have a D (data) drive.

---

### Post by kumarnat on 2009-06-09
Hi,  I am also a recent convert to linux and I have installed ubuntu desktop 9.04.  After a lot of search and forum hunting I got to know of wubi which is a installer for ubuntu linux, 

All you need to do is have the wubi software and it will give you a choice of ubuntu version that you want to install, alternately, if you already have the iso file you can have both wubi and the iso file in the same folder and run wubi.

What wubi does is automatically sizes the windows partition and installs ubuntu as a dual boot os.

See their website for more details [http://wubi-installer.org/](http://wubi-installer.org/)

Hope this helps.

:o

---

### Post by raymondh on 2009-06-09
> **rakashu said:**
>  I have a C drive which has vista on it, and than I have a D (data) drive.


Hello rakashu,

And you do have another separate partition where you plan to install Ubuntu ... is that correct? I hope I don't sound silly.  Just make sure you are not deleting any partition that relies on your windows install.

Your D drive .... is it formatted in NTSF?  Ubuntu can read and write into NTSF.

Some more tips to ponder on.

You/we have a 4 partition limit per HD ... whether the partition be primary or Extended.  That means ... and this may be correct or not ... you already have 3 partitions (i.e recovery, c drive and d drive).  If you decide you need more partitions to support your ubuntu install (i.e. separating the /home from the / (root) files), consider making the last available partition EXTENDED in format.  The advantage of that is an extended partition allows us to have "mini" partitions INSIDE it called LOGICAL. And the limit of logical partition within an extended partition is determined by the OS' capability to number them (in simple terms):)  Yes, this will require a manual istallation.  Otherwise, you may just choose an automated/guided installation and the installer set's it up for you.

Let the forum know how goes.

---

