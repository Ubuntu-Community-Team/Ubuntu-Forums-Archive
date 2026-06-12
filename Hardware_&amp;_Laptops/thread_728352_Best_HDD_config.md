---
title: "Best HDD config?"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by prodezigner on 2008-03-18
I've got a 250GB 7200RPM Western Digital drive, and a 80GB Seagate drive (also 7200RPM). Both are SATA, and I'm running Vista 64-bit and Ubuntu 7.10 64-bit. I kind of want to dabble into RAID, partitioning my 250 into one 80GB partition and the rest as storage, and then using the two 80GB in RAID0. I don't know anything about RAID and would love some expertise. I do a lot of video work and I would love to squeeze more performance out my my machine...

AMD Athlon 64 X2 5200+ AM2
abit AN9 32X
2GB DDR2 800 RAM
256MB GeForce 8600 GTS OC
18x DVD+/-R (Optiarc)
250GB WD SATAII
80GB Seagate SATAII
160GB Seagate External
20" HP w2007 Monitor

---

### Post by penguinpi.com on 2008-03-19
Do you have a hardware RAID controller? if so it should have its own BIOS. there are some things to consider when going with RAID though. if the drives are different sizes it will truncate the RAID partition to whatever the smallest drive is. you will also need to set up a LVM partition, because when you create a RAID array it will make a logical partition.

---

### Post by bigredradio on 2008-03-19
I am not sure what the previous post is referring to, but LVM and RAID are separate storage schemes. To get better performance you what to do striping (multiple I/O paths to gain performance). That can be done with either RAID or LVM. 

For software raid, you combine multiple devices into one RAID device. A device can be an entire disk, a partition, or a logical volume (LVM). If you want to go the RAID route, then create a partition of equal size on each disk. If you want 60gb, then 60gb on each disk. The RAID device is limited in size to smallest device you are using to build the RAID device. For example, you create two paritions, one 60GB and the other 80GB. You will end up with a 120GB RAID device with RAID0. 60+60 not 60+80. If you are mirroring, it would be 60GB total. Make sense?

If you are new to RAID, I would recommend not using RAID0 on the root filesystem. Use it for data storage only. Booting / on RAID gets complicated. So create the RAID device and make it /home/movies or something.

So, more detailed steps for RAID can be found online and within the man pages. Here is a basic breakdown. (I'll let you search for the details)

Create two partitions of equal size with fdisk. The partition type should be "fd".
Use the mdadm command to create the raid device. 
Create a filesystem on the new md0 device.
Create a mountpoint for it (/home/mymountpoint)
Put an entry in /etc/fstab for the new filesystem.

As far as windows using this, you will have to use hardware RAID for that. What I described is software RAID. 

If you are trying to do this with disks that are already in use, you are in a pickle. You should consider reinstalling and create the RAID devices during the install or get two new disks to do this with. Maybe someone savvy with a partition program can help you reallocate some space. Typically once you have partitioned a disk, you are stuck. It gets tricky repartitioning a disk and not losing any data. Good luck

---

### Post by penguinpi.com on 2008-03-19
I probably should have used partition the way I did. The way I have it set up on my servers is RAID 0 across 6 36GB SCSI drives, and my RAID controller created a  216GB logical drive and I have to set up LVM for it to work.

---

### Post by bigredradio on 2008-03-20
> **penguinpi.com said:**
>  I have to set up LVM for it to work.

Why would you have to use LVM? If it is hardware or software RAID, then it will show up as one dis k and you can partition it however you like. If you are seeing 6 disks, then you are not using RAID.

I am a fan of LVM, so I would advocate using it anyway, but because you have RAID does not force you to use LVM.

---

### Post by penguinpi.com on 2008-03-20
Well GRUB returns an error, otherwise

---

