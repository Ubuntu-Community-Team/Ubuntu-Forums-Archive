---
title: "Problem with USB Flashdrive"
date: 2008-11-20
forum: Hardware
---

### Post by Oditius on 2008-11-20
I am still new, but thanks to the folks here, I got the fans running. Now to get to the second part. I plug in my ADATA 16gb flash drive (Fat32 format) and Ubuntu 8.10 doesn't see it. WHat can I do?

---

### Post by __Ryan__ on 2008-11-20
The device should show up as /dev/sd*.

Run this device first and take a look at the output.
```

ls -l /dev/sd*
```

Insert the drive and run the command again. Does a new device show up?

---

### Post by rstoya05-lx on 2008-11-20
I have a similar problem where USB drives do not automatically mount as they used to under 8.04. 

I found that I can still manually mount/unmount it but for some reason auto-mounting doesn't work.

---

### Post by Oditius on 2008-11-20
> **__Ryan__ said:**
> The device should show up as /dev/sd*.

Run this device first and take a look at the output.
```

ls -l /dev/sd*
```

Insert the drive and run the command again. Does a new device show up?

Doesn't look like it. It is formatted to Fat32 if that matters.


oditius@oditius-laptop:~$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2008-11-20 12:15 /dev/sda
brw-rw---- 1 root disk 8,  1 2008-11-20 12:15 /dev/sda1
brw-rw---- 1 root disk 8, 16 2008-11-20 12:15 /dev/sdb
brw-rw---- 1 root disk 8, 17 2008-11-20 12:15 /dev/sdb1
brw-rw---- 1 root disk 8, 18 2008-11-20 12:15 /dev/sdb2
brw-rw---- 1 root disk 8, 21 2008-11-20 12:15 /dev/sdb5
oditius@oditius-laptop:~$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2008-11-20 12:15 /dev/sda
brw-rw---- 1 root disk 8,  1 2008-11-20 12:15 /dev/sda1
brw-rw---- 1 root disk 8, 16 2008-11-20 12:15 /dev/sdb
brw-rw---- 1 root disk 8, 17 2008-11-20 12:15 /dev/sdb1
brw-rw---- 1 root disk 8, 18 2008-11-20 12:15 /dev/sdb2
brw-rw---- 1 root disk 8, 21 2008-11-20 12:15 /dev/sdb5
oditius@oditius-laptop:~$

---

### Post by boof1988 on 2008-11-20
> **Oditius said:**
> I am still new, but thanks to the folks here, I got the fans running. Now to get to the second part. I plug in my ADATA 16gb flash drive (Fat32 format) and Ubuntu 8.10 doesn't see it. WHat can I do?

Did you install Ubuntu 8.10 using a CD or a flash drive?  I have found that if I install using a USB-flash drive, then I have problems with mounting flash drives after install.  The fix I have found is to make a change to /etc/fstab.  If you used a USB-flash to install, I can help.

If you used a CD (and haven't fixed it yet), can you make sure the USB-flash is plugged in and post the output of each of the following:

```

sudo fdisk -l  #this prints the drives connected to the system whether they're mounted or not
sudo blkid     #this prints the drive partitions and UUIDs whether they're mounted or not
cat /etc/fstab #this will print the drives that mount as startup
```

These will not immediately fix the problem but will help with further troubleshooting.

---

### Post by Oditius on 2008-11-20
> **boof1988 said:**
> Did you install Ubuntu 8.10 using a CD or a flash drive?  I have found that if I install using a USB-flash drive, then I have problems with mounting flash drives after install.  The fix I have found is to make a change to /etc/fstab.  If you used a USB-flash to install, I can help.

No, I used the CD.

> **boof1988 said:**
> If you used a CD (and haven't fixed it yet), can you make sure the USB-flash is plugged in and post the output of each of the following:



These will not immediately fix the problem but will help with further troubleshooting.

And here is the results:




oditius@oditius-laptop:~$ sudo fdisk -l
[sudo] password for oditius: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6936ee62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9cc1f48

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23330   187398193+  83  Linux
/dev/sdb2           23331       24321     7960207+   5  Extended
/dev/sdb5           23331       24321     7960176   82  Linux swap / Solaris
oditius@oditius-laptop:~$ 
oditius@oditius-laptop:~$ 
oditius@oditius-laptop:~$ sudo blkid
/dev/sda1: UUID="461C5F5C1C5F4659" LABEL="Vista" TYPE="ntfs" 
/dev/sdb1: UUID="033fd096-7e50-40fc-aa27-6040c87bbaaf" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="5e4db252-da69-4a2a-aace-38e1fae4fadd" 
oditius@oditius-laptop:~$ 
oditius@oditius-laptop:~$ cat /etc/fstab

proc /proc proc defaults 0 0
UUID=033fd096-7e50-40fc-aa27-6040c87bbaaf / ext3 relatime,errors=remount-ro 0 1
UUID=5e4db252-da69-4a2a-aace-38e1fae4fadd none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda1 /media/Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
oditius@oditius-laptop:~$

---

### Post by boof1988 on 2008-11-20
Thanks for posting so quickly...  Since the USB is not showing up at all, it (for me) is a lot trickier.  I will look around a bit and see if I can find some more help...  I was really hoping it would be that same problem I've had, but it's not.

I'll snoop around a bit and see if I can find anything.  Maybe someone else will be able to help as well.

---

### Post by boof1988 on 2008-11-20
I found a thread with [this](http://ubuntuforums.org/showthread.php?t=972971#4) post.  It seems that if you plug in the drive, open a terminal and use the following to get the "tail" of "dmesg":

```
dmesg | tail
```

Following is the output of when I plugged a 1Gb USB and typed the command in Terminal (to give you an idea of what it might look like when the drive mounts successfully):

```
ubuntutest@ubuntutest-laptop:~$ dmesg | tail
[ 3844.062676] sd 2:0:0:0: [sdb] Write Protect is off
[ 3844.062684] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3844.062689] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3844.072298] sd 2:0:0:0: [sdb] 1974272 512-byte hardware sectors (1011 MB)
[ 3844.073297] sd 2:0:0:0: [sdb] Write Protect is off
[ 3844.073306] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3844.073311] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3844.073320]  sdb: sdb1
[ 3844.135055] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 3844.135144] sd 2:0:0:0: Attached scsi generic sg2 type 0
ubuntutest@ubuntutest-laptop:~$
```

I'm still looking around.

[COLOR="Blue"]EDIT: The post after taurus' says that they got a HAL update and it fixed their mount problem.[/COLOR]

---

### Post by Oditius on 2008-11-23
> **boof1988 said:**
> I found a thread with [this](http://ubuntuforums.org/showthread.php?t=972971#4) post.  It seems that if you plug in the drive, open a terminal and use the following to get the "tail" of "dmesg":


I'm still looking around.

[COLOR="Blue"]EDIT: The post after taurus' says that they got a HAL update and it fixed their mount problem.[/COLOR]

This is what I got, and I don't know what HAL is.

> oditius@oditius-laptop:~$ dmesg | tail
[  395.368346] usb-storage: device found at 3
[  395.368352] usb-storage: waiting for device to settle before scanning
[  400.368444] usb-storage: device scan complete
[  400.452146] eth1: no IPv6 routers present
[  405.980095] usb 7-1: reset high speed USB device using ehci_hcd and address 3
[  416.230251] usb 7-1: reset high speed USB device using ehci_hcd and address 3
[  432.472190] usb 7-1: reset high speed USB device using ehci_hcd and address 3
[  447.585102] usb 7-1: device descriptor read/64, error -110
[  462.800117] usb 7-1: device descriptor read/64, error -110
[  463.017104] usb 7-1: reset high speed USB device using ehci_hcd and address 3
oditius@oditius-laptop:~$ 



---

