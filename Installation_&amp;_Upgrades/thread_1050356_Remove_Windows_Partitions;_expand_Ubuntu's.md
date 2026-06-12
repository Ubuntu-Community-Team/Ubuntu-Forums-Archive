---
title: "Remove Windows Partitions; expand Ubuntu's"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by MysticGold04 on 2009-01-25
I know this can be done, but Ubuntu's partition is currently in an "extended partition" /dev/sda4... will this pose an issue if trying to remove two ntfs partitions and make Ubuntu the only os on this machine?

Is there a utility that I can use to copy the Ubuntu partition to the front of the drive, and then expand that partition over the rest of the drive?? 
Does GParted support moving partitions? 

Thanks in advance!

---

### Post by caljohnsmith on 2009-01-25
How about first posting:
```
sudo fdisk -lu
```
And please identify all your partitions, including the ones you want to delete. That will give a better idea if what you want to do is feasible or not.

---

### Post by MysticGold04 on 2009-01-27
> **caljohnsmith said:**
> How about first posting:
```
sudo fdisk -lu
```
And please identify all your partitions, including the ones you want to delete. That will give a better idea if what you want to do is feasible or not.

Ok.. here's the output from fdisk:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92e4538c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    82750814    41375376    7  HPFS/NTFS
/dev/sda2        82750815   226548629    71898907+   7  HPFS/NTFS
/dev/sda3       226548630   312576704    43014037+   5  Extended
/dev/sda5       226548693   309588614    41519961   83  Linux
/dev/sda6       309588678   312576704     1494013+  82  Linux swap

I want to get rid of the two Windows partitions, and move the Linux partition to the top, then expand out the space, or possibly create a new /home partition to keep any data separate.  Thats why there are two NTFS partitions.  

What I would like to find out is if I can do this without having to re-install Ubuntu.  I suppose if I have to, its not a big deal, but it took a few hours to get it running with the eee kernel and such.

---

### Post by caljohnsmith on 2009-01-27
OK, from the Live CD, if you open gparted (System > Admin > Partition Editor), what you could do is delete sda1 and sda2, and then you could do a simple copy/paste of the Ubuntu sda5 partition into that newly created space using gparted. If that goes OK, after that you could mount the new Ubuntu partition to make sure everything is there as expected, and once you've confirmed that, you could delete/reformat the old sda5 Ubuntu partition. You could then use the space freed from sda5 as a data partition if you want; I would recommend just having a data partition rather than actually moving your entire home directory to that partition, but it's up to you. Also, when you first run gparted, it would be good to right-click the swap partition and select "swapoff", otherwise gparted may not allow you to make the changes you want to. Good luck and let me know how it goes.

---

### Post by MysticGold04 on 2009-01-27
Sounds good, I'll give it a try, however, I think that the data partition (only 40GB) will be too small so I might have to expand it some.  Also, I'll probably have to make changes to the Grub boot menu too I assume?  Thanks for the help!

---

### Post by caljohnsmith on 2009-01-27
> **MysticGold04 said:**
> Sounds good, I'll give it a try, however, I think that the data partition will be too small so I might have to expand it some.  Also, I'll probably have to make changes to the Grub boot menu too I assume?  Thanks for the help!
Yes, you'll need to reinstall Grub to the MBR (Master Boot Record), and if you are using a Ubuntu version prior to 8.10, you'll also need to modify the Grub menu (/boot/grub/menu.lst file). Once you are done with your repartitioning and the dust has settled, please post the output of:
```
sudo fdisk -lu
```
And identify your new partitions. We can work from there if you want.

---

### Post by MysticGold04 on 2009-01-28
successful output from fdisk now...

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92e4538c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    83039984    41519961   83  Linux
/dev/sda2        83039985    91297394     4128705   82  Linux swap / Solaris
/dev/sda3        91297395   312576704   110639655   83  Linux

now I just need to set the permissions on my /data directory that is now mounted on /dev/sda3. I also removed the Windows boot option from grub.  Funny thing is now is on boot up, I see the text as it boots... starting services, etc. Minor complaint though. It all works as it should.  Thanks a bunch for the help!! :)

---

### Post by ranch hand on 2009-01-28
If you look in you /boot/grub/menu.lst you will see something like this
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		26f31843-6d54-45e3-8363-1557ff117166
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26f31843-6d54-45e3-8363-1557ff117166 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```
It sounds to me like you are missing the "quiet" entry and thus all the text.
```

gksudo gedit /boot/grub/menu.lst

```
will let you edit that file.

---

### Post by caljohnsmith on 2009-01-28
> **MysticGold04 said:**
> Funny thing is now is on boot up, I see the text as it boots... starting services, etc. Minor complaint though. It all works as it should.  Thanks a bunch for the help!! :)
Did you also change the swap partition in any way? Because if you did, its UUID probably changed, and losing the Ubuntu splash screen on start up is a symptom of when the swap partition does not mount correctly at boot time. How about posting:
```

free
sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab

```
And we can see if that's maybe the issue. You could also check your menu.lst to make sure it has the "quiet" flags that Ranch Hand pointed out, because that would also cause the same behavior; but my guess would be your menu.lst is probably still OK.

---

### Post by MysticGold04 on 2009-01-28
> **ranch hand said:**
> If you look in you /boot/grub/menu.lst you will see something like this
```

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		26f31843-6d54-45e3-8363-1557ff117166
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=26f31843-6d54-45e3-8363-1557ff117166 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

```
It sounds to me like you are missing the "quiet" entry and thus all the text.
```

gksudo gedit /boot/grub/menu.lst

```
will let you edit that file.

Yep, checked on that when I went in to remove the Windows entries. The quiet switch(es) are still in place.

---

### Post by MysticGold04 on 2009-01-28
> **caljohnsmith said:**
> Did you also change the swap partition in any way? Because if you did, its UUID probably changed, and losing the Ubuntu splash screen on start up is a symptom of when the swap partition does not mount correctly at boot time. How about posting:
```

free
sudo blkid -c /dev/null
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab

```
And we can see if that's maybe the issue. You could also check your menu.lst to make sure it has the "quiet" flags that Ranch Hand pointed out, because that would also cause the same behavior; but my guess would be your menu.lst is probably still OK.

Yes, I moved it too, and also made it bigger. (2x the size of RAM installed) It also was not activating on boot, so I went into my /etc/fstab and manually specified the swap partition.  It mounts now, but I'm still getting the text on bootup.  Everything works normally it seems... I will check on your suggestions, John. Thanks :D

---

### Post by MysticGold04 on 2009-01-30
ok, heres the outputs:
```
  
total       used       free     shared    buffers     free:

cached
Mem:       2064440     462144    1602296          0       4604     121564
-/+ buffers/cache:     335976    1728464
Swap:      4128696      10272    4118424
______________________________________________________________________

sudo blkid -c /dev/null

/dev/sda1: UUID="ab3d8d37-b463-43c5-a2e2-bb1778d5a191" TYPE="ext3" 
/dev/sda2: UUID="0769da00-effb-493a-835a-8b38041719c8" TYPE="swap" 
/dev/sda3: UUID="835286a6-b005-4088-8a56-084805201c2a" TYPE="ext3" 
______________________________________________________________________
cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=2244a710-30e3-4a9d-a463-6376c9fc5580
______________________________________________________________________
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1	/               ext3    relatime,errors=remount-ro 0 	 1
/dev/sda2	 none           swap    sw              0       0
/dev/sda3	/data		ext3	defaults	0	2		
______________________________________________________________________

```

I see the issue with the resume, so I'll fix that to see if that is the issue, however, the swap is being used according to System Monitor.

---

### Post by caljohnsmith on 2009-01-30
Changing the resume file is unfortunately not enough; if you change the UUID in the resume file, you also have to regenerate all your /boot/initrd images, because they are all hard-coded with the UUID in the resume file. An easier approach I think is to simply change your swap partition UUID back to what it was before, i.e. what is listed in your resume file, and that should be enough to fix the issue. How about trying:
```
sudo swapoff -a
sudo mkswap -U 2244a710-30e3-4a9d-a463-6376c9fc5580 /dev/sda2
```
And of course the resume file needs to have that original UUID too, so if you all ready changed the resume file to the new swap UUID, I would change it back. Reboot, and if all goes well you should have your Ubuntu splash screen back. Let me know how that goes.

---

### Post by MysticGold04 on 2009-01-31
Yep, that worked. Thanks for your help John! :D

---

### Post by caljohnsmith on 2009-01-31
Glad to hear that worked OK; cheers and enjoy your Ubuntu install. :)

---

