---
title: "Server RAID &amp; LVM drive replacement"
date: 2014-03-06
forum: Hardware
---

### Post by p2bc on 2014-03-06
A few years ago I built a backup server with 4 Western Digital 2TB Greens (WD20EARS) in a LVM with two RAID1.

In the past year we went through a period of a series of power outage, consecutively. Inevitably a drive failed "/dev/sdc", Ubuntu worked great, shut down the drive and notified me.

I come to replace the drive '/dev/sdc' with a new WD 2TB Green (WD20EZRX). I pull out the third drive since it was 'sd_c_' and [Gigabyte GA-P43-ES3G]("http://www.gigabyte.com/products/product-page.aspx?pid=3484") was very specific from manual which order the drives slots should be filled in order, 1,2,3,4 which starts in the top right corner down three, and then top left corner down.

[ 4 ][ 1 ]
[ 5 ][ 2 ]
[ 6 ][ 3 ]

Seem like a no brainer, until I did just that, and I checked the bios. ??? (See Picture)
[ATTACH=CONFIG]250900[/ATTACH]

Did not take into consideration the whole Master/Slave configuration the motherboard does dynamically.
So I placed the drive in the third slot but now it is showing in the second position in the bios.

**So the question is:**
When Ubuntu states '/dev/sdc' where is it deriving the allocation of the drive letter. Is it based on the BIOS or some other criteria. Should I put the new drive in the second [ 2 ] slot so it shows up in the third position on the BIOS list, or does it matter because there is some other deciding factor.

I am sure this seems like a silly question, for me it does can't believe I have to ask, but the ramification can be dire. With the parity, if I don't proceed carefully, I could wipe a drive of information and still have a defective drive.


Thanks in advance for the help.

---

### Post by oldfred on 2014-03-06
It may depend on version of Ubuntu.
And it should depend on if you have a drive.map file.

I saw several versions ago that they stopped using drive.map with grub. So I guess they then just build a new one based on BIOS on each boot. But they said if you have a drive.map file it would be used.

The drive.map was somewhere in /boot or /boot grub, but I have since forgot.
And just checking now, I see a drivemap.mod file. But have never found a good resource on what every mod file does.

I have similar Gigabyte board and made a mistake of skipping port. I do not have RAID but several drives and boot drive is always hd0 in grub. But sda is always my first drive.
Then drives seem to be in port order, but because I skipped ports, if I plug in a flash drive it becomes sdb not my normal sdb drive. So I have to be careful on drive order.

---

### Post by Bashing-om on 2014-03-06
p2bc; Hello;

My 2 cents to add:
> 
The device.map file is located in /boot/grub/ It isn't required but can be used in Grub 2. The same command as Grub legacy: grub-mkdevicemap run as root.


I have not seen the effects of this in a LVM environment, but ->
You can determine what GRUB thinks your disk devices are by running:
sudo grub-mkdevicemap --device-map=device.map
cat /boot/grub/device.map

If things go north, I expect just deleting the file will put you back in place.

Also, UUIDs are the thing now-a-days to identify devices. Are you using UUIDs in your /etc/fstab control file ?

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by p2bc on 2014-03-06
I thought of trying by UUID, but since Ubuntu de-activated the drive, it won't mount it at all, so I can't get the UUID.

---

### Post by Bashing-om on 2014-03-06
p2bc; YUK,

I have no experience with LVM, on a production machine I am concerned that any advise I may give might worsen the situation.

There are those on the forum with extensive knowledge in this realm. ...
Uhmm, you might get a mod's attention and change the title of this thread to address server/LVM to gain their attention ?

[INDENT]down
[INDENT][INDENT]but not out
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-03-06
I can move it or change title if you want.

But LVM is not like some versions of RAID that will auto rebuild. 
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by p2bc on 2014-03-06
Ok, I removed the new drive and re-installed the old drive, and managed to boot it with a degraded RAID. Which at least gave me access to the /dev.

```

bs-admin@Backup-Server:~$ sudo cat /proc/mdstat
[sudo] password for bs-admin: 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda1[0]
      1953382208 blocks super 1.2 [2/2] [UU]
      [=====>...............]  resync = 28.0% (547921536/1953382208) finish=223.8min speed=104652K/sec
      
md1 : active raid1 sdd1[1]
      1953382208 blocks super 1.2 [2/1] [_U]

```

```

bs-admin@Backup-Server:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               system-home
  PV Size               1.82 TiB / not usable 3.81 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476899
  Free PE               0
  Allocated PE          476899
  PV UUID               dfZCVm-yc3X-CSKN-Qqpx-50sf-jrLI-FtXI3n
   
  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               system-home
  PV Size               1.82 TiB / not usable 3.81 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476899
  Free PE               0
  Allocated PE          476899
  PV UUID               kg66fF-IO5X-WmrJ-I3b2-PbY3-CNzg-kclVr5

```

```

bs-admin@Backup-Server:~$ sudo blkid
/dev/sda1: UUID="468f5351-6782-29dd-38fd-97c0c648c373" UUID_SUB="82827e2c-9bd9-d400-3860-09c7d8265903" LABEL="Backup-Server:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="4c1a27b4-42ef-c229-2cfb-c69904d88492" UUID_SUB="995e6376-6ec1-7275-e446-11925cd55937" LABEL="Backup-Server:1" TYPE="linux_raid_member"    <===== Same ???
/dev/sdd1: UUID="4c1a27b4-42ef-c229-2cfb-c69904d88492" UUID_SUB="759f9c8e-2d30-c497-386c-9fa5a34d1f7d" LABEL="Backup-Server:1" TYPE="linux_raid_member"    <===== Same ???
/dev/sdb1: UUID="468f5351-6782-29dd-38fd-97c0c648c373" UUID_SUB="d2d5645e-0e99-1f40-93d6-5fc115a6ab68" LABEL="Backup-Server:0" TYPE="linux_raid_member" 
/dev/md1: UUID="kg66fF-IO5X-WmrJ-I3b2-PbY3-CNzg-kclVr5" TYPE="LVM2_member" 
/dev/md0: UUID="dfZCVm-yc3X-CSKN-Qqpx-50sf-jrLI-FtXI3n" TYPE="LVM2_member" 
/dev/mapper/system--home-lv--home: UUID="033f5194-484a-4f89-ae24-a8dc51767382" TYPE="ext4" 
/dev/sdf1: UUID="b103c874-e00a-4322-9988-c2e1caa419fc" TYPE="swap" 
/dev/sde1: UUID="0337f9c4-e38d-4bef-a39a-143735bfcb7f" TYPE="ext4" 
/dev/sde2: UUID="d5ce1492-38fa-47be-812c-bb1f21508ba7" TYPE="ext4"

```

Why would /dev/sdc1 and /dev/sdd1 have the same UUID, and how does these help with the drive itself /dev/sdc and not the partition on the drive /dev/sdc1

```

bs-admin@Backup-Server:~$ ls -l /dev/disk/by-uuid/
lrwxrwxrwx 1 root root 10 Mar  6 17:18 0337f9c4-e38d-4bef-a39a-143735bfcb7f -> ../../sde1
lrwxrwxrwx 1 root root 10 Mar  6 17:18 033f5194-484a-4f89-ae24-a8dc51767382 -> ../../dm-0
lrwxrwxrwx 1 root root 10 Mar  6 17:18 b103c874-e00a-4322-9988-c2e1caa419fc -> ../../sdf1
lrwxrwxrwx 1 root root 10 Mar  6 17:18 d5ce1492-38fa-47be-812c-bb1f21508ba7 -> ../../sde2

```

```

bs-admin@Backup-Server:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 Mar  6 17:18 ata-HL-DT-ST_DVDRAM_GSA-4163B_K0C53JK2145 -> ../../sr0
lrwxrwxrwx 1 root root  9 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5693418 -> ../../sdc
lrwxrwxrwx 1 root root 10 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5693418-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5701675 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5701675-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5714473 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5714473-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5741587 -> ../../sdd
lrwxrwxrwx 1 root root 10 Mar  6 17:18 ata-WDC_WD20EARS-00MVWB0_WD-WCAZA5741587-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 10 Mar  6 17:18 dm-name-system--home-lv--home -> ../../dm-0
lrwxrwxrwx 1 root root 10 Mar  6 17:18 dm-uuid-LVM-ebcRXP3oyVYD05vs2e8PXv2v4ZvDVhcE8TSGDIbQFEGHudYL9J87KXCtNE1CRWYh -> ../../dm-0
lrwxrwxrwx 1 root root  9 Mar  6 17:18 md-name-BOD-Server:0 -> ../../md0
lrwxrwxrwx 1 root root  9 Mar  6 17:18 md-name-BOD-Server:1 -> ../../md1
lrwxrwxrwx 1 root root  9 Mar  6 17:18 md-uuid-468f5351:678229dd:38fd97c0:c648c373 -> ../../md0
lrwxrwxrwx 1 root root  9 Mar  6 17:18 md-uuid-4c1a27b4:42efc229:2cfbc699:04d88492 -> ../../md1
...
lrwxrwxrwx 1 root root  9 Mar  6 17:18 wwn-0x50014ee205ab4581 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  6 17:18 wwn-0x50014ee205ab4581-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Mar  6 17:18 wwn-0x50014ee25b008270 -> ../../sdd
lrwxrwxrwx 1 root root 10 Mar  6 17:18 wwn-0x50014ee25b008270-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Mar  6 17:18 wwn-0x50014ee25b00829c -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar  6 17:18 wwn-0x50014ee25b00829c-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Mar  6 17:18 wwn-0x50014ee25b0082d8 -> ../../sdc
lrwxrwxrwx 1 root root 10 Mar  6 17:18 wwn-0x50014ee25b0082d8-part1 -> ../../sdc1

```

Seems like impressive information, but I don't feel like I am any further ahead.

---

### Post by p2bc on 2014-03-06
As for changing title/moving the thread, I have no prefference. More eyes on the problems would be appreciated.

---

### Post by Yellow Pasque on 2014-03-06
To find out the failed drive (assuming failed drive is sdc), run:
```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sdc | grep -i serial
```
Look at the serial number and write it down. Then you can open the case and find the defective one by looking at the serial number on the label.

> Why would /dev/sdc1 and /dev/sdd1 have the same UUID
Because they're mirrored? sda and sdb have the same UUID as well.

---

### Post by p2bc on 2014-03-06
<deleted>

---

### Post by p2bc on 2014-03-06
```

bs-admin@Backup-Server:~$ sudo smartctl -a /dev/sdc | grep -i serial
Serial Number:    WD-WCAZA5693418

```

Is this SN the same as the one that would be printed on the actual drive?

[quote=Temüjin]
To find out the failed drive (assuming failed drive is sdc)
[/quote]

It is sdc, because is the active drive listed in the /proc/mdstat obmits it. under md1
```

md0 : active raid1 sdb1[1] sda1[0]
      1953382208 blocks super 1.2 [2/2] [UU]
      [=====>...............]  resync = 28.0% (547921536/1953382208) finish=223.8min speed=104652K/sec
      
md1 : active raid1 sdd1[1]
      1953382208 blocks super 1.2 [2/1] [_U]

```


[quote=Temüjin]
Because they're mirrored? sda and sdb have the same UUID as well.
[/quote]
 I did not notice that, thank you.

---

### Post by Yellow Pasque on 2014-03-06
> **p2bc said:**
> Is this SN the same as the one that would be printed on the actual drive?
It should be, unless someone has tampered with the drive.

---

### Post by oldfred on 2014-03-06
Changed title to Server RAID & LVM drive replacement

---

### Post by p2bc on 2014-03-07
The 'sudo smartctl -a /dev/sdc | grep -i serial' results worked perfectly.

I was able to take out and verify the serial numbers on the actual drives against the 'smartctl' results, and found the right one within seconds.
Not to mention confidence. So thank you so much.

It also gave me a new tool for my toolbox, which always good.


I will be glad to make this thread as "Solved".



Not to highjack my own thread, more on a side note. I did 'smartctl -a /dev/sdc' without the grep to see the full results, and it was interesting.
It came back, with 'No Errors Logged'. With no errors to speak of at all according to it. Which leads me to wonder what caused the system to label
the drive as deffective. That is obviously another command, and I will leave it to another thread, that I might write someday, just make me go "hmmmm" :D

As for this thread, it solved!!!\\:D/

---

