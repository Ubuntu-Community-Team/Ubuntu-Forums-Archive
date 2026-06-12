---
title: "External Hard drive Trouble, help?"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by wesxohio on 2007-07-08
I just bought a PowerSpec usb external hard drive enclosure and put one of my old hard drives in and plugged everything in.

the hard drive boots up and the light flashes every so often on the drive but nothing comes up and i can't locate it to browse through the folder.

i am using feisty fawn

---

### Post by taurus on 2007-07-08
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by wesxohio on 2007-07-08
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
```
~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4724    37945498+  83  Linux
/dev/hda2            4725        4864     1124550    5  Extended
/dev/hda5            4725        4864     1124518+  82  Linux swap / Solaris
 
```

---

### Post by wesxohio on 2007-07-08
these are more codes i have ran to give everyone more information ... i'm really sorry, i am  new at this

```
wes@ubuntu:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-lowlatency/volatile type tmpfs (rw)
none on /proc/bus/usb type usbfs (rw,devgid=1002,devmode=664)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```


```
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  7.0G   27G  21% /
varrun                188M  100K  188M   1% /var/run
varlock               188M     0  188M   0% /var/lock
udev                  188M  100K  188M   1% /dev
devshm                188M   16K  188M   1% /dev/shm
lrm                   188M   33M  156M  18% /lib/modules/2.6.20-15-lowlatency/volatile

```


```
wes@ubuntu:~$ dmesg > before
wes@ubuntu:~$ dmesg > after
wes@ubuntu:~$ diff before after
1081a1082,1206
> [48133.115000] usb 3-2: new high speed USB device using ehci_hcd and address 4
> [48133.236000] usb 3-2: configuration #1 chosen from 1 choice
> [48133.236000] scsi2 : SCSI emulation for USB Mass Storage devices
> [48133.237000] usb-storage: device found at 4
> [48133.237000] usb-storage: waiting for device to settle before scanning
> [48138.237000] usb-storage: device scan complete
> [48139.429000] scsi 2:0:0:0: Direct-Access     SAMSUNG  SP0802N          TK10 PQ: 0 ANSI: 2
> [48139.432000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
> [48139.433000] sda: Write Protect is off
> [48139.433000] sda: Mode Sense: 00 00 00 00
> [48139.433000] sda: assuming drive cache: write through
> [48139.434000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
> [48139.435000] sda: Write Protect is off
> [48139.435000] sda: Mode Sense: 00 00 00 00
> [48139.435000] sda: assuming drive cache: write through
> [48139.435000]  sda:end_request: I/O error, dev sda, sector 0
> [48139.446000] printk: 265 messages suppressed.
> [48139.446000] Buffer I/O error on device sda, logical block 0
> [48139.448000] end_request: I/O error, dev sda, sector 0
> [48139.448000] Buffer I/O error on device sda, logical block 0
> [48139.449000] end_request: I/O error, dev sda, sector 0
> [48139.449000] Buffer I/O error on device sda, logical block 0
> [48139.450000] end_request: I/O error, dev sda, sector 0
> [48139.450000] Buffer I/O error on device sda, logical block 0
> [48139.451000] end_request: I/O error, dev sda, sector 0
> [48139.451000] Buffer I/O error on device sda, logical block 0
> [48139.451000] ldm_validate_partition_table(): Disk read failed.
> [48139.453000] end_request: I/O error, dev sda, sector 0
> [48139.453000] Buffer I/O error on device sda, logical block 0
> [48139.454000] end_request: I/O error, dev sda, sector 0
> [48139.454000] Buffer I/O error on device sda, logical block 0
> [48139.455000] end_request: I/O error, dev sda, sector 0
> [48139.455000] Buffer I/O error on device sda, logical block 0
> [48139.456000] end_request: I/O error, dev sda, sector 0
> [48139.456000] Buffer I/O error on device sda, logical block 0
> [48139.456000] Dev sda: unable to read RDB block 0
> [48139.458000] end_request: I/O error, dev sda, sector 0
> [48139.458000] Buffer I/O error on device sda, logical block 0
> [48139.459000] end_request: I/O error, dev sda, sector 0
> [48139.460000] end_request: I/O error, dev sda, sector 24
> [48139.461000] end_request: I/O error, dev sda, sector 24
> [48139.462000] end_request: I/O error, dev sda, sector 0
> [48139.462000]  unknown partition table
> [48139.462000] sd 2:0:0:0: Attached scsi disk sda
> [48139.463000] sd 2:0:0:0: Attached scsi generic sg0 type 0
> [48139.617000] end_request: I/O error, dev sda, sector 156367872
> [48139.634000] end_request: I/O error, dev sda, sector 156367872
> [48139.684000] end_request: I/O error, dev sda, sector 156368008
> [48139.693000] end_request: I/O error, dev sda, sector 156368008
> [48139.701000] end_request: I/O error, dev sda, sector 156368008
> [48139.709000] end_request: I/O error, dev sda, sector 156368008
> [48139.718000] end_request: I/O error, dev sda, sector 156368008
> [48139.726000] end_request: I/O error, dev sda, sector 156368008
> [48139.734000] end_request: I/O error, dev sda, sector 156367952
> [48139.743000] end_request: I/O error, dev sda, sector 156368000
> [48139.751000] end_request: I/O error, dev sda, sector 156368008
> [48139.760000] end_request: I/O error, dev sda, sector 156368008
> [48139.761000] end_request: I/O error, dev sda, sector 0
> [48139.763000] end_request: I/O error, dev sda, sector 0
> [48139.765000] end_request: I/O error, dev sda, sector 0
> [48139.766000] end_request: I/O error, dev sda, sector 0
> [48139.780000] end_request: I/O error, dev sda, sector 0
> [48139.781000] end_request: I/O error, dev sda, sector 0
> [48139.783000] end_request: I/O error, dev sda, sector 0
> [48139.785000] end_request: I/O error, dev sda, sector 0
> [48139.786000] end_request: I/O error, dev sda, sector 0
> [48139.788000] end_request: I/O error, dev sda, sector 0
> [48139.789000] end_request: I/O error, dev sda, sector 0
> [48139.791000] end_request: I/O error, dev sda, sector 0
> [48139.792000] end_request: I/O error, dev sda, sector 0
> [48139.794000] end_request: I/O error, dev sda, sector 0
> [48139.795000] end_request: I/O error, dev sda, sector 0
> [48139.797000] end_request: I/O error, dev sda, sector 0
> [48139.798000] end_request: I/O error, dev sda, sector 0
> [48139.800000] end_request: I/O error, dev sda, sector 0
> [48139.802000] end_request: I/O error, dev sda, sector 0
> [48139.803000] end_request: I/O error, dev sda, sector 0
> [48139.805000] end_request: I/O error, dev sda, sector 0
> [48139.806000] end_request: I/O error, dev sda, sector 0
> [48139.808000] end_request: I/O error, dev sda, sector 0
> [48139.810000] end_request: I/O error, dev sda, sector 0
> [48139.811000] end_request: I/O error, dev sda, sector 0
> [48139.813000] end_request: I/O error, dev sda, sector 0
> [48139.815000] end_request: I/O error, dev sda, sector 0
> [48139.816000] end_request: I/O error, dev sda, sector 0
> [48139.900000] end_request: I/O error, dev sda, sector 156367872
> [48139.908000] end_request: I/O error, dev sda, sector 156367872
> [48139.918000] end_request: I/O error, dev sda, sector 156368008
> [48139.927000] end_request: I/O error, dev sda, sector 156368008
> [48139.935000] end_request: I/O error, dev sda, sector 156368008
> [48139.943000] end_request: I/O error, dev sda, sector 156368008
> [48139.952000] end_request: I/O error, dev sda, sector 156368008
> [48139.960000] end_request: I/O error, dev sda, sector 156368008
> [48139.968000] end_request: I/O error, dev sda, sector 156367952
> [48139.977000] end_request: I/O error, dev sda, sector 156368000
> [48139.986000] end_request: I/O error, dev sda, sector 156368008
> [48139.993000] end_request: I/O error, dev sda, sector 156368008
> [48139.995000] end_request: I/O error, dev sda, sector 0
> [48139.996000] end_request: I/O error, dev sda, sector 0
> [48139.998000] end_request: I/O error, dev sda, sector 0
> [48139.999000] end_request: I/O error, dev sda, sector 0
> [48140.000000] end_request: I/O error, dev sda, sector 0
> [48140.002000] end_request: I/O error, dev sda, sector 0
> [48140.003000] end_request: I/O error, dev sda, sector 0
> [48140.004000] end_request: I/O error, dev sda, sector 0
> [48140.006000] end_request: I/O error, dev sda, sector 0
> [48140.007000] end_request: I/O error, dev sda, sector 0
> [48140.009000] end_request: I/O error, dev sda, sector 0
> [48140.010000] end_request: I/O error, dev sda, sector 0
> [48140.011000] end_request: I/O error, dev sda, sector 0
> [48140.014000] end_request: I/O error, dev sda, sector 0
> [48140.028000] end_request: I/O error, dev sda, sector 0
> [48140.029000] end_request: I/O error, dev sda, sector 0
> [48140.030000] end_request: I/O error, dev sda, sector 0
> [48140.032000] end_request: I/O error, dev sda, sector 0
> [48140.033000] end_request: I/O error, dev sda, sector 0
> [48140.035000] end_request: I/O error, dev sda, sector 0
> [48140.036000] end_request: I/O error, dev sda, sector 0
> [48140.037000] end_request: I/O error, dev sda, sector 0
> [48140.039000] end_request: I/O error, dev sda, sector 0
> [48140.040000] end_request: I/O error, dev sda, sector 0
> [48140.042000] end_request: I/O error, dev sda, sector 0
> [48140.043000] end_request: I/O error, dev sda, sector 0
> [48140.045000] end_request: I/O error, dev sda, sector 0
> [48140.046000] end_request: I/O error, dev sda, sector 0

```

---

### Post by wesxohio on 2007-07-10
bump :(

---

### Post by dabl on 2007-07-10
Can you show your /etc/fstab file?  I think the command to list it is ```
cat /etc/fstab
```, or else just open it with a text editor and paste it in a reply.

---

