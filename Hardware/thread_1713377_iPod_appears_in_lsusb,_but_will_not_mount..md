---
title: "iPod appears in lsusb, but will not mount."
date: 2011-03-24
forum: Hardware
---

### Post by peces on 2011-03-24
My 3rd Generation iPod nano used to automount just fine, but stopped one day.  Running lsusb produces this:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 05ac:1262 Apple, Inc. iPod Nano 3.Gen
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Yet it doesn't seem to have a device node.  I ran df and fdisk and no iPod.  Please help me.

---

### Post by cwa on 2011-03-24
if you grep for your ipod in dmesg.. does it bring back a device? (/dev/sdb1.. for example)

though you said there was no device node.

cwa

---

### Post by peces on 2011-03-24
Started up with my iPod attached. This is what  "dmesg | grep -i ipod" brings back:

[    6.235380] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0

No idea what this means.  Incidentally, I just discovered that gtkpod will recognize my iPod, but shows several error messages when starting and will not allow me to load any new music.  It claims that iPod mountpoint is /tmp/ipodagO1Ih.

---

### Post by cwa on 2011-03-24
can you run the mount command and post the output? what are the error messages with gtkpod?

bedtime soon.

cwa

---

### Post by peces on 2011-03-24
How do I run the mount command if there's no device node?  Every time i plug it in, gtkpod says the iPod  is at a different /tmp location.  For example, now it says it is at /tmp/ipodzP7apI.  Earlier it was at /tmp/ipodagO1Ih.  

Here is the complete dmesg log when I plug in my iPod:


[ 1863.010531] usb-storage: device found at 3
[ 1863.010538] usb-storage: waiting for device to settle before scanning
[ 1868.008354] usb-storage: device scan complete
[ 1868.023300] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1868.024782] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 1868.038081] sd 6:0:0:0: [sdc] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
[ 1868.039593] sd 6:0:0:0: [sdc] Write Protect is off
[ 1868.039604] sd 6:0:0:0: [sdc] Mode Sense: 68 00 00 08
[ 1868.039611] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1868.042321] sd 6:0:0:0: [sdc] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
[ 1868.042979] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1868.042992]  sdc: sdc1
[ 1868.046067] sd 6:0:0:0: [sdc] 950209 4096-byte logical blocks: (3.89 GB/3.62 GiB)
[ 1868.046868] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 1868.046876] sd 6:0:0:0: [sdc] Attached SCSI removable disk

When I load it in gtkpod, I get error messages like this:

iPod Database Import Failed: 'Illegal seek to offset 0 (length 4) in file '/tmp/ipodzP7apl/iPod_Control/iTunes/OTGPlaylistInfo'.'

I'm going to try plugging my iPod into another computer and doing a factory reset.

---

### Post by cwa on 2011-03-25
unless I am not following what you want to do, (I do not have an ipod myself)

can you mount /dev/sdc to a directory? example: mount /dev/sdc /mnt/ipod 
(create the ipod directory first => mkdir /mnt/ipod)

also, if you run mount by itself at the command prompt, it will list the mounts that are mounted. I was wondering if the claimed mount point of /tmp/ipodagO1Ih had a device attached to it. like /dev/sdc 
cwa

---

### Post by Damascushead on 2011-03-27
I had a very similar issue. I could see my ipod in lsusb but could not get it to mount. 

What I did ended up working for me, hopefully it can help you. in /media I had to make a directory for the ipod to mount to. i creatively named it ipod

```
sudo mkdir /media/ipod
```Then I had to open and edit /etc/fstab to tell it to mount the device at /media/ipod; by doing the following

```
sudo gedit /etc/fstab
```Then I added the line

**/dev/sdc1 /media/ipod vfat user,noauto,umask=000 0 0**

the first directory, /dev/sdc1, is where the ipod is recognized on my machine. It might be different on yours.

Save /etc/fstab and the try mounting the ipod
```

sudo mount /media/ipod
```This worked for me, so hopefully it gives you some insight.

Peace

---

