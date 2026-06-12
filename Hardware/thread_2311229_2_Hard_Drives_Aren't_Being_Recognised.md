---
title: "2 Hard Drives Aren't Being Recognised"
date: 2016-01-25
forum: Hardware
---

### Post by ThePowerpuffGirls on 2016-01-25
I have two Toshiba hard drives (160GB and 750GB SATA). When I plug them in (either USB or internally) they won't be recognised. Any other hard drives do, no trouble.
I can hear them running, they sound like they are running smoothly.

It is one mystery I can not solve and need your help.

- Blossom

---

### Post by oldfred on 2016-01-25
If internal, does BIOS show drive by model in list of available drives?

If shown, does Disks show drive and in Disks upper right corner is a icon for tools and Smart Disk. That should show if disk to good or bad. It can run tests also, but all I know is if not good time for a new drive.

Then if still shown what does this show?
sudo parted -l

---

### Post by ThePowerpuffGirls on 2016-01-25
The BIOS doesn't show the drive, neither does Disk Management.

> borden@Office2:~$ sudo parted -l
[sudo] password for borden: 
Model: ATA SPCC Solid State (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  512MB  511MB  fat32              boot
 2      512MB   112GB  111GB  ext4


Model: ATA WDC WD10EZEX-22R (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  1000GB  1000GB  ntfs

Edit: After running the command, the 160GB showed up in Disk Management after a seconds. I tried to reformat it, and get the following error:
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdg, scheme=0
got it

- Blossom

---

### Post by oldfred on 2016-01-25
If external is it getting enough power? Some USB ports do not offer enough power. And drive may not come up to speed when rebooting for a bit.
If Internal check that cables/connections are good.

---

### Post by ThePowerpuffGirls on 2016-01-28
I've used it successfully on other drives, that are the same. Is it possible that some 2.5 HDD require more power?

- Blossom

---

### Post by sudodus on 2016-01-28
Yes.

I guess these are external drives. Is there a way to get separate power (a power cable)? If not, you might succeed with a USB hub, that has a separate power supply. Search the internet for **usb hub with power supply** and find for example

[http://lifehacker.com/five-best-usb-hubs-1414094277](http://lifehacker.com/five-best-usb-hubs-1414094277)

---

### Post by ThePowerpuffGirls on 2016-01-28
I have USB 3.0 PCI connected to a power cable. and a USB to SATA cable. I''m trying it now. So far, no luck.

Edit: They originally were from a laptop.

- Blossom

---

### Post by sudodus on 2016-01-29
Different 2.5" SATA drives need different amount of power to work. SSDs need less power than HDDs, and there is a variation within the HDD class.

What about the 'USB to SATA cable.'? It should also have a power supply.

There could also be a compatibility problem between the USB 3.0 PCI device and the 'USB to SATA cable' or between the 'USB to SATA cable' and the SATA drive.

---

### Post by ThePowerpuffGirls on 2016-01-29
My Sister had taken the broken HDDs, dismantled them and taken them to recycle, unfortunately. We'll probably never know what the problem was. :(
We had some other HDD that was definitely broke (3 Desktop drives, and the 3 laptop drives). Fortunately, she destroyed the disks platters from the laptop drives.
Thank you very much for you help. :)

- Blossom

---

