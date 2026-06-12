---
title: "Thinking about getting a Synology or QNAP NAS; any thoughts (cautions)...?"
date: 2018-05-14
forum: Hardware
---

### Post by bobsone on 2018-05-14
Hi
We need to share/sync some files between 4 different OS's in 5 different computers, a Linux Lite desktop, a windows 8.1 desktop, a Mate 18.04 desktop, a Mate 16.04 laptop (soon to be 18.04) and a windows 10 laptop.

We are looking for a simple(r) way to transfer and sync files between our computers, we will only need a little bit of storage (1-2TB) and a backup function would be nice.
So far we have been looking at something like Synology DS218J or QNAP TS-213P.

From what I have seen both models will do what we need, but most info is from windows/mac users, does anyone have experience with and/or thoughts about either of these models (or something like them).

Thanks.

---

### Post by TheFu on 2018-05-14
All cheap NAS devices (for certain values of "cheap") are a trade-off between $$$, expertise and time.

I would never buy devices like these, especially for just 2 data disks, since an old PC with a few disks inside running Ubuntu Server can perform the same tasks with greater flexibility and usually better performance. Plus, when a disk fails, and all disks fail, you don't have to seek out experts to attempt data recovery if the commercial device uses a proprietary LVM or file system solution.  OTOH, if you don't have the requisite skills for setting up an NFS and CIFS server yourself, paying for hardware that has a pretty GUI might be smart.

I built a DAS/NAS using a $50 intel CPU + $50 motherboard and $26 in RAM a few years ago.  Today, that box has over 24TB of storage with 6 internal HDDs and 4 external disks connected by a cheap USB3 array.  The external array is only used for backups. I don't trust USB3 for primary storage.

I would use NFS for all Unix clients and CIFS only for Windows clients. 

Whatever you do, always google for "failed" and "hacked" with any vendor + model under consideration.  Storage devices on a network need to be patched every month, just like normal computers and printers.   Also, google for backup failures, so if you use this for that purpose, you get an idea about which failures are happening to others.

Depending on how important this data is, I'd choose the hardware and how dedicated I wanted the OS/software to be.  NAS-for-free or other FreeNAS builds can provide very impressive, enterprise-level, solutions with the correct hardware. For a home, something similar to what I built could make sense.  If size is important, there are Odroid Q4 devices that support multiple SATA disks.  [https://category5.tv/shows/extras/episode/525-odroid-cloudshell-2-xu4/](https://category5.tv/shows/extras/episode/525-odroid-cloudshell-2-xu4/)

---

### Post by bobsone on 2018-05-20
Thanks for the reply,
Your points are helpful, a "Pretty GUI" is often nice but I am always up for having a go at setting something up, I will have a  look at how hard it is before I spend anything.
I guess I have more research to do...  
The Odroid Q4 looks interesting and I like the small form of the Cloudshell (imagine what it will look like once it has sucked up all the dust it can access). I have also seen a Kickstarter that did ship some kits called the Helois 4.

Regards

---

### Post by scotc on 2018-05-22
I use a Synology DS214 with one drive in it.
It is compatible with Ubuntu, especially the later versions 14 and above.  Before that it could be flaky and one would have to repeatedly login or fail to login.

TheFu's advice is good though: synology software is perhaps a bit bloated.  There are a lot of installed apps that I don't need or can't work out how to use e.g. file streaming so that you can store your music centrally...

I've not had a drive or OS failure on the Synology in the 3 years I have owned it. 

What DOESN't seem to work is the alleged network printer function.  I should say I haven't tried it for a couple of years (life is too short to repeatedly waste on pointless computing tasks).  The DS214 has a usb port.  I use it to backup the DS to a removable drive once in a while.  
Even that is a bit of a faff - the inbuilt software (bloatware) doesn't work very well, indeed it automatically compresses and pseudo encrypts the files - no use if I need to recover but my DS is dead.  Therefore I just use a drag and drop between the two drives.

I chose to get a NAS so that our photos would be shared-access between two laptops.  The wife doesn't use it because she has OS 12.04 and won't allow me to upgrade it for her, so the photos are still only accessible by me!

The bloat ware contains various cloud backup options - useless unless you have a) LOTS of cloud backup space and b) a fast broadband UPLOAD connection

---

