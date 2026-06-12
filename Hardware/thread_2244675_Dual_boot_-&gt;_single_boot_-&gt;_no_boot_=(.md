---
title: "Dual boot -&gt; single boot -&gt; no boot =("
date: 2014-09-18
forum: Hardware
---

### Post by galen666 on 2014-09-18
I had to reinstall Windows onto a dual boot system and afterward Grub quit working. I guess this is expected. The system began booting directly into Windows. Previously it was using Grub.

I tried repairing this with boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but it resulted in a system that won't boot at all. I think it is due to a RAID configuration that I've messed up. The boot repair disk can probably repair it but I don't know what disk and partition to use for the MBR.

The boot repair disk provides config at [http://paste.ubuntu.com/8369567/](http://paste.ubuntu.com/8369567/) 

I'm just not used to working on dual boot and not sure what to do next. Any advice is welcome.

---

### Post by galen666 on 2014-09-18
By default, boot repair wants to repair sdb1. I know my working Windows partition is /dev/sdb3 and it looks like the grub entry wants to boot Linux from \dev\sdc2.

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048       489,471       487,424  83 Linux
/dev/sdc2             489,472   156,739,583   156,250,112   5 Extended
/dev/sdc5             491,520   148,547,583   148,056,064  fd Linux raid autodetect
/dev/sdc6         148,549,632   156,739,583     8,189,952  fd Linux raid autodetect
/dev/sdc3    *    156,739,584   489,631,743   332,892,160   7 NTFS / exFAT / HPFS

"menuentry 'Ubuntu 14.04 LTS (14.04) (on /dev/sdc2)'"

I think I need to choose advanced options in the boot repair disk and select: 
restore MBR of sdc
partition booted by MBR: sdc1

---

### Post by galen666 on 2014-09-18
[http://paste.ubuntu.com/8370262](http://paste.ubuntu.com/8370262)

No operating system present again..

---

### Post by galen666 on 2014-09-18
OK somehow it worked to repair /dev/sdc and set /dev/sdc3 as the partition that is booted. 
I basically this gets me back to where I was before, booting directly into Windows without Grub, but it's better than no operating system.

---

### Post by yancek on 2014-09-18
> "menuentry 'Ubuntu 14.04 LTS (14.04) (on /dev/sdc2)'"

If you look at your fdisk output just above this line, you can see that sdc2 is marked as an "Extended" partition.  An Extended partition does not contain any data so that won't work.
That same fdisk output shows sdc3 as a windows partition marked as active so windows can boot it.  I'm guessing sdc1 would be a boot partition but I'm also curious as to what happened to sda and sdb?

---

### Post by oldfred on 2014-09-18
You have both a /boot for Ubuntu and Windows outside of the RAID, but your install of Ubuntu inside of the RAID.
And the UUID that the boot stanza shows for the / (root) does not exist. The boot partition UUID looks correct.

Windows does not correctly see Linux partitions, so reinstalling it may have corrupted or changed partition tables. Often better to keep Windows on its own drive to avoid issues, if you have an available drive.

It also looks like your Windows install in sdb3 & sdb4 is the working install. You should have boot flag on either sdb3 or possibly sdb4 as both show boot files. Your Windows in sdc3 is missing a BCD which is required to boot.

This looks like it mounts /boot correctly either by set root or searching for correct UUID.
 
>  set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  feb9fc89-05cd-427b-8aba-2ee6bd3cbb76
else
  search --no-floppy --fs-uuid --set=root feb9fc89-05cd-427b-8aba-2ee6bd3cbb76
fi

    
 
But this UUID does not exist inside your RAID and I am not familar with your boot parameters. Is this a special version of Linux?
linux	/vmlinuz-3.13.0-24-generic root=UUID=74cc2a92-5ef2-4780-8b3c-05004919065a ro  nomdmonddf nomdmonisw nomdmonddf nomdmonisw

---

