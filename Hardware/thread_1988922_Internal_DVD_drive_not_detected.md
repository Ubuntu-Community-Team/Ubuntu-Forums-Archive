---
title: "Internal DVD drive not detected"
date: 2012-05-28
forum: Hardware
---

### Post by blalasaadri on 2012-05-28
Hi everyone!
I'm having a problem with an Acer Aspire 7520: Kubuntu won't detect the internal dvd drive. This problem existed with 11.10 and when I installed 12.04 (completely new installation, not an update) nothing changed - although I installed the system THROUGH that drive.
I tried finding any trace of the drive, so far with no luck. Here's commands that didn't bear any fruit:
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
...
/dev/sdb1 on /media/sdb1 type ext4 (rw,noexec,nosuid,nodev)
/dev/sda5 on /home type ext4 (rw)

``` OK, that just confirms what I already knew: the drive is not mounted.
```
> udisks --enumerate
/org/freedesktop/UDisks/devices/sda2
/org/freedesktop/UDisks/devices/sdb1
/org/freedesktop/UDisks/devices/sda
/org/freedesktop/UDisks/devices/sda5w
/org/freedesktop/UDisks/devices/sda6
/org/freedesktop/UDisks/devices/sda1
/org/freedesktop/UDisks/devices/sdb

``` Yes, the laptop has two harddrives, which are both recognised. No dvd drive though. And yes, there was a disc in the drive at the time. 
```
> lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: Hitachi HTS54168
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SB2O
       serial: SB2241KGE2J7PE
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=4b540dbe
  *-disk:1
       description: ATA Disk
       product: Hitachi HTS54328
       vendor: Hitachi
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: FB1O
       serial: 081218FB2100LBC4U50A
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a26da26d

``` Same here. No help.
```
 > lshw -short
H/W path    Device     Class      Description
=============================================
                       system     Aspire 7520 ()
...
/0/9        scsi0      storage    MCP67 AHCI Controller
/0/9/0      /dev/sda   disk       80GB Hitachi HTS54168
/0/9/0/1    /dev/sda1  volume     36GiB EXT4 volume
/0/9/0/2    /dev/sda2  volume     38GiB Extended partition
/0/9/0/2/5  /dev/sda5  volume     37GiB Linux filesystem partition
/0/9/0/2/6  /dev/sda6  volume     980MiB Linux swap / Solaris partition
/0/9/1      /dev/sdb   disk       80GB Hitachi HTS54328
/0/9/1/1    /dev/sdb1  volume     74GiB EXT4 volume
...
``` Only thing that might be helpful here as far as I can see is scsi0...
```
> dmesg | grep scsi
[    1.278164] scsi0 : ahci
[    1.278320] scsi1 : ahci
[    1.278443] scsi2 : ahci
[    1.278560] scsi3 : ahci
[    1.598215] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    1.598468] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.598763] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54328 FB1O PQ: 0 ANSI: 5
[    1.598965] sd 2:0:0:0: Attached scsi generic sg1 type 0

``` One of the few dmesg greps that actually gave me anything possibly useful - greping for dvd, cd or drive didn't produce anything worth quoting here.
Even though it's an internal drive, I tried lsusb, which didn't list any devices (apart from the usb hubs) and ```
> ls -Adl /dev/s*
brw-rw---- 1 root disk  8,   0 May 28 14:38 /dev/sda
brw-rw---- 1 root disk  8,   1 May 28 14:38 /dev/sda1
brw-rw---- 1 root disk  8,   2 May 28 14:38 /dev/sda2
brw-rw---- 1 root disk  8,   5 May 28 14:38 /dev/sda5
brw-rw---- 1 root disk  8,   6 May 28 14:38 /dev/sda6
brw-rw---- 1 root disk  8,  16 May 28 14:38 /dev/sdb
brw-rw---- 1 root disk  8,  17 May 28 14:38 /dev/sdb1
crw-rw---- 1 root disk 21,   0 May 28 14:38 /dev/sg0
crw-rw---- 1 root disk 21,   1 May 28 14:38 /dev/sg1
...
``` didn't help me either; neither sg0 nor sg1 are block devices, at least according to the mount command.

Now I'm out of ideas. Can anyone suggest something else, which might help? It's quite annoying, not being able to use the drive...

Thanks,
Blalasaadri

---

