---
title: "usb flash drive won't mount"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by davidgarcin on 2006-10-22
I've got a Corsair Flash Voyager 2GB.  It's formatted as FAT32, and works in XP just fine.  However, I can't get it to mount in Dapper.

If I try mounting it, I get this:
```
root@Dave:~# mount -t vfat /dev/sdc1 /media/usbdrive
mount: /dev/sdc1: can't read superblock

```

I've tried rebooting linux with it plugged in, same results.  If I run tail -n 0 -f /var/log/messages, and then plug it in, I get the following:
```

david@Dave:~$ tail -n 0 -f /var/log/messages
Oct 22 00:21:52 localhost kernel: [17181826.260000] usb 5-3: new high speed USB device using ehci_hcd and address 7
Oct 22 00:21:52 localhost kernel: [17181826.404000] hub 5-3:1.0: USB hub found
Oct 22 00:21:52 localhost kernel: [17181826.404000] hub 5-3:1.0: 1 port detected
Oct 22 00:21:52 localhost kernel: [17181826.708000] usb 5-3.1: new high speed USB device using ehci_hcd and address 8
Oct 22 00:21:52 localhost kernel: [17181826.812000] scsi5 : SCSI emulation for USB Mass Storage devices
Oct 22 00:21:57 localhost kernel: [17181831.812000]   Vendor: Corsair   Model: Flash Voyager     Rev: 1.00
Oct 22 00:21:57 localhost kernel: [17181831.812000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Oct 22 00:21:57 localhost kernel: [17181831.812000] SCSI device sdc: 4063232 512-byte hdwr sectors (2080 MB)
Oct 22 00:21:57 localhost kernel: [17181831.816000] sdc: Write Protect is off
Oct 22 00:21:57 localhost kernel: [17181831.820000] SCSI device sdc: 4063232 512-byte hdwr sectors (2080 MB)
Oct 22 00:21:57 localhost kernel: [17181831.824000] sdc: Write Protect is off
Oct 22 00:21:57 localhost kernel: [17181831.824000]  sdc: sdc1
Oct 22 00:21:57 localhost kernel: [17181831.824000] sd 5:0:0:0: Attached scsi removable disk sdc
Oct 22 00:21:57 localhost kernel: [17181831.824000] sd 5:0:0:0: Attached scsi generic sg3 type 0
Oct 22 00:21:57 localhost kernel: [17181832.044000] end_request: I/O error, dev sdc, sector 4063008
Oct 22 00:21:57 localhost kernel: [17181832.044000] printk: 137 messages suppressed.
Oct 22 00:21:57 localhost kernel: [17181832.092000] end_request: I/O error, dev sdc, sector 4063008
Oct 22 00:21:57 localhost kernel: [17181832.092000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:57 localhost kernel: [17181832.096000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:57 localhost kernel: [17181832.096000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:57 localhost kernel: [17181832.100000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:57 localhost kernel: [17181832.100000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:57 localhost kernel: [17181832.104000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:57 localhost kernel: [17181832.104000] end_request: I/O error, dev sdc, sector 4063168
Oct 22 00:21:57 localhost kernel: [17181832.104000] end_request: I/O error, dev sdc, sector 4063168
Oct 22 00:21:57 localhost kernel: [17181832.108000] end_request: I/O error, dev sdc, sector 4063216
Oct 22 00:21:57 localhost kernel: [17181832.108000] end_request: I/O error, dev sdc, sector 4063216
Oct 22 00:21:57 localhost kernel: [17181832.108000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:57 localhost kernel: [17181832.112000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:57 localhost kernel: [17181832.112000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.116000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.120000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.120000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.120000] end_request: I/O error, dev sdc, sector 104
Oct 22 00:21:58 localhost kernel: [17181832.124000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.128000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.132000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.136000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.140000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.144000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.144000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.160000] end_request: I/O error, dev sdc, sector 4063008
Oct 22 00:21:58 localhost kernel: [17181832.164000] end_request: I/O error, dev sdc, sector 4063008
Oct 22 00:21:58 localhost kernel: [17181832.164000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:58 localhost kernel: [17181832.164000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:58 localhost kernel: [17181832.168000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.172000] end_request: I/O error, dev sdc, sector 4063224
Oct 22 00:21:58 localhost kernel: [17181832.172000] end_request: I/O error, dev sdc, sector 4063168
Oct 22 00:21:58 localhost kernel: [17181832.172000] end_request: I/O error, dev sdc, sector 4063168
Oct 22 00:21:58 localhost kernel: [17181832.176000] end_request: I/O error, dev sdc, sector 4063216
Oct 22 00:21:58 localhost kernel: [17181832.176000] end_request: I/O error, dev sdc, sector 4063216
Oct 22 00:21:58 localhost kernel: [17181832.176000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.180000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.184000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.184000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.188000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.188000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.188000] end_request: I/O error, dev sdc, sector 104
Oct 22 00:21:58 localhost kernel: [17181832.192000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.196000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.200000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.204000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.208000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost last message repeated 2 times
Oct 22 00:21:58 localhost kernel: [17181832.212000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.212000] end_request: I/O error, dev sdc, sector 32
Oct 22 00:21:58 localhost kernel: [17181832.216000] end_request: I/O error, dev sdc, sector 0
```

That will go on if I let it.  A little help, please?
Thanks,
-Dave

---

### Post by randomnumber on 2006-10-22
First thing I would do is
# mount
this list all mounts. It is possible that the drive is mounted.

---

### Post by davidgarcin on 2006-10-22
Thanks for your reply.  I tried it and got this:
```
david@Dave:~$ mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/sda1 on /media/windows type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda3 on /media/files type vfat (rw,utf8,umask=007,gid=46)
/dev/sdb1 on /media/stuff type vfat (rw,noexec,nosuid,nodev,sync,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb5 on /media/BACKUP type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

As far as I can tell, it's not mounted.  It does however show up under the Device Manager.

---

### Post by randomnumber on 2006-10-22
I am still learning.

It may be that it got mounted at a different folder then /media/usbdisk

This is how my output of mount looks like
erik@ubuntu:/proc/bus/usb$ mount
/dev/hda1 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-686/volatile type tmpfs (rw)
/dev/hda5 on /media/hda5 type vfat (rw,iocharset=utf8,gid=1002,umask=0007)
/dev/hda6 on /media/hda6 type vfat (rw,iocharset=utf8,gid=1002,umask=0007)
/dev/hda7 on /media/hda7 type vfat (rw,iocharset=utf8,gid=1002,umask=0007)
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

The following line is the usb drive
/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

Just so you know it can be setup to mount the usbdisk almost anywhere with any name. The Folder does not have to be named usbdisk.

---

### Post by randomnumber on 2006-10-22
apparently "f 8 )" make a smiley face f8). Sure that adds to the confusion.

---

### Post by davidgarcin on 2006-10-22
sda is the hard disk in my laptop, and sdb is an external hard drive.  Both are mounting correctly, and my flash drive contents definitely can't be accessed at those mount points, if that's what you mean, only what's on those particular partitions.  Correct me if I'm misunderstanding you though.

I don't think it's a problem of the usb drive mounting at some unknown place.  On occasion it will show up in Nautilus under 'Computer' as Corsair Flash Media, and if I right-click mount it, it gives some generic error messages.  It doesn't seem to mount at all, even if I explicitly add a line in fstab and boot with the drive plugged in.

I'm aware of the ability to mount drives anywhere - that's why I've customized fstab to mount my drives in folders with folder names other than sd**.  I could never remember which partition was which.  Thanks for the tip though.

---

### Post by randomnumber on 2006-10-22
I just relized that your drive was /dev/sdc. Please ignore what I said before.


You could do a gui thing and go to System -> Administration -> Disks
   There you be able to see all availble drives, including the usb drive. It   may be a formating issue. If it I would backup all the data to the windows machine and reformat in linux. If it is not there You may need a more advanced user to help.

---

### Post by randomnumber on 2006-10-22
I dont know how to delete messages.

---

### Post by davidgarcin on 2006-10-22
Uhhhhh..... wrong thread?

Getting back to the topic at hand....

That's sort of what I was thinking as well - that it's a formatting issue.  I've tried reformatting with Windows before, to no avail.  This time I tried reformatting with gParted, the Disks utility, AND the Corsair utility.  gParted and the Disks utility can't reformat it because they can't access it for some reason.  /dev/sdc shows up in both of them, but when I try to reformat it doesn't actually do anything (as evidenced by my data still being there when I boot up windows).  Does a disk have to be mounted for it to be formatted?

Thanks for your suggestions.

---

### Post by randomnumber on 2006-10-22
Formating at command line I just use fdisk.

[INDENT]
sudo fdisk /dev/sdc

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
Command (m for help): p

Disk /dev/sdb: 260 MB, 260046848 bytes
16 heads, 32 sectors/track, 992 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         991      253680    b  W95 FAT32

Command (m for help):
[/INDENT]

fdisk is a commonly used application used by many. Notice that there is no number at the end of sdc.

---

### Post by davidgarcin on 2006-10-22
fdisk is good to know.  However, I get similar results:

```
root@Dave:~# fdisk /dev/sdc

Unable to read /dev/sdc

```

---

### Post by srf21c on 2006-11-10
David, I'm having the same problems with a 4GB Corsair Flash Voyager on a fresh install of Edgy 6.10.   Same mess O' I/O errors in dmesg/syslog, same problems with disk utilities such as gparted being able to read or manipulate the partition table.  I wonder if this is a bug specific to the Corsair flash media, or maybe just large capacity USB flash drives in general....highly annoying.

---

### Post by davidgarcin on 2006-11-10
yeah, it's weird, I know.  I've done a bit of looking on the Corsair forums and haven't been able to find much.  Let me know if you solve it though, and I'll do likewise.

---

### Post by srf21c on 2006-11-10
Sounds like a plan.  I'm going to do some digging on this issue at linuxquestions.org as well.

---

### Post by chiisu on 2007-01-19
Also having trouble mounting a usb hard drive (WD 80GB) in Edgy  :(

---

