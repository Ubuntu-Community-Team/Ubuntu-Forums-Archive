---
title: "vista partition &quot;non-existant&quot;"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by donmiguel on 2009-02-08
Hi

I bought myself a new laptop, with vista pre-installed of course (as dictated). So I shrinked the vista partition, worked well. Formatted the free space to a ext3 and a linux-swap partition. very well. Then I installed ubuntu 8.10, worked marvellous.

When restarting after the installation, it automatically went into Ubuntu and didn't even give the option to choose vista. So I opened gparted again and saw, that the vista-partition and the vista-recovery partition are just not existant (recognised). But, the size of the harddisk (300gb) indicated in gparted is too small, the ~40 gb missing correspond exactly to the space the two vista-partitions occupy together. So, they should still be on the harddisk, but are just not recogniced by nothing (also not listed in /dev/).

Thinking about what the problem could be, it occured to me, that left checkbox on "primary partition" for the linux parition, shouldn't I have done this?

And what could I do in order to try to get Ubuntu to recognize the other partitions and add them into menu.lst of grub??

Thanks for any hint!!

---

### Post by caljohnsmith on 2009-02-08
How about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output. That will give us a better idea of what your HDD's partitioning scheme looks like, and whether it looks like you can recover your Vista partition.

---

### Post by donmiguel on 2009-02-08
ok, here it goes:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x33053305

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    606919634    303459786   83  Linux
/dev/sda2        606919635    625137344     910885   5  Extended
/dev/sda5        606919698    625137344     9108823+   82  Linux swap / Solaris


does not look good, does it :(

---

### Post by caljohnsmith on 2009-02-08
Ouch, unfortunately that doesn't look good; it appears you unintentionally overwrote your Vista partition when installing Ubuntu. Just for future reference, I would suggest using the "manual" partition option when installing Ubuntu, because I think that gives you greater control of where Ubuntu gets installed to. Do you have some really critical files from your Vista install you want to try and recover? It will be alot of work, and you'll need another drive at least as big as your 320 GB drive to save all the recovered files to; it's up to you. Let me know if you want to look into data recovery or not, but otherwise I would suggest reinstalling Vista, and then try installing Ubuntu again after that. Let me know what direction you would like to take.

---

### Post by donmiguel on 2009-02-08
****.
Thanks for your support! Well, I'm not sad at all that i don't have anymore Vista, I'm more worried about warranty problems... I have to check that. I have not had a single personal file in Vista..

Well, thanks
greets

---

