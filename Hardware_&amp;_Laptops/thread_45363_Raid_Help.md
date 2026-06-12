---
title: "Raid Help"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by siancell on 2005-06-29
Hello, I have a Ubuntu 5.04 "The Hoary Hedgehog" installed and I would like if anyone can help me mount 400 GB SATA RAID array into ubuntu, Is there a way to mount the array with out erasing anything from the 400 gigs? I'm also using 2x60 GB hard drives using a promise fastrak 378 controller I believe. I'm new to linux so I have looked around many forums and here but always seem to find threads that already have the array mounted though having problems with it.

---

### Post by norman_h on 2005-07-05
We need more info about your RAID setup.

---

### Post by siancell on 2005-07-06
I have 2x200 SATA harddrives set up to stripe on a VIA Serial ATA RAID controller.

---

### Post by CHumPy on 2005-07-07
I'm in a similar situation. I have an Asus a8v deluxe mobo and currently have 2x200 western digital sata drives in a raid 0 array, with xp32 and xp64 installed and working fine. what im planning to do is format, make the same array again (i assume the original dies in a format? im not sure), then install xp64 and ubuntu 5.04. but from what i've been searching/reading on the forums there could be a problem with that. oh and the drives are on the promise fastrack 378 controller. so whatever help people can give here is probably going to help both of us  :grin:

okay so just messing around with stuff and seeing what happened with ubuntu installer, it didnt recognise that there was a raid array - does this mean i have a software? hybrid? hardware raid array. windows sees the array but ubuntu doesnt.

---

### Post by siancell on 2005-07-07
Oh by the way, if its too much to ask. Is there a way to mount them into ubuntu with out erasing all the data cuase I have 289 GB used out of the 400.
Thank you

---

### Post by norman_h on 2005-07-07
There are two ways to get RAID going under linux.  Software RAID and hardware RAID.  Each has different ways of getting to the end result.

There is an excellent [HOWTO](http://www.tldp.org/HOWTO/Software-RAID-HOWTO.html) which details software RAID under linux.  It details the use of two different tools for administrating RAID under linux.  Both raidtools and mdadm can be used.  I have a preference to mdadm as it is one compact tool and not a collection of tools.

Some motherboards come with SATA chipsets that allow RAID.  These might seem like hardware RAID, however, they are really a hybrid hardware/software.  I know that the nForce chipsets are quite often like this.  These hybrids don't work in linux afaik.  Dedicated PCI RAID cards are usually hardware based RAID.  If real hardware RAID is used and supported in the kernel; then the device will probably be autodetected and be accessable somewhere under /dev/rd/* or /dev/sd* depending on the brand of card/chipset.  It is important that the kernel has RAID support, ubuntu should do this by default.

It sounds like you guys want to do RAID0 or RAID1.  RAID0 is the striping option which gives a performance increase.  As always, it is *heaps* easier to start from scratch with new drives.  A rough outline of the method to create a RAID setup from scratch on brand new drives (or drives whos data can be wiped) goes as follows:

1. create RAID partitions on your physical disks of type FD "linux RAID autodetect".  Use the tool cfdisk from the console to acomplish this.  ```
cfdisk /dev/hda
cfdisk /dev/hdb
```reboot to save changes
2. use mdadm to create /dev/md0 as a RAID0 array consisting of /dev/hda1 and /dev/hdc1.```
mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/hd[ac]1
```
3. format the new device /dev/md0 into whatever filesystem you want your RAID array to use.  ie use the command ```
mkfs.ext2 /dev/md0
```
4. create a mountpoint and mount /dev/md0 onto the correct point in your filesystem.  ```
mkdir /mnt/raid-array
mount /dev/md0 /mnt/raid-array
```

If you want to move an existing RAID setup from another OS onto ubuntu, then you might have problems.  If it is pure hardware RAID, then it should be picked up as long as the RAID chipset is supported under linux.  If it is a software RAID from another OS, then you might have a few problems on your hands and will need advice from someone else as I am unable to offer much help with that due to lack of experience.

I'd love to setup ubuntu on a RAID0 with my GA-K8NS-ultra-939 mobo and its Sil3112 chipset, but it aint gonna happen easily. I managed to find some info on mailing lists sometime ago and I concluded that it would be possible to do it.  I found that with a lot of hacking it is also possible to get RAID0 working partially in a very hacked sort of way.  The method involved something like putting the raid modules in the initrd image so that the kernel would be able to have access to the RAID partitions at boot time. There would also have to be a seperate /boot partition that was on a non-RAID partition where the initrd image would reside.

Unless you have pure hardware RAID, then it is going to be difficult to get ubuntu running on single RAID setup under software.  While I'm not using RAID0 at the moment, I have played with it before and there is a definate performance increase of about 1.8x, but this is only really noticeable when loading apps from the hard disk. Once the apps are in the RAM the RAID0 makes no difference unless you run out of RAM and start using swap space on you hard disk.  I have 512Meg of RAM and find that it is enough, more is always good though.

---

### Post by norman_h on 2005-07-07
[QUOTE=siancell]Hello, I have a Ubuntu 5.04 "The Hoary Hedgehog" installed and I would like if anyone can help me mount 400 GB SATA RAID array into ubuntu, Is there a way to mount the array with out erasing anything from the 400 gigs? I'm also using 2x60 GB hard drives using a promise fastrak 378 controller I believe. I'm new to linux so I have looked around many forums and here but always seem to find threads that already have the array mounted though having problems with it.[/QUOTE]
What file system is used on the drives whose data you wish not to loose?  What chipset are they connected to?

---

### Post by siancell on 2005-07-11
Its is formated in NTFS and the chipset is VIA K8T800Pro + VT8237. I'm not really sure which of the chips is the one responsible for the RAID though.

---

### Post by joe897897 on 2005-07-17
Same problem, it is pure hardware raid 0 (promise fasttrack 100 tx2) for me but i want to install ubuntu 5.04 directly on the raid, not to ba able to read it after a first install on another disk :
Is it possible ?

---

### Post by Xizorbg on 2006-06-04
](*,) Hi All-

I already wrote Chumpy and I figured I could ask you all as well.  I am having a devil of a time getting my a8v to run in ubuntu on a RAID 1 system.  I have 2 WD 74gB raptors, an AMD 3200+ CPU.  I tried following some how-tos but when I set up my partitions, it either says no root is installed (even though I selected '/') or that the partitions have the same moint point.  I also noticed that under the description, one HD is scsi 4 (0,0,0) and the other is scsi 5 (0,0,0).   I have them connected to the South Bridge PROMISE controller, as the Northbridge VIA would not let ubuntu really install.  Any help you can offer would be greatly apprecaited.

Thanks,
Xizor

---

