---
title: "RAID Configuration"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by dr_jaymahdi on 2008-12-23
Hi,

I am a newbie when it comes to RAID configurations in Linux.  I have 4 HDDs in which all the sizes are 500GB.  I am wondering if it is possible for me to set up a RAID configuration of the following:

2x500GB Raid 1 Striped to combine 1TB

another 2x500GB Raid 1 Striped to combine 1TB

And then, can I use both of those striped Raid's as a mirror like Raid 0 or am I dreaming?  I am not sure what kind of nested Raid mode would this be.

If anyone has the patience to answer my question, it would be greatly appreciated!

Thanks.

---

### Post by lemming465 on 2008-12-26
Striping across mirrors is a very standard way of building high-performance reliable storage, particularly when you need better write performance than you would get from RAID-5 (striped with parity).  It's usually called RAID-10 or RAID-1/0 (first mirror [1], then stripe [0]).  For reliability reasons you want to stripe across mirrors, not mirror across stripes, as that decreases the odds that two simultaneous disk failures will cause data loss.

There are at least 3 ways to do this.

**option 1 - hardware**
If your disk controller is fancy and expensive and supports true hardware RAID (as opposed to software "fakeraid"), it may offer a RAID-10 mode in hardware.  In this case any operating systems would see only the logical disk array presented by the disk controller, not the underlying physical drives.  This is very common when building database servers.  If you have the expensive disk controller, you can multiboot, do graphical installs, and have an easy time of it - as long as the controller is supported by the OS.  Usually it is; typical chipsets are from LSI, Megaraid, or Adaptec.

If you don't have hardware support for the RAID, Linux systems can do it in software at the OS level.  Microsoft server operating systems can too; but they leave that out of their consumer versions.  Do not expect to be able to dual-boot systems using either fakeraid or some kind of software RAID.  If you only plan to use the system with Linux (or with Linux as the host OS and other things as virtual guests), this is not a problem.

You'll have to use the Ubuntu alternate install CD's, or create the disk layout in advance using a live CD, as the ubuntu GUI installer isn't smart enough to handle mdadm and LVM stuff.  The Redhat enterprise installer is; I'm not sure about Fedora; probably.

**option 2 - mdadm Linux OS RAID**
"mdadm --create --level=raid10 dev0 dev1 dev2 dev3" should do what you want at a command line level.  Usually the devices would be /dev/sda /dev/sdb /dev/sdc /dev/sdd, but it will depend on exactly what your hardware is and how things are cabled.  The result would probably be called /dev/md0. It will act like one giant partition, so you can run mke2fs against it, but you can't subdivide it.  If one giant partition is an OK result, this is an easy option.

**option 3 - mdadm / LVM Linux OS hybrid**
Another option is to use mdadm to create two mirrors, /dev/md0 and /dev/md1.  Then use LVM2 to stripe across them.  You start by using *pvcreate* to designate the RAID-1 devices as LVM physical volumes, then use *vgcreate* to add them into a volume group, and lastly use *lvcreate* to make logical partitions.  Similarly to option 2, you'll end up with a block device like /dev/vg0/lv1 which you can run mke2fs or whatever against. This is what I usually do on severs when I don't have hardware RAID.  (But in my day job those are Redhat boxes, and I build the disk layout by hand-editing my kickstart templates.)

I think the disk partitioning menus on the Ubuntu alternate install CD's can step through this process for you.  Just keep the order in mind: 1) make mirrors  2) make physical volumes 3) make a volume group 4) make partitions and you should be OK.

---

### Post by dr_jaymahdi on 2009-01-05
Thanks very much for your detailed reply.  I believe this will help me during the installation with Ubuntu Alternate.

Have a great day!

---

### Post by Rithmarin on 2009-01-06
I run intrepid / vista in a dual boot using nvidia mobo raid (raid 0). This is new in Intrepid, previous versions didnt (easily) support this type of setup. 

I used the alternate CD to install.

---

