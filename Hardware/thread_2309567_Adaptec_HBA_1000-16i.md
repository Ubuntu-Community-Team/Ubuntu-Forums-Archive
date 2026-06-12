---
title: "Adaptec HBA 1000-16i"
date: 2016-01-11
forum: Hardware
---

### Post by Hammi on 2016-01-11
Hi,

does the Adaptec HBA 1000-16i work out of the box with Ubuntu 14.04? Adaptec offers drivers for Ubuntu for this card on their website, which to me suggests it does not...? It's probably too new?

Thanks!

---

### Post by ubu_dynamite on 2016-05-01
Any news on the Adaptec HBA 1000-16i controller?
Would this work out of the box with "linux-generic-lts-xenial" under ubuntu 14.04.
Also would be nice to know if it would work nicely with [zfsonlinux]("http://zfsonlinux.org/") and [btrfs]("https://btrfs.wiki.kernel.org/index.php/Main_Page").

---

### Post by Hammi on 2016-05-02
Because of the lack of replies here and other findings, I decided against the Adaptec and in favor of a LSI 9300-16i. Works like a charm, with 14.04 and zfsonlinux. I will follow the official update path to 16.04, i.e. with the .1 release. It's running too well now to take chances. :D

---

### Post by ubu_dynamite on 2016-05-02
I have been looking ad LSI 9201-16i/9300-16i for a while also bit of a price difference though over here.

Adaptec HBA 1000-16i - €265
LSI HBA SAS 9201-16i - €416
LSI HBA SAS 9300-16i - €470

---

### Post by Hammi on 2016-05-02
Yes, the LSI is pricier (I paid a bit less than 450 &#8364;), which is why I looked at the Adaptec first. But I nevertheless ultimately went with the LSI, as I did not want to play the guinea pig with my data on a production machine.

---

### Post by ubu_dynamite on 2016-05-02
From Microsemi website sounds promising will keep an eye on it for when i really need it the "LSI 9300-16i" is way to expensive right now for my home storage.

[http://storage.microsemi.com/en-us/smartstorage/hba/](http://storage.microsemi.com/en-us/smartstorage/hba/)
> "Canonical's Cloud Alliances team has been working closely with PMC to ensure leading Ubuntu support for the HBA 1000," said John Dolen, Cloud Partner Marketing Manager.
"With the industry's highest port count, lowest power and leading performance, PMC’s new HBA is an ideal pairing with Ubuntu and OpenStack Software Defined Storage workloads." 

Some user experiences would still be nice though.

---

### Post by Hammi on 2016-05-02
Isn't that the same controller mentioned above? Adaptec appears to be a Microsemi brand. In any case, I couldn't find a price point through a quick Google search for Microsemi HBA 1000.

---

### Post by ubu_dynamite on 2016-05-02
Yes is same controller as above would save me about 50% in price compared with LSI if i buy in a trustworthy shop just wish that there was bit more info about the support/stability of the controller and compatibility with zfs/btrfs.

---

### Post by ubu_dynamite on 2016-05-10
I decided to just buy one and try it and it seems to work so far out of the box on ubuntu 14.04 with linux-generic-lts-wily 4.2.0.36.29 installed haven't tried any other kernels yet.
Just my 3 disk btrfs raid5 testing array connected to it now but it was working after bootup so will do some testing and if everything works okay will move my zfs array also  and hope for the best.

```
uname -a
Linux nas 4.2.0-36-generic #41~14.04.1-Ubuntu SMP Tue Apr 19 17:03:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```
```
lspci | grep Adaptec
01:00.0 Serial Attached SCSI controller: Adaptec Series 8 12G SAS/PCIe 3 (rev 01)
```

```
sudo lshw -class disk -class storage
  *-storage               
       description: Serial Attached SCSI controller
       product: Series 8 12G SAS/PCIe 3
       vendor: Adaptec
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: scsi0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi msix pciexpress bus_master cap_list rom emulated
       configuration: driver=aacraid latency=0
       resources: irq:16 memory:df600000-df6fffff memory:df780000-df7803ff ioport:d000(size=256) memory:df700000-df77ffff
     *-disk:0
          description: ATA Disk
          product: WDC WD10EADS-65M
          vendor: Western Digital
          physical id: 2.8.0
          bus info: scsi@0:2.8.0
          logical name: /dev/sda
          logical name: /mnt/btrfs0
          version: 0A01
          serial: WD-WCAV51272604
          size: 931GiB (1TB)
          configuration: ansiversion=6 mount.fstype=btrfs mount.options=rw,relatime,space_cache,subvolid=5,subvol=/ sectorsize=512 state=mounted
     *-disk:1
          description: ATA Disk
          product: WDC WD10EADS-00L
          vendor: Western Digital
          physical id: 2.9.0
          bus info: scsi@0:2.9.0
          logical name: /dev/sdb
          version: 1A01
          serial: WD-WCAU4D170403
          size: 931GiB (1TB)
          configuration: ansiversion=6 sectorsize=512
     *-disk:2
          description: ATA Disk
          product: WDC WD10EARS-00Y
          vendor: Western Digital
          physical id: 2.a.0
          bus info: scsi@0:2.10.0
          logical name: /dev/sdc
          version: 0A80
          serial: WD-WMAV51389092
          size: 931GiB (1TB)
          configuration: ansiversion=6 sectorsize=512
```


Its seems hddtemp can't read the temperatures off the drives connected to the controller though smartctl is working and showing the temps.
Just WDC connected to adaptec controller
```
sudo hddtemp /dev/sd{a..k}
/dev/sda: ATA WDC WD10EADS-65M:  drive supported, but it doesn't have a temperature sensor.
/dev/sdb: ATA WDC WD10EADS-00L:  drive supported, but it doesn't have a temperature sensor.
/dev/sdc: ATA WDC WD10EARS-00Y:  drive supported, but it doesn't have a temperature sensor.
/dev/sdd: Crucial_CT256M550SSD1: 34°C
/dev/sde: Crucial_CT256M550SSD1: 33°C
/dev/sdf: HGST HDN724040ALE640: 39°C
/dev/sdg: HGST HDN724040ALE640: 40°C
/dev/sdh: HGST HDN724040ALE640: 41°C
/dev/sdi: HGST HDN724040ALE640: 41°C
/dev/sdj: HGST HDN724040ALE640: 38°C
/dev/sdk: HGST HDN724040ALE640: 36°C
```

```
sudo smartctl -A /dev/sda | grep "^194"
194 Temperature_Celsius     0x0022   112   099   000    Old_age   Always       -       35
sudo smartctl -A /dev/sdb | grep "^194"
194 Temperature_Celsius     0x0022   116   103   000    Old_age   Always       -       34
sudo smartctl -A /dev/sdc | grep "^194"
194 Temperature_Celsius     0x0022   113   106   000    Old_age   Always       -       34
```

Crucial and WDC connected to motherboard sata and HGST to adaptec controller guess will have to find something else for the unmaintained hddtemp to get the temps from WDC.
```
sudo hddtemp /dev/sd{a..k}
/dev/sda: HGST HDN724040ALE640: 38°C
/dev/sdb: HGST HDN724040ALE640: 38°C
/dev/sdc: HGST HDN724040ALE640: 36°C
/dev/sdd: HGST HDN724040ALE640: 33°C
/dev/sde: HGST HDN724040ALE640: 38°C
/dev/sdf: HGST HDN724040ALE640: 39°C
/dev/sdg: Crucial_CT256M550SSD1: 29°C
/dev/sdh: Crucial_CT256M550SSD1: 28°C
/dev/sdi: WDC WD10EADS-65M2B0: 33°C
/dev/sdj: WDC WD10EADS-00L5B1: 34°C
/dev/sdk: WDC WD10EARS-00Y5B1: 31°C
```

Also can't get arcconf to work says "Controller Status : Inaccessible" same when run with root user although i,m not sure if there is much to control if it would work.
Updating the firmware with "adaptec_bootusb" worked out fine.
```

sudo ./arcconf list
Controllers found: 1
Controllers found: 1
----------------------------------------------------------------------
Controller information
----------------------------------------------------------------------
   Controller ID                            : Status, Slot, Mode, Name, SerialNumber, WWN
----------------------------------------------------------------------
   Controller 1:                            : Inaccessible, Slot 0, RAID (Expose RAW), 1000 16i, , 
```

```
sudo ./arcconf GETCONFIG 1 AL
Controllers found: 1
----------------------------------------------------------------------
Controller information
----------------------------------------------------------------------
   Controller Status                        : Inaccessible

----------------------------------------------------------------------
Logical device information
----------------------------------------------------------------------
   No logical devices configured

----------------------------------------------------------------------
Physical Device information
----------------------------------------------------------------------


----------------------------------------------------------------------
Connector information
----------------------------------------------------------------------
   No connector information available       

Command completed successfully.
```

---

### Post by chrisk2305 on 2016-06-16
Hi,

I also bought the HBA 1000-16i and I am experiencing bad performance on a ZFS Raid Z2 (raid 6). I only read and write with about 150mb/s. (6x 6TB WD Red). On an old LSI controller I achieved around 600mb/s. I am using Kernel 4.5 (I am on Gentoo, not Ubuntu but shouldn't matter). I am not sure if I should compile the driver from the Adaptec site. Can you guys do some benchmarking? Thanks in advance, Christian

---

### Post by ubu_dynamite on 2016-06-16
> **chrisk2305 said:**
> Hi,

I also bought the HBA 1000-16i and I am experiencing bad performance on a ZFS Raid Z2 (raid 6). I only read and write with about 150mb/s. (6x 6TB WD Red). On an old LSI controller I achieved around 600mb/s. I am using Kernel 4.5 (I am on Gentoo, not Ubuntu but shouldn't matter). I am not sure if I should compile the driver from the Adaptec site. Can you guys do some benchmarking? Thanks in advance, Christian

Haven't done any benchmarking but scrubbing is indeed slow on ZFS Raid Z2 (raid 6) 6x 4TB HGST Deskstar NAS.
Compiling the driver from the Adaptec site is not working on the 4.x kernel you will have to wait till august.

> Greetings from Microsemi!

Thank you for your message.  Support for the 4.x kernel and .deb version of the DKMS package is expected in the next maintenance update loosely slated for release late July or August.  Drivers for Ubuntu 15 & 16 with 4x kernel support should be included in the web release then.
 
Thank you for using ASK Us.

Best Regards,
Microsemi Technical Support

---

### Post by ubu_dynamite on 2016-06-19
These tests did not come out that bad but scrubbing is about 80MB/s it has been faster but it had lesser data on it and the drives where not connected to the adaptec back then so not sure its the controller the extra data or some update to zfs.
Any tips for better benchmarking avoiding cache?

6x 4TB HGST Deskstar NAS Raidz2
```
$ bonnie++ -d /mnt/pool0/vol0/test -r 32768
Writing a byte at a time...done
Writing intelligently...done
Rewriting...done
Reading a byte at a time...done
Reading intelligently...done
start 'em...done...done...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.97       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
nas             64G    55  99 354143  99 204539  78   204  99 797654  91 107.7   6
Latency               148ms    7928us     295ms   51515us     117ms     386ms
Version  1.97       ------Sequential Create------ --------Random Create--------
nas                 -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  3866  98 +++++ +++  4139  54  3598  98 +++++ +++ 10061  75
Latency             55941us     494us     758ms   99456us      53us     192ms
1.97,1.97,nas,1,1466388940,64G,,55,99,354143,99,204539,78,204,99,797654,91,107.7,6,16,,,,,3866,98,+++++,+++,4139,54,3598,98,+++++,+++,10061,75,148ms,7928us,295ms,51515us,117ms,386ms,55941us,494us,758ms,99456us,53us,192ms


$ dd if=/dev/zero of=tempfile bs=1M count=1024 conv=fdatasync,notrunc
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 1.13242 s, 948 MB/s

# echo 3 > /proc/sys/vm/drop_caches
$ dd if=tempfile of=/dev/null bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 0.647431 s, 1.7 GB/s


$ sudo hdparm -t /dev/sda
/dev/sda:
 Timing buffered disk reads: 482 MB in  3.01 seconds = 160.10 MB/sec

$ sudo hdparm -t /dev/sdb
/dev/sdb:
 Timing buffered disk reads: 496 MB in  3.00 seconds = 165.19 MB/sec

$ sudo hdparm -t /dev/sdc
/dev/sdc:
 Timing buffered disk reads: 480 MB in  3.00 seconds = 159.74 MB/sec

$ sudo hdparm -t /dev/sdd
/dev/sdd:
 Timing buffered disk reads: 476 MB in  3.00 seconds = 158.59 MB/sec

$ sudo hdparm -t /dev/sdh
/dev/sdh:
 Timing buffered disk reads: 474 MB in  3.00 seconds = 157.87 MB/sec

$ sudo hdparm -t /dev/sdi
/dev/sdi:
 Timing buffered disk reads: 498 MB in  3.01 seconds = 165.52 MB/sec
```


```
$ dd if=/dev/zero of=tempfile bs=1M count=131072 conv=fdatasync,notrunc
131072+0 records in
131072+0 records out
137438953472 bytes (137 GB) copied, 127.472 s, 1.1 GB/s

# echo 3 > /proc/sys/vm/drop_caches
$ dd if=tempfile of=/dev/null bs=1M count=131072
131072+0 records in
131072+0 records out
137438953472 bytes (137 GB) copied, 81.9314 s, 1.7 GB/s
```

---

### Post by ubu_dynamite on 2016-09-02
I noticed that i,m getting really bad performance the more drives are accessed doing a hdparm to 11 disks at once giving me a read speed of 22MB/sec or worse per disk with max of 4 drives per connector.
The dd commands in last post may also not be accurate because i,m using compression.

Also there is still no support for the 4.x kernel just send a support request again.

---

### Post by Hammi on 2016-09-03
I wouldn't be too surprised about performance issues as long as it's not officially supported.

I just noticed, by the way, that prices for the Adaptec 1000-16i have gone up here. It's around 350 &#8364;, only 70 &#8364; less than the LSI currently.

---

