---
title: "Very slow disk I/O"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Explosive_Cornflake on 2006-10-29
I made a file sever a few months back. The Disk I/O has always been very slow on it. At the moment I'm copying about 200GB of data from one IDE drive to a SATA drive, and it's taken about 5 hours so far, and it's still going.
The hardware is as follows.
[Gigabyte  GA-7VKML Motherboard](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1306)
Duron 1300+
512 DDR
[Sunway 4 Port Sata card (Sil 3114 Chipset)](http://www.sunsway.com.hk/products/pci-sata-4.html)
1 * 250 GB Samsung IDE on Primary Master IDE 
2 * 200 GB Samsung Sata
1 * 200 GB Maxtor Sata
1 * 320 GB Seagate Sata
Running Kubuntu Edgy Final
```
ccoffey@Branigan:~$ uname -r
2.6.17-10-generic
```
```
ccoffey@Branigan:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda3 on /media/hda3 type ext3 (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw)
/dev/sdc1 on /media/sdc1 type reiserfs (rw)
/dev/sdd1 on /media/sdd1 type ext3 (rw)
```
```
ccoffey@Branigan:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
00:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```
Does anyone have any idea why it is so slow. As you can see I've tried different FS types without any joy.
Any further tests you want me to run, just let me know.

---

### Post by zgornel on 2006-10-29
If there are 200GB of very small files, it is normal to take a lot of time, maybe not 5 hrs but still... Try and run some benchmarks ($ sudo hdparm -tT /dev/sdx) on all hard drives and see if the transfer rates are normal.

---

### Post by Explosive_Cornflake on 2006-10-29
It's films and episodes I'm moving, so certainly not small files :) .
It's was taking 5 minutes to run the tests earlier, and half way through, it went back taking a few seconds. And the speed has increased a bit, weird. Anyway....
Samsung 250gig IDE - ext3
```
ccoffey@Branigan:~$ date +%H:%M:%S && sudo hdparm -tT /dev/hda3 && date +%H:%M:%S
18:44:35

/dev/hda3:
 Timing cached reads:   876 MB in  2.01 seconds = 436.18 MB/sec
 Timing buffered disk reads:  204 MB in  3.02 seconds =  67.44 MB/sec
18:44:48

```

Maxtor 200gig Sata - ext3
```
ccoffey@Branigan:~$ date +%H:%M:%S && sudo hdparm -tT /dev/sda1 && date +%H:%M:%S
18:45:45

/dev/sda1:
 Timing cached reads:   872 MB in  2.01 seconds = 434.48 MB/sec
 Timing buffered disk reads:  178 MB in  3.03 seconds =  58.67 MB/sec
18:45:58

```

Samsung 200gig Sata -ext3
```
ccoffey@Branigan:~$ date +%H:%M:%S && sudo hdparm -tT /dev/sdb1 && date +%H:%M:%S
18:46:23

/dev/sdb1:
 Timing cached reads:   872 MB in  2.01 seconds = 434.82 MB/sec
 Timing buffered disk reads:  158 MB in  3.03 seconds =  52.11 MB/sec
18:46:36

```

Seagate 320gb 7200.10 sata - resierfs
```
ccoffey@Branigan:~$ date +%H:%M:%S && sudo hdparm -tT /dev/sdc1 && date +%H:%M:%S
18:48:41

/dev/sdc1:
 Timing cached reads:   864 MB in  2.01 seconds = 430.52 MB/sec
 Timing buffered disk reads:  144 MB in  3.02 seconds =  47.74 MB/sec
18:48:55

```


Samsung 200gig Sata - ext3
**NB** I re did test, and it took 17 seconds. Drives aren't set to sleep.
```
ccoffey@Branigan:~$ date +%H:%M:%S && sudo hdparm -tT /dev/sdd1 && date +%H:%M:%S
18:34:40

/dev/sdd1:
 Timing cached reads:   796 MB in  2.00 seconds = 397.21 MB/sec
 Timing buffered disk reads:   50 MB in  3.13 seconds =  15.99 MB/sec
18:39:35

```
**NB**I re did test, and it took 17 seconds. Drives aren't set to sleep..

Now testing the exact same model of seagate in my Desktop (Conroe E6600, Asus P5W DH Deluxe)
```
ccoffey@Zoidberg:~$ date +%H:%M:%S && sudo hdparm -tT /dev/sda5 && date +%H:%M:%S
18:34:54

/dev/sda5:
 Timing cached reads:   14240 MB in  2.00 seconds = 7130.80 MB/sec
 Timing buffered disk reads:  218 MB in  3.01 seconds =  72.36 MB/sec
18:35:07

```

---

### Post by zgornel on 2006-10-29
Well, there is certainly no IDE speed problem. Might be some strange driver bug.

---

### Post by Explosive_Cornflake on 2006-10-29
This is my file server so X shouldn't be needed, but I thought a better approach would be to use XDMCP on it.
Anyway, running konqueror as root, this is what I'm faced with
[img]http://www.ecornflake.com/Images/snapshot1.png[/img]

---

### Post by chalex on 2006-10-29
hdparm doesn't care at all about the type of filesystem you have on the disk.  Anyway, your hdparm numbers should look about 50MB/s.

Are there any unusual errors in your /var/log/messages or /var/log/syslog?

You could install the package "sysstat" and look at the "iostat" output.

My first thought would be to blame your Sil3114 chipset.  It's a crummy chipset, and this might be the best performance you can get out of it.

---

### Post by Explosive_Cornflake on 2006-10-29
I think I'll blame the motherboard. It's a piece of crap, but I got it for free so I won't complain too much.
Nothing to report from the the log files.
```
ccoffey@Branigan:/media/hda3/Writeable$ iostat
Linux 2.6.17-10-generic (Branigan)      10/29/2006

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           2.77    0.03   11.57   79.34    0.00    6.29

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0.01         0.24         0.01       2350        120
sdb              20.21         8.32     16773.83      80680  162646632
sdc               0.25         2.15         0.01      20824        112
sdd              36.58     15853.15        12.51  153719296     121290
hda               2.39        58.31        26.08     565405     252928

```

---

