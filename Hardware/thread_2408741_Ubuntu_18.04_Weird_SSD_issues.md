---
title: "Ubuntu 18.04 Weird SSD issues"
date: 2018-12-22
forum: Hardware
---

### Post by 2155x on 2018-12-22
Hello,

I've recently purchased a SSD for my system so I can dual boot Windows 10 (HDD) and Linux (SSD). Everything works fine and I can use both OS's, but I have some weird issues with my SSD.

After numerous different testing I've noticed that if the SSD activity goes up, the system might freeze for like 5-15 seconds. Most of the time I can move my mouse and click on a few things but usually I can just move the mouse and wait.
Also, my root partition seems to be slowing down the SSD aswell, it used to reach 400MB/s+, while now it reaches about 200MB/s, just like my hard drive.

Speeds I get using 'hdparm':

```
sdb2   /          partition  201.46 MB/sec
sdb3   /boot/efi  partition  522.69 MB/sec
sdb4   /home      partition  393.82 MB/sec
```

I'm not sure on what to do, the freezing is starting to get quite annoying and happens usually when I'm just browsing chrome and suddently start loading something. It also happens very often during the 'Disk Benchmark' process of the 'Disks' app.

Output of 'fdisk -l' for the SSD:

```
Disk /dev/sdb: 447.1 GiB, 480103981056 bytes, 937703088 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6CE8A305-B6DB-471B-B844-140F32D6D3AF


Device         Start       End   Sectors   Size Type
/dev/sdb2       2048 244172799 244170752 116.4G Linux filesystem
/dev/sdb3  244172800 245172223    999424   488M EFI System
/dev/sdb4  245172224 937701375 692529152 330.2G Linux filesystem

```

Issue solving priority:
1. Random 5-15 second freezes when SSD IO activity increases.
2. Root partition being twice as slow as before.

The SSD: Kingston A400 480GB

I am running Ubuntu 18.04 with the GNOME environment if that helps.

PS: Using the USB installation flash, I still received ~200MB/s speeds on the root partition.

Thank you.

UPDATE: Seems like benchmarking the speeds of each partition seperately or the entire SSD using the 'Disks' app gives proper 500MB/s read speeds. 
Why would the 'hdparm' test be throttled down by the root partition?

---

### Post by ajgreeny on 2018-12-22
What m/b do you have and in what make of computer?

Some makers require a BIOS/UEFI update to get the best from certain types of SSD so that may be worth investigating further.

---

### Post by 2155x on 2018-12-22
I have the MSI H81M-P33, it's a custom build. I have updated the bios to the latest before installing the SSD.

Thank you.

---

### Post by oldfred on 2018-12-22
Have you updated firmware. Note only for Windows.
[https://www.kingston.com/us/support/technical/ssdmanager](https://www.kingston.com/us/support/technical/ssdmanager)

I do not understand why many vendors at least do not offer a way for Linux users to update firmware.
But some vendors now support UEFI/firmware updates.
       [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by 2155x on 2018-12-22
Hello again.

After updating the firmware I ran some tests and the speeds, stability look better. 'hdparm' also shows a higher speed of 337MB/s average which is still under what speeds it reached the first week I had it, but it is definitely better than 15 minutes ago.
I will do more tests and hope that the freezing issue is gone too.

If anyone else knows anything more that could help, I would appreciate it.

**SOLVED**: Went ahead and randomly moved partitions around like 4 times, resizing one by 1MB and putting it all back to what it was. Combining that with the SSD firmware update it seems that both of my issues are solved. The read speeds reached 509MB/s average which is higher than the advertised 500MB/s.

If you have any more tips to increase speed of the SSD, feel free to PM me.

Thank you very much and happy holidays.

---

### Post by poncho0 on 2019-03-27
Hello


How did you update the firmware?

> **2155x said:**
> Hello again.

After updating the firmware I ran some tests and the speeds, stability look better. 'hdparm' also shows a higher speed of 337MB/s average which is still under what speeds it reached the first week I had it, but it is definitely better than 15 minutes ago.
I will do more tests and hope that the freezing issue is gone too.

If anyone else knows anything more that could help, I would appreciate it.

**SOLVED**: Went ahead and randomly moved partitions around like 4 times, resizing one by 1MB and putting it all back to what it was. Combining that with the SSD firmware update it seems that both of my issues are solved. The read speeds reached 509MB/s average which is higher than the advertised 500MB/s.

If you have any more tips to increase speed of the SSD, feel free to PM me.

Thank you very much and happy holidays.

---

### Post by AnotherBrian on 2019-03-28
also check smart data for the drive.  the disks utility upper right drop down will report the smart data.

---

