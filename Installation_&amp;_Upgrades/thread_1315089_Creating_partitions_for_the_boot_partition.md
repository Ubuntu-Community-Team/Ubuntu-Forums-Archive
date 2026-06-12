---
title: "Creating partitions for the boot partition"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by uk2 on 2009-11-05
Hello,

I will be installing Ubuntu 9.10.

However, when I go to the advanced options for making the partitions. I have decided that I will create a 

swap file x2 size of RAM 
/ (root) partition.

I have read some documents that say you should also create a boot partition (primary partition) for the first partition so that the BIOS can easily find it. And allocate only about 100MB.

I am just wondering do I need to create a boot partition? And what does it really do?

Many thanks,

---

### Post by kyuubi777 on 2009-11-05
didn't need to on mine 
just ext4 mount point /
and swap 1:1 ram

---

### Post by harrismh777 on 2009-11-05
> **uk2 said:**
> Hello,

I will be installing Ubuntu 9.10.. . .

I am just wondering do I need to create a boot partition? And what does it really do?

Many thanks,

You do not technically need a boot partition these days; modern machine, and latest grub.  It used to be that the /boot mount point had to be located on a separate partition within the first 1024 on disk.
That said, I always create several partitions, one of which is the boot partition. I do make it large enough that many (several) kernels can live there, but the partition size can usually be safely less than 100M;  on my 320 gig machine I set the first primary partition as 1024M for /boot.
I also set the swap area on a primary partition as twice the physical memory size... but this can also be a "swap file" these days.
I set  /  (root) on the third primary partition as something over 4gig... 
The remainder of partitions are set in extended (logicals).
I set /usr as about 8gig, 
/opt as about 6gig,... depending on what I'm using it for...
I set /home as about 4gig,
/var as 2048
/tmp as 1024
/usr/local   on one large partition on the remainder of the drive.

Some of this is done for security reasons... like mounting the /home partition as nosuid, etc.
Some of this has to do with easy upgrade and risking less opportunity for damaging /home etc.

But, if you're new to linux, or just in a hurry, or... lazy,... then you can mount the whole kit-n-kabootle on one hugmungous partition called    /

(By the by,  I always use reiserfs as my default filesystem too...)

And.... by the looks of things, ext4 isn't ready for prime time yet.


YMMV   MHO

kind regards,
):P

---

### Post by sliketymo on 2009-11-05
No problems with ext4 for 6mos or so for me.Works like a dream as far as I can tell.

---

### Post by uk2 on 2009-11-05
Hello,

Thanks for the info. Just a few follow up questions. 

As I am migrating from windows to Ubuntu, I not sure where the actual operating system gets installed to. In windows its the windows directory on drive C. And I install all my applications in C:\program files. I seperate all my data on drive D partition.

How does this differ in Linux?

I always thought that the primary partition is where the operating system can installed to, as this is where the operating will boot from. So I couldn't understand why you have your /root as primary partition?

Many thanks,

---

### Post by seenthelite on 2009-11-05
If you are removing Windows, from my experience just boot with the Ubuntu install disk and go with the flow. Always works for me.

---

### Post by audiomick on 2009-11-10
Hello uk2

My 2 bob's worth:

I use separate partitions at least for / and /home.

The operating system lives in /
all your stuff, and all your options & config files live in /home

If you put them on separate partitions, it means you can do a new install and leave the /home untouched. The computer comes back all happy and healthy and new, but all your stuff is still there and all the customizing that you fiddled with for months still works.

In the 4th post on this thread
[http://ubuntuforums.org/showthread.php?t=1307628&highlight=partition]("http://ubuntuforums.org/showthread.php?t=1307628&highlight=partition")
darkestfright explains how to clean up the home folder.

**[COLOR="Red"]CAUTION !!! If you execute this command in the wrong place, you WILL kill your computer !![/COLOR]**

The command 
```
sudo rm -rf .*
```
means " remove everything whose name starts with "."  "
All the files in the home folder that have your configurations and such like are hidden files and have a "." at the start of the name, so the command removes all the config and system stuff, but ignores your files.

Hope that helps.
Michael

---

