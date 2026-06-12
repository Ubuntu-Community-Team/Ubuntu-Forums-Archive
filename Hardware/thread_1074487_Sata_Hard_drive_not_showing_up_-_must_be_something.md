---
title: "Sata Hard drive not showing up - must be something daft"
date: 2009-02-19
forum: Hardware
---

### Post by dredwerker on 2009-02-19
Hi all,

I have 4 drives two seagate 750 gigs  and two 1tb samsungs and 4 sata connections in my asus mobo.

All 4 of them show up in the bios.

I have formatted and partitioned them using gparted but one of the 750s doesnt show up in the 'computer' bit in nautilus.

My fstab doesnt have anything about drives in it
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=be403c25-33c9-4cbe-9cde-639310b7e3ee /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=d1e97f13-1fee-4190-a60d-c831c1b96cc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

my fdisk -l looks strange to me:
```

Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc
Cannot open /dev/sdd
```

I have had 4 hard disks before in this but two of them were IDE.

Am I missing something obvious?

Also - they were being odd when I partitioned them as I had to do it originally using system rescue gparted.

TIA Dred :)

---

### Post by digitalbenji on 2009-02-19
Hi,
   I had an interesting issue similar to this with a slackware system yesterday.  I think that udev (which handles the mapping and population of the /dev folder) hasn't properly triggered to map UUID's to your drives.  Try running ```
sudo udevadm trigger
``` and see if that makes fdisk behave better.  My guess is that it will, and you can then partition the disks and add the appropriate fstab entries.

---

### Post by dredwerker on 2009-02-19
> **digitalbenji said:**
> Hi,
   I had an interesting issue similar to this with a slackware system yesterday.  I think that udev (which handles the mapping and population of the /dev folder) hasn't properly triggered to map UUID's to your drives.  Try running ```
sudo udevadm trigger
``` and see if that makes fdisk behave better.  My guess is that it will, and you can then partition the disks and add the appropriate fstab entries.

No joy unfortunately. Thanks for the quick response though

here is my output from the command

```
sudo udevadm trigger --verbose|grep sd
/bus/scsi/drivers/sd
/devices/pci0000:00/0000:00:0e.0/host0/target0:0:0/0:0:0:0/block/sda
/devices/pci0000:00/0000:00:0e.0/host0/target0:0:0/0:0:0:0/block/sda/sda1
/devices/pci0000:00/0000:00:0e.0/host0/target0:0:0/0:0:0:0/block/sda/sda2
/devices/pci0000:00/0000:00:0e.0/host0/target0:0:0/0:0:0:0/block/sda/sda3
/devices/pci0000:00/0000:00:0e.0/host0/target0:0:0/0:0:0:0/block/sda/sda4
/devices/pci0000:00/0000:00:0e.0/host1/target1:0:0/1:0:0:0/block/sdb
/devices/pci0000:00/0000:00:0e.0/host1/target1:0:0/1:0:0:0/block/sdb/sdb1
/devices/pci0000:00/0000:00:0f.0/host2/target2:0:0/2:0:0:0/block/sdc
/devices/pci0000:00/0000:00:0f.0/host2/target2:0:0/2:0:0:0/block/sdc/sdc1
/devices/pci0000:00/0000:00:0f.0/host3/target3:0:0/3:0:0:0/block/sdd
/devices/pci0000:00/0000:00:0f.0/host3/target3:0:0/3:0:0:0/block/sdd/sdd1
/devices/virtual/tty/ptysd
/devices/virtual/tty/ttysd

```

---

### Post by digitalbenji on 2009-02-19
after you do that, fdisk -l still gives the same output?  are the sata disks partitioned already?

---

### Post by dredwerker on 2009-02-19
> **digitalbenji said:**
> after you do that, fdisk -l still gives the same output?  are the sata disks partitioned already?

yeah fdisk -l :

```
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc
Cannot open /dev/sdd
```

They are all partitioned and the terabyte shows up but not the other 750. The 750 that doesnt show up is on sata 4. 

I suppose I could take out the 750 and see if fdisk works again or swap the channels or something.

---

### Post by digitalbenji on 2009-02-19
Yeah, although it sounds simple, I guess I'd verify that the disk not showing up doesn't work on a different channel, and that it is getting power.  I'll research this a bit, see if I can dig anything else up for you as well.

---

### Post by dredwerker on 2009-02-19
> **digitalbenji said:**
> Yeah, although it sounds simple, I guess I'd verify that the disk not showing up doesn't work on a different channel, and that it is getting power.  I'll research this a bit, see if I can dig anything else up for you as well.

Thanks

---

### Post by dredwerker on 2009-02-19
I have now taken out the 1tb and put the 750 in its place and now I can see it.

> 
fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc

so fdisk -l has just one less drive :)

I shall try and take both the 1tb and the 750 out and see if fdisk -l works again.

---

### Post by dredwerker on 2009-02-19
> **dredwerker said:**
> I have now taken out the 1tb and put the 750 in its place and now I can see it.



so fdisk -l has just one less drive :)

I shall try and take both the 1tb and the 750 out and see if fdisk -l works again.

I have now taken them both out and put them both back in and it works now.

I did it whilst they were powered up the first time.

I have to admit that I did an fdisk -l and not a sudo fdisk -l so that may have been a red herring :)

In essence solved for now but I am not entirely sure how.

---

### Post by caljohnsmith on 2009-02-19
Are you running fdisk with "sudo"? It doesn't look like you are. How about posting:
```
sudo fdisk -lu
```
With all your drives connected.

---

### Post by dredwerker on 2009-02-19
Yeah - thanks tis all solved now. In part to the sudo being missed but also due to randomly pulling each one out and putting them back and one more reboot.

May be something else helped liked the original command by digitalbenji. I just dont know.

Thanks all.

---

