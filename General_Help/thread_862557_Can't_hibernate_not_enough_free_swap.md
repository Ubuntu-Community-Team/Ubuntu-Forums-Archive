---
title: "Can't hibernate: not enough free swap"
date: 2008-07-17
forum: General Help
---

### Post by Duranxl on 2008-07-17
Hi all
Well i couldn't hibernate because of nvidia module, but after turning blacklist off it seems to go on.
But now it says i dont have enough free space for swap...but i do, i have 3GB free space on my filesystem and i only have 2GBs of RAM

So what's up?
thanks

---

### Post by Elfy on 2008-07-17
How big is your swap partition - it has to be bigger than RAM I believe, or at least the same size.

```
free -m
``` in a terminal will give you a quick check


Edit - changed free-m to code as it appears that it was invisible :D

---

### Post by drs305 on 2008-07-17
You can also run the following command to check how much swap space is available as well as memory usage:
```
free
```

If you have questions about what it means you can post the results.

---

### Post by bodhi.zazen on 2008-07-17
You need your swap to be = or slightly larger then ram.

What is the output of :

```
free
```

---

### Post by Duranxl on 2008-07-17
total       used       free     shared    buffers     cached
Mem:          2013       1996         16          0        510        750
-/+ buffers/cache:        735       1277
Swap:          953          0        953


Seems its 950MB! why? it should be able to use 3GB
So next: how do i make it bigger:p

---

### Post by bodhi.zazen on 2008-07-17
Boot the ubuntu live CD, use gparted to resize

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by Elfy on 2008-07-17
You are going to have to resize existong partitions. No idea why it's that size - if you used the guided option to install with have you added ram?

Anyway you can use the partition editor in your livecd to resize partitions, possible that UUID's change so that will need to be looked at. When you boot the livecd it will use the existing swap so you will need to turn it off before you can do any resizing

```
sudo swapoff -a
``` in a terminal will do that for you.

---

### Post by Duranxl on 2008-07-17
Thing is, I installed using WUBI, because i didn't want to change any partitions.

But I've created a 8GB file disk, of which 5GB is in use..so it should be able to do it?

---

### Post by drs305 on 2008-07-17
To elaborate a bit on _post-partitioning_ actions:

Your swap partition's UUID will change. If it is identified by UUID in fstab, you will need to change it to the new value. To see what your swap partition's UUID is after resizing it:
```
sudo blkid -c /dev/null
```

You might as well check your other UUIDs in fstab while you are at it:
```

sudo cp /etc/fstab /etc/fstab-backup
gksu gedit /etc/fstab
```

And don't forget to:
```
sudo swapon -a
```

---

### Post by bodhi.zazen on 2008-07-17
> **Duranxl said:**
> Thing is, I installed using WUBI, because i didn't want to change any partitions.

But I've created a 8GB file disk, of which 5GB is in use..so it should be able to do it?

Not easily ...

You could try making a swap file rather then a partition :

[http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3)

        [http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

---

### Post by Elfy on 2008-07-18
I didn't think that you could hibernate with a swap file  - or is that old information I read.

---

### Post by Duranxl on 2008-07-18
Guess wubi + hibernate = bad:(

---

### Post by bodhi.zazen on 2008-07-18
> **Duranxl said:**
> Guess wubi + hibernate = bad:(

It is true hibernation can sometimes be problematic on any OS, hibernation so working on my laptop.

I do not know how you can draw this conclusion when your system is misconfigured. Keep in mind wubi is a non-standard installation method.

Did you try a swap file ?

---

### Post by Elfy on 2008-07-18
> I didn't think that you could hibernate with a swap file - or is that old information I read.?

---

### Post by avtolle on 2008-07-18
As I recall from the Wubi Guide, hibernation was not supported for Ubuntu 8.04. I think it has something to do with the "virtual disk" that Wubi installs Ubuntu on under Windows.

---

### Post by bodhi.zazen on 2008-07-18
I think it will, it may need to be configured. I have not done it mind you, none the less :

[http://www.freesoftwaremagazine.com/articles/hibernate_linux?page=0%2C3](http://www.freesoftwaremagazine.com/articles/hibernate_linux?page=0%2C3)

---

### Post by avtolle on 2008-07-18
[http://ubuntuforums.org/showthread.php?t=848667](http://ubuntuforums.org/showthread.php?t=848667) It appears that hibernation may now be supported under the latest Wubi installer.

---

### Post by Elfy on 2008-07-18
I will this weekend try and install windows just so I can install wubi, I keep seeing all these errors/problems and can't help other than pointing in the general direction of the wubi guide/forum - I need to break it for myself :)

I had a quick look at [http://www.freesoftwaremagazine.com/articles/hibernate_linux?page=0%2C3](http://www.freesoftwaremagazine.com/articles/hibernate_linux?page=0%2C3) and it is certainly not as easy as having a swap partiton ;)

Is the general rule though that you can't hibernate with a swap file - unless you want to make life harder for yourself :) - just what I'd read hereabouts somewhere - I think it was a wiki page. That said of course I've also read that 50Mb is more than enough for /boot - and I've helped on more than enough of those :lol:

Just trying to make it straight in my head for others as I don't do it myself you understand - I hope :)

---

### Post by Elfy on 2008-07-18
@avtolle - you posted while I was checking my spolling -

The only reference I can see on that page to hibernation is a fix for

> * LP224697: Disable hibernation if swap is on file which I assume to mean it didn't work previously - so if people haven't got updated then it wouldn't, that of course also assumes that it actually works in the 'field'

---

### Post by rwabel on 2008-07-23
it's really a pity we cannot hibernate to a swapfile. In order to resize my swap parition, I need to move around free space from other partition. I spent hours by trying to hibernate to my swapfile...luckily I came across here now.

---

### Post by Neo4 on 2008-11-26
I'm having the same problem on my asus eee 1000h! I have 512MB for swap and 1GB of ram but I was only using 300Mb why can't I hibernate?! the ram used is less than the swap!

---

### Post by Elfy on 2008-11-27
But swap is less than RAm - try resizing the swap so it's at least the same as RAM

---

