---
title: "How to activate and then verify automatic TRIM on a SSD for Ubuntu 12.04 Precise"
date: 2013-01-20
forum: Hardware
---

### Post by yeehi on 2013-01-20
I have looked around and haven't found a single site providing all the following information:

1) Whether a drive is automatically recognized as a SSD during installation of Ubuntu (12.04, 12.10, 13.04 Precise Pangolin, Quantal Quetzal, Raring), consequently not automatically creating a swap partition (is swap needed?) 

3) Whether or not to proceed with the "overwrite data on partition" option on a SSD during an installation

4) Whether partitions are automatically correctly aligned for a SSD during installation for these releases

5) Whether TRIM is automatically enabled 

6) How to activate automatic TRIM, if it doesn't occur during installation

7) What to do if the drive is using encrypted partitions / LVM

8) How to verify that TRIM is occurring automatically on both BtrFS and ext4 file systems

9) Whether there is a nice package in the repositories which does "everything" for your Solid State Drive

I would be very grateful if somebody could help with this information.

Thank you! :)

EDIT:

I found a useful, no **truly excellent** site [here]("https://sites.google.com/site/easylinuxtipsproject/ssd"), but it would still be nice to get some answers to the points above.

---

### Post by sudodus on 2013-01-20
I can start helping you (but I don't have answers to all questions).

> **yeehi said:**
> 
4) Whether partitions are automatically correctly aligned for a SSD during installation for these releases

I think so
> 
4) Whether TRIM is automatically enabled 

No
> 
5) How to activate automatic TRIM, if it doesn't occur during installation

Add the option [FONT="Courier New"][SIZE="3"]discard[/SIZE][/FONT] to the line for the SSD drive in /etc/fstab
example:
```
UUID=3d28b4a7-46af-43bd-92fc-030c21ef98c7 /               ext4    defaults,discard,noatime,errors=remount-ro 0       1
```
Edit: yes, haqking, I changed it here an in my fstab: ext4

---

### Post by sudodus on 2013-01-20
Read also this link

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2100088&highlight=discard+trim[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2100088&highlight=discard+trim")

---

### Post by oldfred on 2013-01-20
For the last couple of years partitions have been aligned correctly.  First partition starts at 2048 and every partition should have a start sector that can be divided by 8.
       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?tit](http://ubuntuforums.org/showthread.php?tit)'s 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

     
If you have data on SSD have you backed it up, otherwise why would you want to overwrite it?

       HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)

    
        trim does need ahci in BIOS
kernel version >=2.6.33. It does not work with ext3; (10.04 was 2.6.32)

    
I did not enable trim right away so I ran this:
       fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

    
       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by haqking on 2013-01-20
> **sudodus said:**
> I can start helping you (but I don't have answers to all questions).


I think so

No

Add the option [FONT=Courier New][SIZE=3]discard[/SIZE][/FONT] to the line for the SSD drive in /etc/fstab
example:
```
UUID=3d28b4a7-46af-43bd-92fc-030c21ef98c7 /               ext3    defaults,discard,noatime,errors=remount-ro 0       1
```

I am pretty sure that ext3 does not support TRIM (discard)

```
man mount
``` confirms this.

but i might be wrong, it has been a while since i used ext3

---

### Post by Hreinsi on 2013-01-20
this shows it all.

[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html#more](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html#more)

---

### Post by haqking on 2013-01-20
> **Hreinsi said:**
> this shows it all.

[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html#more](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html#more)

Ahh yes I thought so.

Thanks for the link

Peace

---

### Post by yeehi on 2013-01-20
1) 
I read that the discard option is *not* the best one for a SSD. (I linked to the page that explains why at the top of this thread.) Setting trim by rc.local is preferred for setting TRIM. (It happens at boot, which is ok if you regularly reboot.)

2)
Does TRIM on a BtrFS partition (on a SSD) require special settings?

3) 
Very nice to see you on ubtuntu forums again, haqking. You are most knowledgeable. I thought you had abandoned this place.

---

### Post by sudodus on 2013-01-21
> **haqking said:**
> I am pretty sure that ext3 does not support TRIM (discard)

```
man mount
``` confirms this.

but i might be wrong, it has been a while since i used ext3

Thanks at lot for finding that!

It is an ext4 partition, but the ext3 entry is inherited via an upgraded system (Ubuntu 8.04 -- 10.04 -- 12.04). You bet I was quick to correct it in fstab ;-)

---

### Post by roten on 2013-01-21
Hi,

Several of you know a lot about trim for SSD drives. I just started this thread and need help.

[http://ubuntuforums.org/showthread.php?p=12466039#post12466039](http://ubuntuforums.org/showthread.php?p=12466039#post12466039)

Thanks in advance  :P

---

### Post by sudodus on 2013-01-21
Focusing on roten's questions:

> sudo fstrim -v /
With discard enabled it did nothing. Without discard enabled it reported
Code:
/mnt: 19918028800 bytes were trimmed
- Do you think that discard works also on this drive?
- Do you think that fstrim works on this drive?

I guess fstrim works (I, too, tested on a drive, that is not zeroized), and it could trim various amounts depending on how much was written and deleted).

> - What do you recommend?
. discard or
. cron job with fstrim

Given the feedback from fstrim, it sound more likely to work. But I leave it to the gurus ...

---

### Post by sudodus on 2013-01-21
I found this link

[http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/](http://www.buildingcubes.com/2012/10/10/ssd-trim-command-on-linux/)

which claims fstrim works on ext2 and ext3, but will trim the whole unused space trimmed or not trimmed.

---

### Post by loyhz2ayj-jeff on 2013-12-27
I have read (at [http://blog.neutrino.es/2013/howto-properly-activate-trim-for-your-ssd-on-linux-fstrim-lvm-and-dmcrypt/](http://blog.neutrino.es/2013/howto-properly-activate-trim-for-your-ssd-on-linux-fstrim-lvm-and-dmcrypt/)) (see also [http://askubuntu.com/questions/191914/how-should-i-configure-trim-support-for-lvm-logical-volumes/191945#191945](http://askubuntu.com/questions/191914/how-should-i-configure-trim-support-for-lvm-logical-volumes/191945#191945)) that lvm 2.02.66 that ships with 12.04 LTS does not support TRIM.  

And there is no way to upgrade LVM except installing Ubuntu 13 (which you have already done).   Are we stuck until 14 LTS comes out unless we want to run 13 for 9 months?

---

