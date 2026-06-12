---
title: "How would I go about making a multi-boot DVD?"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by XtremeGamer99 on 2008-12-18
Hello,

I've been thinking about this for a while, and the more I think about it, the more I want to do it.

Instead of carrying around 3+ CD's/DVD's all the time (Ubuntu 8.10, Debian, Windows XP Pro, Knoppix, Ultimate Boot CD, Ultimate Boot Cd for Windows, etc), how can I compile all of those into a single image to burn onto a DVD-RW, and then have a menu to select which OS to boot from on the DVD?

---

### Post by XtremeGamer99 on 2008-12-19
Anyone?

---

### Post by mylo9000 on 2008-12-19
I know this post won't be much help, but its better than getting nothing. 

I've tried a similar approach with a series of USB flash drives and Unetbootin. What i wanted to do was have a series of different distros on a 4GB stick and have a menu to boot each one.

I got it to somewhat work with Ubuntu 8.10, PcLinuxOS 2007, Puppy 4.1, and DSL. 

Ubuntu and Puppy 4.1 booted ok but i couldn't get PcLunuxOS or DSL to boot. PcLinuxOS kept complaining about missing files, I can't remember what DSL did.

I did some digging and found that i needed to crack open the initrd.gz and change the paths in some of the files to point to the subfolder that PcLunuxOS was placed in. then i had to tinker with the syslinux.cfg file to add the menu entries for each boot.

It became a bigger project then i was looking for so i dropped the idea.

I know what your looking for is doable though. 
The reason i know this is because Linux Format magazine includes a DVD with every issue and sometimes they release a multi-distro live DVD. i've got a couple of them myself. they work great. so it can be done it just a bit more work than what i'm willing to do.

I might try again some day.

I hope i was able to give you a clue on a direction if you still wish to create the disk. i'm not sure how you will integrate the windows stuff. but i know a linux live DVD compilation is possible and has been done before. 

If you ever get it working, maybe you could post a how-to or something here and i'll do the same if i ever try again.:grin:

---

### Post by prshah on 2009-10-23
> **XtremeGamer99 said:**
> 
Instead of carrying around 3+ CD's/DVD's all the time (Ubuntu 8.10, Debian, Windows XP Pro, Knoppix, Ultimate Boot CD, Ultimate Boot Cd for Windows, etc), how can I compile all of those into a single image to burn onto a DVD-RW, and then have a menu to select which OS to boot from on the DVD?

You can also check out [http://ubuntuforums.org/showpost.php?p=8147658&postcount=12](http://ubuntuforums.org/showpost.php?p=8147658&postcount=12) (or my sig) for a multiboot live DVD which includes Ubuntu, Kubuntu, Xubuntu, MythBuntu, etc. It can also be used to boot various versions of Windows, etc.

---

