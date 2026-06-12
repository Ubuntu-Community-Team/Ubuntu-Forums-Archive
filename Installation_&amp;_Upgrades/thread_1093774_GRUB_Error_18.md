---
title: "GRUB: Error 18"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by OxentroT on 2009-03-11
I had decided to take the plunge and install 'Ubuntu_intrepid8.10'
full scale unto my 'IBM T40, centrino'. All seemed to be running 
smooth until i chose option to restart now in order to use new 
installation. 

After reboot the screen reads as follows:


______________________________
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 18
_
______________________________



thankyou. 

OT

---

### Post by upchucky on 2009-03-11
search posts in here for grub error 18, there are hundreds of posts that show how to fix this.

---

### Post by OxentroT on 2009-03-12
Thank you for the advice. I have already searched the forums for the 'GRUB Error18' but it seems as if the solution varies from machine to machine. In my particular case I am unable to do anything on this 'GRUB' prompt. However I seem to notice that some people are able to run commands in this 'Error 18' state, not me, no buttons seem to work.:(

---

### Post by dstew on 2009-03-12
You have a stage1 error. This means that the grub stage1 boot loader is in the MBR of the boot disk, but when it runs it cannot "mount" (access) the targeted partition that has the grub stage2 file in it. Stage1 is a tiny program, so it doesn't give you a command line or other options. The folks who get a command line are probably dealing with a stage2 error.

Anyway, bottom line is you will need to re-install grub, and maybe Ubuntu, in such a way that the stage1 file can mount the partition that contains the stage2 file and Linux kernel. This particular error 18 may mean that your BIOS is one of the older sorts that cannot access partitions beyond the 1000 cylinder limit. The usual fix is to re-install Ubuntu, but to create an extra "boot" partition of about 50 Mb at the front of the disk that contains the boot files (the grub files and the Linux kernel). Once the Linux kernel loads, it no longer depends on the BIOS, and it will access the whole disk.

What exactly is your hard disk partition structure? Run the command **sudo fdisk -l** from a terminal window from an Ubuntu Live CD system. Post the results to the forum.

---

### Post by meierfra. on 2009-03-12
> but to create an extra "boot" partition of about 50 Mb

Due  to  the frequent kernel updates, I  recommend 200 Mb for the boot partition.  (50 MB is enough for about 4 kernels, but it  is easy to collect more than that)

---

### Post by OxentroT on 2009-03-13
> What exactly is your hard disk partition structure? Run the command sudo fdisk -l from a terminal window from an Ubuntu Live CD system. Post the results to the forum.

Thanks for the responses
I have attempted running the Ubuntu live CD to no avail, the most I have got out of my attempts is a prompt change to 'D:/>'. I will be sure and search up a list of applicable commands for the next time I get the chance. 

As for my HDD partition structure, this is where I may have messed up by installing ubuntu 100%
ubuntu is the only partition I have anymore.

---

### Post by dstew on 2009-03-14
To get the Live CD to boot, you need to change your boot disk order in your BIOS. How did you install Ubuntu in the first place? Didn't you run the Live CD then?

---

### Post by OxentroT on 2009-03-14
I have produced a copy of 'Super Grub' on cd-r. However I do(and this may be the n00b talking)-not -know -how to run through 'D:\>'.

---

### Post by tommcd on 2009-03-14
Are you installing Ubuntu using Wubi in Windows? Or are you installing Ubuntu the real way, to a dedicated partition.
As suggested previously by others:
set your computer's BIOS to boot from CDROM.
boot up the live CD, open a terminal (applications > accessories > terminal) and run:
```
sudo fdisk -l
```
to list your partitions.
If you set the BIOS to boot from the CDROM you should be able to boot the Super Grub Disc and reinstal grub.

---

### Post by OxentroT on 2009-03-15
Truth Be Told, I *REALLY* should have learned a *little* more about what I am doing before going ahead with a full on partition-wide installation. Looks like I need to go get me a couple of books, take my lil' think pad into a shoppe for a revival.   
             
:) -Thank You all for helping this impatient lemmings.

---

### Post by tommcd on 2009-03-15
So you are installing to the hard drive, and selected to autopartition the drive and let Ubuntu use the whole hard drive. Is that correct? How many hard drives do you have? If you have more than 1 drive it is possible that grub is pointing to the wrong partition. Can you boot the live CD and run:
```
sudo fdisk -l
```
For a good guide to getting started in Ubuntu, see this:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
Here is everything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

