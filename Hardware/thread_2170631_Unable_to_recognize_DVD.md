---
title: "Unable to recognize DVD"
date: 2013-08-27
forum: Hardware
---

### Post by khat33b on 2013-08-27
Ubuntu is unable to recognize any DVDs I put in. It recognizes CDs. I have Ubuntu 13.04. In System Settings>Details>Disks, no information about the DVD is given. I ran the following commands:

```
$ eject -n
eject: device is `/dev/sr0'

$ sudo mount -o ro,unhide,uid=1000 /dev/cdrom /mnt/cdrom
mount: mount point /mnt/cdrom does not exist

$ sudo lshw -C disk
  *-cdrom
       description: DVD-RAM writer
       product: DVD+-RW GT32N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: A203
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

$ regionset 
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/khat33b/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=khat33b)

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=fb5c5f59-fe54-4bd5-a07f-0445adb8a66c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a01b2598-d43c-47a8-993b-3c2d030597f8 none            swap    sw              0       0

sudo hdparm -I /dev/dvd
/dev/dvd:

ATAPI CD-ROM, with removable media
    Model Number:       HL-DT-STDVD+/-RW GT32N                  
    Serial Number:      KW1B8945213         
    Firmware Revision:  A203    
    Transport:          0x7200; Revision: 0x5356
Standards:
    Likely used CD-ROM ATAPI-1
Configuration:
    DRQ response: 50us.
    Packet size: 12 bytes
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns

$ sudo dmesg | grep -i dvd //gives nothing
$ sudo dmesg | grep -i CD-ROM //gives nothing

$ ls -al /dev/hd*
ls: cannot access /dev/hd*: No such file or directory

$ ls -al /dev/sr*
brw-rw----+ 1 root cdrom 11, 0 Aug 27 10:03 /dev/sr0
```

---

### Post by Rockman-X on 2013-08-27
Ubuntu by default will not  play dvd's have you tried installing mediubuntu? 

[http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/](http://www.unixmen.com/medibuntu-repositories-available-for-ubuntu-12-04-lts-precise-pangolin-ppa/)

---

### Post by khat33b on 2013-08-27
Tried it... didn't work
I am trying to burn iso into a blank dvd
even brasero doesn't recognize the dvd
neither I am able to play any dvd movies

---

### Post by Rockman-X on 2013-08-28
The only thing I can tell you is you might want to try using another dvd-burning software. I have had problems with Brasero before. You could try another  burning software (i.e k3b) Keep in mind that if you decide to go with K3b it will cost you a couple of hundred mb in download.  You also could try and burn simply just using the command line. 

Have you tried using the command line to burn a cd following the steps here: [http://linuxconfig.org/using-command-line-wodim-tool-to-burn-iso-image](http://linuxconfig.org/using-command-line-wodim-tool-to-burn-iso-image)

everything you posted is pointing to  codec's

---

### Post by khat33b on 2013-08-28
Already tried k3b. It also didn't recognize the DVD.
running wodim gives:

```


$ wodim --devices
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.


```

---

### Post by Rockman-X on 2013-08-28
Copy & Paste this into a terminal and please post the results:

cat /var/log/dmesg | egrep '(CD|DVD)'

---

### Post by SweetAurora on 2013-08-28
Hold the phone... Does anyone else see the "DVD-**RAM**" in the output? If that's the case, the drive only takes DVD-RAM disks. A technology that never caught on. Essentially beaten out by DVD-ROM. It can read CD's because most DVD-RAM drives supported CD-ROMS.

---

### Post by khat33b on 2013-08-29
```


$ cat /var/log/dmesg | egrep '(CD|DVD)' 
[    1.615690] ata5.00: ATAPI: HL-DT-STDVD+/-RW GT32N, A203, max UDMA/100
[    1.621721] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT32N    A203 PQ: 0 ANSI: 5
[    1.626293] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.626509] sr 4:0:0:0: Attached scsi CD-ROM sr0


```


> Hold the phone... Does anyone else see the "DVD-**RAM**" in the  output? If that's the case, the drive only takes DVD-RAM disks. A  technology that never caught on. Essentially beaten out by DVD-ROM. It  can read CD's because most DVD-RAM drives supported CD-ROMS.

It also says 
```
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
```

---

