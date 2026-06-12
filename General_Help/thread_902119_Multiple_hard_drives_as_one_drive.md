---
title: "Multiple hard drives as one drive"
date: 2008-08-27
forum: General Help
---

### Post by mishathegoat on 2008-08-27
Okay I have like like five 4G hard drives. And I was wondering if it were possible to get my operating system (Linux or Windows) to see them all as one hard drive. Maybe some sort of adapter or connector?

Any help is appreciated

Thanks

---

### Post by sdennie on 2008-08-27
It sounds to me like you want to investigate either RAID or LVM (or both).  They will let you see your disks as one contiguous disk depending on how you configure them.  There are many, many guides for setting this up and you can actually try setting it up in a virtual machine before doing the install on your disks (I did so using VirtualBox and it was very useful in getting a feel of how I was going to setup my server).

---

### Post by amitkher on 2008-08-27
vor, raid (sw raid) and lvm come after the OS comes alive. mishathegoat wants the OS to see the drives as one combined drive. A hardware raid controller that supports raid 5 should do the trick.

It is possible to do it with software raid and/or lvm but to boot the OS you will need a plain partition. This can be done while installing ubuntu by creating a /boot partition (around 200MB partition). Don't include this /boot partition in the raid/lvm that combines the drives. 

This is for Ubuntu. No idea for windows but there must be a way.

---

### Post by kaligus on 2008-08-27
FWIW having tried both RAID and LVM I would generally go with LVM unless the new additive drive needs to be accessed on a dual booter in which case I would tend toward hardware (motherboard) RAID.

---

### Post by c2olen on 2008-08-27
> **amitkher said:**
> vor, raid (sw raid) and lvm come after the OS comes alive. mishathegoat wants the OS to see the drives as one combined drive. A hardware raid controller that supports raid 5 should do the trick.

Not necessarely true.
You can set up the sw-raid and for autodetect, so it will be brought online during boot, even before the filesystems are to be mounted. You need to have it in your kernel of course. Unless you run your own modified kernel, this shouldn't be a problem.

I would use sw-raid if you want to use it as one contiguous space. Use raid-5 for protection if one of the disks would fail. You should end up with a single disk image, represented by /dev/mdX, where X is the number of the raid set you created.

[http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.8](http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.8)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

---

### Post by mixmaster on 2008-08-27
The problem with raid is that if you lose one disk you will lose the entire filesystem (assuming raid 0).  lvm would work ok but can be a bit of a pig to administer if you are not used to it.

An alternative would be create a filesystem on each drive then use unionfs to combine them.

I have to ask, though, why you are playing with 4Gb drives?  Are they actually memory sticks of some kind?  If they are genuine rotating magnetic media then I would imagine they are pretty ancient and I'd dump them and buy a new sata drive - with 250Gb drives coming in at about 30 pounds I think attempting to use ancient media is a false economy.

---

### Post by amitkher on 2008-08-27
> **c2olen said:**
> Not necessarely true.
You can set up the sw-raid and for autodetect, so it will be brought online during boot, even before the filesystems are to be mounted. You need to have it in your kernel of course. Unless you run your own modified kernel, this shouldn't be a problem.

I would use sw-raid if you want to use it as one contiguous space. Use raid-5 for protection if one of the disks would fail. You should end up with a single disk image, represented by /dev/mdX, where X is the number of the raid set you created.

[http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.8](http://tldp.org/HOWTO/Software-RAID-HOWTO-5.html#ss5.8)
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

I'd like to know how to use raid for /boot. The issue here is not having it in the kernel as the kernel image is stored in /boot (assume for simplicity). The bootloader needs to know how to read raid so that it finds the kernel image and boots from it.

The links that you point to don't explain this at all. Some other section in the article of your first link ([http://tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.3](http://tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.3)) mentions that RAID 1 can be used. You just use ONE of the constituting devices of the RAID 1. This is not what we are talking about here.

Your second link explicitly mentions that /boot and / are not being discussed there. Could you point to some resources that can help set up raid on /boot?

---

### Post by c2olen on 2008-08-29
Ok you guys,

It has been a while since I set this up, so I'll have to digg into my memory for this, but I think I can retrace my steps.

The result of my steps is booting off a software RAID1 device using GRUB (LILO should work too). I have LVM2 in place as well, but not for all filesystems. The filesystems /, /boot usually require no LVM since they don't grow.


Make your disks/partitions raid-autodetect (type fd) when setting them up in fdisk.
During boot, these partitions can be detected automatically and brought online. 

Here's an example on a full-disk raid and several partitions-per-disk raid. Please note that these two examples are from two different raid sets, not the same.
It is possible however, to get a partition from a certain disk to be part of a raid set with a full-disk, as long the sizes are the same.
In my example, disk sda is part of a raid-1 set with sdb, and hda is part of a raid-1 set with hdb.


```

acapulco:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         122      979933+  fd  Linux raid autodetect
/dev/hda2             123         152      240975   fd  Linux raid autodetect
/dev/hda3             153         213      489982+  fd  Linux raid autodetect
/dev/hda4             214       14596   115531447+   5  Extended
/dev/hda5             214       14596   115531416   fd  Linux raid autodetect

```Here's the output of /proc/mdstat. You can see that each partition being mirrored is being represented by an md device.
hda and hdb have several partitions, and sda and sdb are full disk raid-sets.
```

acapulco:~# cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 hda2[0] hdc2[1]
      240896 blocks [2/2] [UU]

md2 : active raid1 hda3[0] hdc3[1]
      489856 blocks [2/2] [UU]

md3 : active raid1 hda5[0] hdc5[1]
      115531328 blocks [2/2] [UU]

md5 : active raid1 sda1[0] sdb1[1]
      488383936 blocks [2/2] [UU]

md0 : active raid1 hda1[0] hdc1[1]
      979840 blocks [2/2] [UU]

unused devices: <none>

```


When you have setup the partition types (fd), you can add them to a raid set using mdadm.
In this example we use a two (-n2) partiton mirror (-l1).  I suggest you read the mdamd man pages for more details on it.
```

#>mdadm -C -n2 -l1 /dev/md0 /dev/hda1 /dev/hdb1

```Now we have the raid set synchronising. Check /proc/mdstat to see the progress.
You can either format a filesystem on /dev/md0 (or whatever number it has) or make it a LVM type device using fdisk on /dev/md0, and set the partition type to LVM (8e).

I havent tried booting from an LVM device, but i guess it should be possible when you have a initrd holding the LVM modules.
I just boot from /dev/mdX devices, and have LVM start during the bootprocess.

Here's my filesystem layout for reference.

```

acapulco:~# df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/md0                      897M  564M  286M  67% /
/dev/md1                      221M   59M  151M  29% /boot
/dev/md5                      459G  298G  138G  69% /mnt/nasdata
/dev/mapper/rootvg-usr       5.0G  1.5G  3.3G  32% /usr
/dev/mapper/rootvg-var       5.0G  247M  4.5G   6% /var
/dev/mapper/rootvg-tmp      1008M  264M  694M  28% /tmp
/dev/mapper/rootvg-home     1008M   53M  904M   6% /home
/dev/mapper/rootvg-vmware    69G   22G   46G  32% /vmware

```All you now have to do, is fill the new devices with your files required to boot and edit your bootloader to match the new device.

One entry from grub:
```

title           Debian GNU/Linux, kernel 2.6.25-2-486
root            (hd0,1)
kernel          /vmlinuz-2.6.25-2-486 root=/dev/md0 ro
initrd          /initrd.img-2.6.25-2-486

```some other good references:
[http://hilli.dk/howtos/lvm2-and-software-raid-in-linux/](http://hilli.dk/howtos/lvm2-and-software-raid-in-linux/)
[http://www.brad-x.com/2007/07/22/linux-software-raidlvm2-with-root-on-raid-howto/](http://www.brad-x.com/2007/07/22/linux-software-raidlvm2-with-root-on-raid-howto/)
[http://www.linux.org/docs/ldp/howto/Software-RAID-HOWTO.html#toc11](http://www.linux.org/docs/ldp/howto/Software-RAID-HOWTO.html#toc11)

---

### Post by c2olen on 2008-08-29
In case you are missing /dev/md2 and /dev/md3 in the examples above;

/dev/md2 is actually swap (yeah I know, I mirrored my swap, which makes no sense)
/dev/md3 is the basis for the LVM. 
/dev/mapper/rootvg is build upon /dev/md3.

So I have made all other filesystems like /home, /usr, /var inside the LVM rootvg (root volume group, which can be any name you give it).

---

