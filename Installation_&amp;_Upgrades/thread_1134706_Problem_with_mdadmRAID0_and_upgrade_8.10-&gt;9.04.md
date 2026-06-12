---
title: "Problem with mdadm/RAID0 and upgrade 8.10-&gt;9.04"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by jalder on 2009-04-23
I've been using Ubuntu and mdadm for a while now, and it seems like each time I do a dist upgrade something goes wrong with my raid. I have four disks in my box, 2x250Gb SCSI and 2x750Gb SATA. The SCSI disks are raid1 and are formated with LVM/ext3 as the root drive. The two SATA disks are raid0 and ex3 (no LVM). In 8.10 I had /dev/md0 (SCSI) and /dev/md1 (SATA) and life was good. When I rebooted after the 9.04 upgrade, I got dropped to a shell because my raid0 disks didn't mount. Turns out that it is now called /dev/md_d1 and does not show up in /dev/disk/by-uuid. Since I don't have a proper UUID for md_d1 I can't put it in my fstab to mount on boot. Luckily, I can mount it by hand to prove the array and data are still ok (which is good because there is about 700Gb of data on it).

So my questions for people whom know mdadm better than I are:
Why is it called /dev/md_d1 now?
Why is there no UUID in /dev/disk/by-uuid?
How can I mount this at boot?

Here are my obligatory logs:

```
jalder@jalder:~$ sudo fdisk -l 

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000180dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91201   732572001   83  Linux

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e406f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Disk /dev/sdc: 300.0 GB, 300000000000 bytes
255 heads, 63 sectors/track, 36472 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053e00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36472   292961308+  fd  Linux raid autodetect

Disk /dev/sdd: 300.0 GB, 300000000000 bytes
255 heads, 63 sectors/track, 36472 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00059cf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       36472   292961308+  fd  Linux raid autodetect

Disk /dev/md0: 299.9 GB, 299992285184 bytes
2 heads, 4 sectors/track, 73240304 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md_d1: 1500.3 GB, 1500307259392 bytes
2 heads, 4 sectors/track, 366285952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md_d1 doesn't contain a valid partition table
```

I was a little worried about the no valid partition table thing, but my /dev/md0 also has the error and works fine (although it is also LVM).

```
jalder@jalder:~$ sudo mdadm -D /dev/md_d1
/dev/md_d1:
        Version : 00.90
  Creation Time : Thu Sep 18 11:39:15 2008
     Raid Level : raid0
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Oct  3 10:57:04 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 35dbfb25:ee628a58:91a192f7:9de6166b (local to host jalder)
         Events : 0.5

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
```

```
jalder@jalder:~$ ls -la /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 100 2009-04-23 17:51 .
drwxr-xr-x 5 root root 100 2009-04-23 17:51 ..
lrwxrwxrwx 1 root root  20 2009-04-23 17:51 a4748270-6c28-48e8-932b-a1878a8f3c12 -> ../../mapper/vg-root
lrwxrwxrwx 1 root root  20 2009-04-23 17:51 ec17344a-feac-4741-a9f4-4fb605fc9802 -> ../../mapper/vg-swap
lrwxrwxrwx 1 root root  20 2009-04-23 17:51 ed22033d-bbd7-451f-b1c1-92dd59fd357e -> ../../mapper/vg-boot
```

Thank you to anyone who might be able to help.

---

### Post by stefsybo on 2009-04-24
I have the same problem. My home server has a RAID1 of two SATA disks which was known as /dev/md0 in Intrepid and mounted by its UUID. I just upgraded to Jaunty and it dropped to a maintenance shell at boot.

In /proc/mdstat there is an inactive RAID device called /dev/md_d0 containing one of the drives from the RAID array, like this:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdb2[0](S)
      621225408 blocks
       
unused devices: <none>
```
When I stop this array and run mdadm --assemble --scan, /dev/md0 is assembled as it was before the upgrade and when I resume the boot process it is mounted using the array's UUID as it should be. /proc/mdstat now contains these contents:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb2[0] sdc2[1]
      621225408 blocks [2/2] [UU]
      
unused devices: <none>
```
How can I make sure this array is assembled and mounted at boot without intervention?

---

### Post by voxed on 2009-04-24
I've got the same problem aswell. From what i can work out, it has to do with kernel block device partition checking, which was altered in the 2.6.28 kernel. Haven't found a decent work-around for it yet.

---

### Post by Diskdoc on 2009-04-24
This was certainly scary to read! I have a server with two RAID1:s and was planning to upgrade today! Wouldn't want any trouble..

Found this bug: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298)

Can anyone confirm upgrading from 8.10 to 9.04 works when you have RAID0 or RAID1?

/ Carl

---

### Post by voxed on 2009-04-24
> **Diskdoc said:**
> This was certainly scary to read! I have a server with two RAID1:s and was planning to upgrade today! Wouldn't want any trouble..

Found this bug: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298)

Can anyone confirm upgrading from 8.10 to 9.04 works when you have RAID0 or RAID1?

/ Carl

The work-around suggested in the bug req does work, but you can only apply it after you dist-upgrade.

---

### Post by stefsybo on 2009-04-24
The workaround suggested in that bug report works indeed, thanks.

---

### Post by jalder on 2009-04-24
Thanks all, the fix in the bug report worked for me also. I didn't have an entry for /dev/md1 in my /etc/mdadm/mdadm.conf. It worked ok in 8.10 without the entry, but I needed to add it for 9.04.

```
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=35dbfb25:ee628a58:91a192f7:9de6166b
```

Once I added that, I could uncomment the line from my /etc/fstab and my raid0 (/dev/md1 now rather than /dev/md_d1) now mounts at boot.

Thanks for all your help

---

### Post by j_araquistain on 2009-04-24
I think that I'm having a similar problem, but the workaround isn't fixing it.

When I power on it fails to boot my fake RAID 0 and drops me into an (initramfs) shell.

I tried doing:
```
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

and it says
```
/bin/sh: cannot create /etc/mdadm/mdadm.conf: nonexistent directory
/bin/sh: mdadm: not found
```

Is there something obvious I'm missing?

---

### Post by stefsybo on 2009-04-24
I think you do not have mdadm installed, run *sudo apt-get install mdadm* to get it.

---

### Post by j_araquistain on 2009-04-24
I can't do apt-get either, it can't find the command. I think its maybe because I'm in the (initramfs) shell and not a regular one.

If there's a way to boot to a recovery shell or any regular shell given that it won't recognize my RAID I'm not aware of it. But then again, I'm pretty new to all this so it could be really easy.

Here is exactly what it says when I try to boot into recovery mode from GRUB:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  -Ceck rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/nvidia_bbbbbffe2 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

---

### Post by jalder on 2009-04-24
j_araquistain: is your root partition on the raid device that isn't starting? Luckily, the raid that wasn't working for me was just a place to store data, not the OS, so I got dropped into a regular shell. I am no good with BusyBox. Firing up a LiveCD might be worth a shot. Its funny that Ubuntu is all about the "One time install" but I often find myself downloading the LiveCD to deal with upgrade issues.

---

### Post by j_araquistain on 2009-04-24
Yeah, my root partition is on the RAID.

I figured I might have to use the Live CD to try and fix it, the problem is I don't really have any idea how.

I know this is a super stupid question but if I boot using the live cd what do I have to do so that whatever I do in the terminal affects my drives, rather than whatever is on the cd i.e. could I use the cd to run the command suggested by the workaround?

---

### Post by jalder on 2009-04-24
Things get pretty sticky when the root partition is software raid. A lot of places say just don't do it. Of course I did anyway and luckily haven't had any problems (or I did a long time ago a just forgot how I fixed them). I am a little rusty on this, but you may need the Alternative CD. I don't think mdadm comes in the regular one (or at least it wasn't on 8.10). As I understand it, you should be able to load the LiveCD, thinker with the raid using mdadm, mount the raid and edit your mdadm.conf. Hopefully, if that gets squared away you can reboot without the disk and everything will automagically work. 

Sorry if this is a little vague, but as I said, its tricky when the root partition is raided. Maybe someone who knows better can give more advise.

---

### Post by j_araquistain on 2009-04-24
You know what, I think I'm just going to use the alternate CD to do a fresh re-install.

I have all my files backed up on an external drive so all I'd have to do is re-install some programs which isn't a big deal.

And when I have time I'll get another hard drive so I can have the root partition on a non-RAID hard drive and avoid this problem again.

---

### Post by Diskdoc on 2009-04-24
I'd use System Rescue CD for this. [http://www.sysresccd.org/](http://www.sysresccd.org/)

You should be able to get your RAID:s running, edit the files you want and chroot into your root partition if needed.

---

### Post by j_araquistain on 2009-04-24
can I chroot into the root partition if the root partition is on the RAID that can't be read?

I'm really at a loss, I don't know know what files I would edit even if I wanted to.

---

### Post by Diskdoc on 2009-04-25
Yeah, I feel sorry for you having to go through this. If the problem really is only mdadm.conf being overwritten I feel someone should have caught this before release. Software RAID is an offical feature on the alternative install CD, I think.

However, I think you will be able to access your root, even if it is on a RAID. Lots for you to learn here about how to do it.. I don't remember everything exactly from memory so I'll sketch up the process for you. I might have to do the exact same thing here this weekend (our server has two RAID1:s of which one is / and the other is /home) so I might return with more details unless someone else beats me to it.

1) Boot the System Rescue CD
2) Start the relevant RAIDs (Using mdadm? Maybe started automatically?)
3) Mount the root file system on the RAID at for example /mnt/raidroot after first creating the mountpoint.
4) Edit the necessary file (/mnt/raidroot/etc/mdadm.conf I think?)
5) Unmount /mnt/raidroot
6) Reboot and see what happens

Roughly, as I said. The instructions for re-creating mdadm.conf might require you to chroot into the root filesystem in which case I THINK you change the process above with something like:

3.1) mount -o bind /dev /mnt/raidroot/dev
3.2) mount -t proc none /mnt/raidroot/proc
3.3) chroot /mnt/raidroot /bin/bash
4) Do the mdadm automatic mdadm.conf-thing people had success with in this thread.

Really, I've done stuff like this a few times but I forget a lot :-p Hopefully someone else will help us on this..

---

### Post by ironlung on 2009-04-26
Had the same problem. Workaround worked for me as well. Thanks!

---

### Post by icephoenix on 2009-04-26
Make sure you're loading a proper kernel. I also have all partitions on RAID and upgrade failed to update my grub to load up the proper kernel. 

uname -a in your shell and see if loaded kernel is NOT 2.6.28 then you're loading wrong kernel.

If that's the case boot up from rescue cd( [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) )
Reassamble your raid array that holds your boot partition, something like this:

mdadm --assemble /dev/md1 /dev/sda1 /dev/sdb1 
etc. ( you need to know how your array is built, you may need to run mdadm --examine or something like that if you don't know)

after array is assambled mount it:

mkdir /mnt/raid
mount /dev/md1 /mnt/raid

then edit your /mnt/raid/menu/grub.lst
or whatever and update it to load the proper kernel, restart :)

That's what was wrong with my system and I got the same error message, so I hope this helps.

Good luck!

---

### Post by dspohn23 on 2009-04-26
> **jalder said:**
> j_araquistain: is your root partition on the raid device that isn't starting? Luckily, the raid that wasn't working for me was just a place to store data, not the OS, so I got dropped into a regular shell. I am no good with BusyBox. Firing up a LiveCD might be worth a shot. Its funny that Ubuntu is all about the "One time install" but I often find myself downloading the LiveCD to deal with upgrade issues.

Just an FYI. I just found out that mdadm can be used in BusyBox, just have to use the full path: /sbin/mdadm

---

### Post by dibuntux on 2009-04-27
Hi everybody, this seems like a nightmare! I would like to upgrade from 8.10 to 9.04 but my system is entirely on RAID 1, with md0 as root, md1 as swap and md2 as home plus a RAID0 on md3...
The prospective to finding myself in a busybox and asking for help on a forum is really scaring.

The tenth release of Ubuntu and we are at this point?

Is there a solution?

Thanks in advance for your help

---

### Post by mharpe2 on 2009-04-28
I am having a simular problem.

I also upgraded from 8.10 to 9.04 and was kicked into a console on first boot of the upgraded system.  I chose to degrade the raid array to continue to boot.

I tried the fix posted on the first page but still have the same result.
>   It appears the problem may have been caused by /etc/mdadm/mdadm.conf being silently overwritten by a default config file. After executing the following mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf in a recovery shell, the array mounts just fine.I have tried physically unpluging each drive to see if files created after the degrade exist on both drives -they do.

here are the logs:
**FDISK**
```

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfb0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60428   485387878+  fd  Linux raid autodetect
/dev/sda2           60429       60801     2996122+   5  Extended
/dev/sda5           60429       60801     2996091   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfb0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60428   485387878+  fd  Linux raid autodetect
/dev/sdb2           60429       60801     2996122+  fd  Linux raid autodetect

Disk /dev/md0: 497.0 GB, 497037082624 bytes
2 heads, 4 sectors/track, 121346944 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 3067 MB, 3067871232 bytes
2 heads, 4 sectors/track, 748992 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000


```[B]/proc/mdstat   notice the _U, and the weird drive names and degraded status

[/B]```

cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 dm-2[1]
      2995968 blocks [2/1] [_U]
      
md0 : active raid1 dm-1[1]
      485387776 blocks [2/1] [_U]
      
unused devices: <none>

sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Dec 31 19:08:16 2008
     Raid Level : raid1
     Array Size : 485387776 (462.90 GiB 497.04 GB)
  Used Dev Size : 485387776 (462.90 GiB 497.04 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 28 21:17:21 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : b2feb7a5:99833b7d:c50b4455:be485a3f
         Events : 0.47948

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        1        1      active sync   /dev/block/252:1

 sudo mdadm -D /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Wed Dec 31 19:08:29 2008
     Raid Level : raid1
     Array Size : 2995968 (2.86 GiB 3.07 GB)
  Used Dev Size : 2995968 (2.86 GiB 3.07 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Apr 28 21:17:17 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9d8e3e66:cbe4ff30:626d1941:768f80f4
         Events : 0.1610

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        2        1      active sync   /dev/block/252:2



```here is the parted output
```

(parted) print all                                                        
Model: ATA WDC WD5000AACS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags     
 1      32.3kB  497GB  497GB   primary   ext3         boot, raid
 2      497GB   500GB  3068MB  extended                         
 5      497GB   500GB  3068MB  logical                raid      


Model: ATA WDC WD5000AACS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags     
 1      32.3kB  497GB  497GB   primary  ext3         boot, raid
 2      497GB   500GB  3068MB  primary  linux-swap   raid      


Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/via_chbjibdgid: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags     
 1      32.3kB  497GB  497GB   primary  ext3         boot, raid
 2      497GB   500GB  3068MB  primary  linux-swap   raid     

```


thanks for any help

---

### Post by agibby5 on 2009-05-03
I just did this:
```
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

...and the array mounted on reboot.  This post saved my day!

---

### Post by dibuntux on 2009-05-07
Thank you for providing a solution - I printed the page and started to update from 8.10 to 9.04 on AMD64 with /, /home and swap on md0, md1 & md2 on RAID1, plus a RAID0 on md3 using two spare partitions on my 2 SATA disks.

But... The upgrade just went as smooth as silk! The system booted just fine. For now I just had to reconfigure VMWare server 2.

Not so for md3, the RAID0. Raid monitor says md_d3 (instead of calling it md3): inactive sdb4[0](S)

Any help? TIA

---

### Post by dspohn23 on 2009-05-17
Hope this help others.... My root partition is on a raid 1 partition. Once I upgraded to 9.04 the computer kept dropping into busybox during boot. I was able to continue booting using the above suggestions by calling mdadm from busybox (using: /sbin/mdadm). However, every time I restarted the computer I would drop into busybox and would have to run the same commands to continue booting... After a few weeks I was tired of this and was trying different things to get mdadm to assemble my arrays automatically at boot.

I found that by not using acpi, the arrays assembled successfully at boot. I did this by editing grub config file. [http://ubuntuforums.org/showthread.php?t=398948](http://ubuntuforums.org/showthread.php?t=398948)

Good Luck!

---

### Post by toshko3 on 2010-01-22
Hi, from my experience, after upgrading two of three md devices were renamed to md_d1 and md_d2. The md0 stood still. Turns out that in this kernel the raid autodetect function is not working any more (from what I read). This is because it can cause problems in more complicated environment and this function is left to /etc/mdadm.conf. After configuring the mdadm.conf file correctly all works just fine. In my case - raid1 and the mdadm.conf file looks like this:
```
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=423a6272:703e4a30:913c5897:31a85d06
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=07db1c33:5f542382:913c5897:31a85d06
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=238bedb9:81c82c3b:ab7016b1:7c803cea

```
Before my editing with "mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf" the file only had this line for definition:
```
ARRAY /dev/md0 metadata=0.90 level=raid1 num-devices=2 UUID=238bedb9:81c82c3b:ab7016b1:7c803cea

```
I suppose this is why only the md0 device worked right after the upgrade.
Hope I was helpful for anybody. :popcorn:

---

