---
title: "Cloning a NAS hard drive with OS"
date: 2023-01-12
forum: Hardware
---

### Post by michael351 on 2023-01-12
I have a WD My Cloud NAS drive system which I use for both backup and to  serve music files throughout my home. The drive is used mostly with my Ubuntu HTPC.
Recently, I noticed bad sectors  cropping up and so it's time to replace the hard drive with a new one.

Because it is a combination server (has an OS on the drive) as well as  storage, I intend to clone it (Clonezilla) onto a new drive and replace/boot up.

The old drive is a WD Red 4TB 5400 rpm. I'd like to increase the size to 6TB and  use a different brand (HGST) with a speed of 7200 RPM. I know I can increase the partition after  the clone (gparted), but wonder if the different brand and speed will cause an issue with  WD's NAS firmware which is the basis of the OS used in the NAS.

Thanks in advance to anyone who has done this.

---

### Post by TheFu on 2023-01-12
The last few years, WD has been less than nice towards mixing and matching hardware.  This is common with all NAS vendors. By limiting the hardware, they prevent potential issues. Only someone with the exact same setup as yours will be able to comment with any authority.

In short, google what others with the exact same hardware have done.  Also, check for WD firmware updates.
If you aren't already familiar with Clonezilla, perhaps using 'ddrescue' or even 'cp' on the correct source-->target drive device files would be easier? If you are unfamiliar with whole drive device naming under Linux, please ask for  Then just resize the partitions using 'gparted' afterwards to use the extra space.

BTW, I did see a 10TB WD-Red on sale yesterday for $160. [https://www.amazon.com/gp/product/B08TZPS4QQ/](https://www.amazon.com/gp/product/B08TZPS4QQ/)  WD makes 2 different technology "Red" HDDs.  I don't remember which we want, so it could be that sale device is on the "avoid" group.  IDK.

Some hardware will only work with specific sized HDDs, so beware in changing sizes too.  I have a 4-slot external array that wouldn't accept 4TB HDDs, but worked fine with 2TB.

[https://edwardbetts.com/price_per_tb/](https://edwardbetts.com/price_per_tb/) - Newegg
[https://diskprices.com/](https://diskprices.com/) - Amazon
Updated daily.

BTW, the WD My Cloud NAS had some security failures where all the data was made available over the internet, so definitely ensure you run the latest firmware and you'll probably want to block all internet access directly to that device at your router.
[https://www.engadget.com/western-digital-my-cloud-os-3-vulnerability-212839292.html](https://www.engadget.com/western-digital-my-cloud-os-3-vulnerability-212839292.html) - won't fix.
[https://krebsonsecurity.com/2021/07/another-0-day-looms-for-many-western-digital-users/](https://krebsonsecurity.com/2021/07/another-0-day-looms-for-many-western-digital-users/)
[https://arstechnica.com/information-technology/2022/01/western-digital-finally-releases-patch-for-critical-my-cloud-os-3-bugs/](https://arstechnica.com/information-technology/2022/01/western-digital-finally-releases-patch-for-critical-my-cloud-os-3-bugs/)
[https://www.theverge.com/2021/7/2/22561140/wd-cloud-os-3-security-flaw-update-patch-disconnect](https://www.theverge.com/2021/7/2/22561140/wd-cloud-os-3-security-flaw-update-patch-disconnect)

Beware.

---

### Post by michael351 on 2023-01-12
Thanks for your reply and suggestions. I will look into all of it.

I am not too concerned about security from the Internet as I don't use these drives over the Internet, only behind my firewall for my home network. External access is turned off and only specific MAC addresses can access the drive. I am aware of the issue WD faced, but glad I wasn't in that situation anyway.

---

### Post by michael351 on 2023-01-16
I have begun the process of cloning my 4 TB NAS drive to a duplicate drive which is brand new.

I notice that when I do a "lsblk", I can see the partitions of the old drive (/dev/sdb, 1,2,3, etc), but the new drive shows nothing, just /dev/sdc
I half expected the partition structure would have been copied over straight away?

---

### Post by TheFu on 2023-01-16
> **michael351 said:**
> I have begun the process of cloning my 4 TB NAS drive to a duplicate drive which is brand new.

I notice that when I do a "lsblk", I can see the partitions of the old drive (/dev/sdb, 1,2,3, etc), but the new drive shows nothing, just /dev/sdc
I half expected the partition structure would have been copied over straight away?

Partition tables are cached by the OS.  Until a re-read is forced, which wouldn't be a good idea in the middle of a clone operation. Also, since the UUIDs are being cloned too, the OS can get confused about which drive and/or partitions are involved.  That would be very bad.

Last time I cloned 4TB, it was 26 hrs.

---

### Post by michael351 on 2023-01-16
I am using blocksize = 1M. It seems my dd copy will take 3 times longer than the one you reported.
My goal is to simply plug the new drive back into my NAS enclosure and boot it up. or perhaps run a filesystem check and fix any errors first.

This is what "status=progress" is reporting:
> 242148864 bytes (9.2 GB, 8.6 GiB) copied, 558.664 s, 16.5 MB/s
9244246016 bytes (9.2 GB, 8.6 GiB) copied, 586 s, 15.8 MB/s
dd: error reading '/dev/sdb': Input/output error
8808+8 records in
8816+0 records out
9244246016 bytes (9.2 GB, 8.6 GiB) copied, 589.518 s, 15.7 MB/s
9245294592 bytes (9.2 GB, 8.6 GiB) copied, 602 s, 15.4 MB/s
dd: error reading '/dev/sdb': Input/output error
8808+9 records in
8817+0 records out
9245294592 bytes (9.2 GB, 8.6 GiB) copied, 605.156 s, 15.3 MB/s
9247391744 bytes (9.2 GB, 8.6 GiB) copied, 629 s, 14.7 MB/s
dd: error reading '/dev/sdb': Input/output error
8809+10 records in
8819+0 records out
9247391744 bytes (9.2 GB, 8.6 GiB) copied, 632.323 s, 14.6 MB/s
9248440320 bytes (9.2 GB, 8.6 GiB) copied, 651 s, 14.2 MB/s
dd: error reading '/dev/sdb': Input/output error
8809+11 records in
8820+0 records out
[B]9248440320 bytes (9.2 GB, 8.6 GiB) copied, 653.879 s, 14.1 MB/s
144746479616 bytes (145 GB, 135 GiB) copied, 9452 s, 15.3 MB/s[/B]

---

### Post by TheFu on 2023-01-16
I don't use dd.  I use 'ddrescue' with failed drives.  It has automatic features to deal with dying/dead sectors.  For good devices, I'd use 'rsync' at the file level, not the device level.

---

### Post by michael351 on 2023-01-16
I installed ddrescue, but will wait to see how 'dd' goes as it has been running now for 5 or so hours. The drive hasn't failed (yet). It has reallocated sectors and a few pending. It's on its way out.
I'd hate to start over in case this works. 
I will use ddrescue if this doesn't work.

---

### Post by TheFu on 2023-01-17
See all those I/O errors?  They aren't good.

---

### Post by michael351 on 2023-01-17
Took your advice and stopped "dd" and started ddrescue. It's been running overnight.
Transfer rate is ~15 MB/sec. and constant. The dispaly shows 2 read errors which occurred right when I started ddrescue and no change overnight.
According to the display, I have 2 days 14 hours remaining. 17% of my 4TB disk is "rescued".

[IMG]https://www.dropbox.com/s/5cj8j30xjlswkkx/ddrescue_log.PNG?dl=0[/IMG]

logfile shows:
> 
# Mapfile. Created by GNU ddrescue version 1.23
# Command line: ddrescue -f -n -r3 /dev/sdb /dev/sdc /root/ddrescue.log
# Start time:   2023-01-16 18:07:51
# Current time: 2023-01-17 06:51:31
# Copying non-tried blocks... Pass 1 (forwards)
# current_pos  current_status  current_pass
0x9AC79F0000     ?               1
#      pos        size  status
0x00000000  0x17F9A6000  +
0x17F9A6000  0x0000A000  *
0x17F9B0000  0x02630000  ?
0x181FE0000  0xA4C23000  +
0x226C03000  0x0000D000  *
0x226C10000  0x02630000  ?
0x229240000  0x989E7C0000  +
0x9AC7A00000  0x308B9DD6000  ?

I gather this is normal and ddrescue is working. I hope when this is done, I will be able to just take the new drive and put it back in my NAS box and it will boot up.
The old drive never failed - it just started to show reallocated sectors.

---

