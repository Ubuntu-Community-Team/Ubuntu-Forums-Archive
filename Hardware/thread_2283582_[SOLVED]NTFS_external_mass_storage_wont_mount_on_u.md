---
title: "[SOLVED]NTFS external mass storage wont mount on ubuntu studio"
date: 2015-06-22
forum: Hardware
---

### Post by gh0zt362 on 2015-06-22
Now I have 2 machines. I formatted and created the ntfs file system on Fedora 21 KDE long story short I nix'd Fedora on that machine and installed ubuntu studio 15.xx.  Now when I try to mount the ntfs to ubuntu studio 15.xx it says cant mount / NTFS signature missing . Tinkering in terminal says bad magic number , bad superblock yada yada ....... 

I have a 2nd machine with fedora 21 on it and the external mounts fine , no problems transfers data I/O   with no issues. 

I tried ntfsfix -l /dev/sdb1 and it says access denied on Ubuntu  ....... not sure whats going on here. 

I dont want to not have my music on this machine .... so what can I do ?

---

### Post by gh0zt362 on 2015-06-23
also mounts to windows no problem .... just ubuntu it wont . Whats the deal neal ?

---

### Post by gh0zt362 on 2015-06-23
windows chkdsk says no bad sectors and found no problems .

---

### Post by gh0zt362 on 2015-06-23
```
[  235.360558]  sdb: AHDI sdb1 sdb2
[  235.360574] sdb: p1 size 1702064928 extends beyond EOD, truncated
[  235.365656] sd 4:0:0:0: [sdb] Attached SCSI disk
[  356.328475] usb 3-1: USB disconnect, device number 2
[  371.823994] usb 3-1: new high-speed USB device number 3 using ehci-pci
[  371.940370] usb 3-1: New USB device found, idVendor=1058, idProduct=0704
[  371.940384] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  371.940391] usb 3-1: Product: External HDD    
[  371.940396] usb 3-1: Manufacturer: Western Digital 
[  371.940401] usb 3-1: SerialNumber: 57584D314541344352554833
[  371.942634] usb-storage 3-1:1.0: USB Mass Storage device detected
[  371.943036] usb-storage 3-1:1.0: Quirks match for vid 1058 pid 0704: 8000
[  371.943127] scsi host5: usb-storage 3-1:1.0
[  372.946503] scsi 5:0:0:0: Direct-Access     WD       7500BPK External 1.05 PQ: 0 ANSI: 4
[  372.947860] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  372.949732] sd 5:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[  372.953468] sd 5:0:0:0: [sdb] Write Protect is off
[  372.953482] sd 5:0:0:0: [sdb] Mode Sense: 21 00 00 00
[  372.955595] sd 5:0:0:0: [sdb] No Caching mode page found
[  372.955605] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  373.008427]  sdb: AHDI sdb1 sdb2
[  373.008447] sdb: p1 size 1702064928 extends beyond EOD, enabling native capacity
[  373.014086]  sdb: AHDI sdb1 sdb2
[  373.014105] sdb: p1 size 1702064928 extends beyond EOD, truncated
[  373.018606] sd 5:0:0:0: [sdb] Attached SCSI disk
[  574.218769]  sdb: AHDI sdb1 sdb2
[  574.218811] sdb: p1 size 1702064928 extends beyond EOD, truncated
[  606.933622] usb 3-1: USB disconnect, device number 3
[  615.728877] usb 3-1: new high-speed USB device number 4 using ehci-pci
[  615.845295] usb 3-1: New USB device found, idVendor=1058, idProduct=0704
[  615.845309] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  615.845316] usb 3-1: Product: External HDD    
[  615.845321] usb 3-1: Manufacturer: Western Digital 
[  615.845326] usb 3-1: SerialNumber: 57584D314541344352554833
[  615.846869] usb-storage 3-1:1.0: USB Mass Storage device detected
[  615.847130] usb-storage 3-1:1.0: Quirks match for vid 1058 pid 0704: 8000
[  615.847241] scsi host6: usb-storage 3-1:1.0
[  616.852301] scsi 6:0:0:0: Direct-Access     WD       7500BPK External 1.05 PQ: 0 ANSI: 4
[  616.852993] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  616.854158] sd 6:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[  616.855742] sd 6:0:0:0: [sdb] Write Protect is off
[  616.855760] sd 6:0:0:0: [sdb] Mode Sense: 21 00 00 00
[  616.859913] sd 6:0:0:0: [sdb] No Caching mode page found
[  616.859922] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  616.912595]  sdb: AHDI sdb1 sdb2
[  616.912633] sdb: p1 size 1702064928 extends beyond EOD, enabling native capacity
[  616.917906]  sdb: AHDI sdb1 sdb2
[  616.917924] sdb: p1 size 1702064928 extends beyond EOD, truncated
[  616.922154] sd 6:0:0:0: [sdb] Attached SCSI disk
[ 1170.503018] usb 3-1: USB disconnect, device number 4
[ 1865.815391] usb 3-1: new high-speed USB device number 5 using ehci-pci
[ 1865.931861] usb 3-1: New USB device found, idVendor=1058, idProduct=0704
[ 1865.931875] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1865.931882] usb 3-1: Product: External HDD    
[ 1865.931887] usb 3-1: Manufacturer: Western Digital 
[ 1865.931891] usb 3-1: SerialNumber: 57584D314541344352554833
[ 1865.933243] usb-storage 3-1:1.0: USB Mass Storage device detected
[ 1865.934422] usb-storage 3-1:1.0: Quirks match for vid 1058 pid 0704: 8000
[ 1865.934610] scsi host7: usb-storage 3-1:1.0
[ 1866.937999] scsi 7:0:0:0: Direct-Access     WD       7500BPK External 1.05 PQ: 0 ANSI: 4
[ 1866.939100] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1866.939773] sd 7:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[ 1866.940994] sd 7:0:0:0: [sdb] Write Protect is off
[ 1866.941010] sd 7:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 1866.942230] sd 7:0:0:0: [sdb] No Caching mode page found
[ 1866.942243] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1867.001099]  sdb: AHDI sdb1 sdb2
[ 1867.001138] sdb: p1 size 1702064928 extends beyond EOD, enabling native capacity
[ 1867.006513]  sdb: AHDI sdb1 sdb2
[ 1867.006532] sdb: p1 size 1702064928 extends beyond EOD, truncated
[ 1867.010724] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 2741.079021] usb 3-1: USB disconnect, device number 5
[ 5411.727930] usb 6-1: new full-speed USB device number 2 using ohci-pci
[ 5411.867212] usb 6-1: not running at top speed; connect to a high speed hub
[ 5411.879036] usb 6-1: New USB device found, idVendor=1058, idProduct=0704
[ 5411.879049] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 5411.879056] usb 6-1: Product: External HDD    
[ 5411.879061] usb 6-1: Manufacturer: Western Digital 
[ 5411.879066] usb 6-1: SerialNumber: 57584D314541344352554833
[ 5411.881193] usb-storage 6-1:1.0: USB Mass Storage device detected
[ 5411.881728] usb-storage 6-1:1.0: Quirks match for vid 1058 pid 0704: 8000
[ 5411.881845] scsi host8: usb-storage 6-1:1.0
[ 5412.891560] scsi 8:0:0:0: Direct-Access     WD       7500BPK External 1.05 PQ: 0 ANSI: 4
[ 5412.893249] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 5412.901431] sd 8:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[ 5412.911402] sd 8:0:0:0: [sdb] Write Protect is off
[ 5412.911412] sd 8:0:0:0: [sdb] Mode Sense: 21 00 00 00
[ 5412.921403] sd 8:0:0:0: [sdb] No Caching mode page found
[ 5412.921411] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 5413.016598]  sdb: AHDI sdb1 sdb2
[ 5413.016638] sdb: p1 size 1702064928 extends beyond EOD, enabling native capacity
[ 5413.064585]  sdb: AHDI sdb1 sdb2
[ 5413.064601] sdb: p1 size 1702064928 extends beyond EOD, truncated
[ 5413.122577] sd 8:0:0:0: [sdb] Attached SCSI disk
gh0zt36@Toshi:~$ 

``` 


blkid doesnt even register its attached. I was going to manually create a mount point with uuid but I cant get an ID off blkid   soooo  ...

---

### Post by gh0zt362 on 2015-06-23
Bump for the daytime crew.    This drive works on everything but ubuntu .   BLKID doesnt show it . windows chkdsk says no problems 0 bad sectors   tried to create a new UUID in gparted and now getting a

 " Error mounting /dev/sdb1 at /media/gh0zt36/6CD3134B62379A00: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/gh0zt36/6CD3134B62379A00"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0x5f0e674b  size: 1024   usa_ofs: 33238  usa_count: 20615: Invalid argument
Record 0 has no FILE magic (0x5f0e674b)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
. "  

Error

---

### Post by weatherman2 on 2015-06-23
Do you have any other NTFS disks you could try mounting with your Ubuntu install?  I haven't used 15.04 - I assume it includes NTFS support automatically like older versions of Ubuntu but not sure.

For fun, try booting say Ubuntu 14.04 live USB on the same hardware and seeing if there's any change.

If by any chance this is a portable USB-powered drive, could be it's not powering the drive enough off of just one USB port.  The real-life power capabilities of USB ports vary by machine and tended to be weaker on older machines, hence the need occasionally for a "Y" adapter to tap off of two USB ports to power on USB device.  If the drive is externally powered with its own power supply then disregard.

---

### Post by oldfred on 2015-06-23
size 1702064928 extends beyond EOD

Post this, if it shows your sdb:
sudo parted -l

---

### Post by gh0zt362 on 2015-06-23
> **weatherman2 said:**
> Do you have any other NTFS disks you could try mounting with your Ubuntu install?  I haven't used 15.04 - I assume it includes NTFS support automatically like older versions of Ubuntu but not sure.

For fun, try booting say Ubuntu 14.04 live USB on the same hardware and seeing if there's any change.

**If by any chance this is a portable USB-powered drive, could be it's not powering the drive enough off of just one USB port.  **The real-life power capabilities of USB ports vary by machine and tended to be weaker on older machines, hence the need occasionally for a "Y" adapter to tap off of two USB ports to power on USB device.  If the drive is externally powered with its own power supply then disregard.

It is . I pulled a external drive apart long ago and removed the hardware drive interface out and now I just use it as a generic interface for any hdd Im using and yess it does pull power off the USB . I never  knew that could be an issue though . Funny enough the windows machine and the fedora 21 machine are both circa what 2009 ?  and the usb powered the drive just fine and the Ubuntu studio is a circa 2012 quad core machine with way better specs. 




Thanks oldfred and weatherman .  I ended up just reformatting / partitioning the drive and re copying my back ups from the fedora machine . Now the drive shows up on all 3 machines. 

I coulda done that to begin with but I wanted to try to figure out why the problem was occurring and fix it . Alas I missed having my music on the ubuntu studio machine .

BTW what a distro .  I installed all the production packages when I installed it video , music , photos , graphics   soooo much win in this thing,

---

