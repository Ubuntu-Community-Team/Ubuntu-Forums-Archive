---
title: "Ubuntu duplicates my external harddrive?"
date: 2010-09-23
forum: Hardware
---

### Post by indirestraits on 2010-09-23
Hiya! I just registered here and installed lucid like a week ago.

I have an issue though.

I installed ubuntu through wubi to be able to dual boot.
I have 2 HD's 1 internal and 1 external.
The external one is full with a 800 gigabytes of stuff.
The internal has over 800 gigabyte of space left.

My problem is that everytime I plug in my external HD it pops up as a hardrive in "Computer" but everything it contains also pops up in "File System/Media".

Which means that all the free space on my internal HD is used up by my external HD by duplicating itself onto the system. How? Why? and is there a solution? :confused:

I would really much like to know cuz it's kinda getting on my nerves...

Please help me out!

---

### Post by bcbc on 2010-09-23
> **indirestraits said:**
> Hiya! I just registered here and installed lucid like a week ago.

I have an issue though.

I installed ubuntu through wubi to be able to dual boot.
I have 2 HD's 1 internal and 1 external.
The external one is full with a 800 gigabytes of stuff.
The internal has over 800 gigabyte of space left.

My problem is that everytime I plug in my external HD it pops up as a hardrive in "Computer" but everything it contains also pops up in "File System/Media".

Which means that all the free space on my internal HD is used up by my external HD by duplicating itself onto the system. How? Why? and is there a solution? :confused:

I would really much like to know cuz it's kinda getting on my nerves...

Please help me out!
It's not using space. External hard drives are mounted automatically under /media and they show up under Computer as well.

If you go to a terminal (CTRL-ALT-t) and enter "df -h" it will show you the space used. When the external is mounted it will show as /dev/sdb# mounted on /media/xxx.
It won't change what is available on /dev/loop0 (your wubi virtual disk) or /dev/sda# mounted on /host (your partition that wubi is installed on).


PS it's confusing to some wubi users but the space available is based on the size you chose when you installed wubi. That is the size of the virtual disk and it is doesn't matter whether there is space available on the host partition - the virtual disk is fixed.

---

