---
title: "Issues with NTFS Config Tool"
date: 2012-03-23
forum: Hardware
---

### Post by subvertc on 2012-03-23
I have issues mounting my Seagate external.

It was working just fine for months, until I installed NTFS Configuration Tool and executed the program. 

Ever since then, my XHD will not mount properly.

A new icon for the drive appears on my desktop every time I need to shut down and relocate (laptop. There are three now. Only the most recent icon works properly (can unmount and read/write) but the other two do nothing. If I open them, a empty window appears, with zero files. If I try and unmount, i get this:

[IMG]http://i.imgur.com/xsEP9.png[/IMG]

If i restart, restart is delayed by the drive being "not found".

Here is the same XHD mounted three times according to my screenlet:

[IMG]http://i.imgur.com/xhbxL.png[/IMG]

And same issue in gmusicbrowser:

[IMG]http://i.imgur.com/3cqv9.png[/IMG]

Here are the devices listed by UUID

```
/dev/sda1: UUID="9956352b-1e14-4db6-a704-543a03d1af0d" TYPE="ext4" 
/dev/sda5: UUID="e08e4f99-ece6-440f-8c53-dd4eb909b7b6" TYPE="swap" 
/dev/sdd1: LABEL="Codex Malleus Diabolicus" UUID="E8404B27404AFC36" TYPE="ntfs"
```

I have used gconf-editor  to ensure it is set to automount, as well as Mount Manager to try and solve the root issue. I have also tried fixing the problem using the NTFS Config Tool.

Im stumped. :confused:

---

### Post by coffeecat on 2012-03-23
> **subvertc said:**
>  as well as Mount Manager to try and solve the root issue. I have also tried fixing the problem using the NTFS Config Tool.


First, I suggest you uninstall both of those, both of which have been unmaintained for years. Also - please avoid installing any other mounting apps. I know of not a single one I would trust. If there is a trustworthy one I would like to hear of it.

Post the output of these commands...

```
cat /etc/fstab
sudo blkid
ls -l /media
sudo fdisk -lu
mount

```

(You can highlight the output and then right-click to copy for pasting into your post - better than typing it out.) It sounds as though you have a bad /etc/fstab line created by ntfs-config. It should be possible to sort this out with the information from those outputs.

Which version of Ubuntu are you using?

**EDIT**: if you have the app usbmount installed - uninstall it.
**EDIT2** - if you have the app pysdm installed - uninstall it. :wink:

---

### Post by subvertc on 2012-03-23
> First, I suggest you uninstall both of those, both of which have been unmaintained for years.

Ok I removed both programs. 

And here is the output:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda1 :
UUID=9956352b-1e14-4db6-a704-543a03d1af0d	/	ext4	defaults	01
#Entry for /dev/sdd1 :
UUID=E8404B27404AFC36	/media/Codex_Malleus_Diabolicus	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=e08e4f99-ece6-440f-8c53-dd4eb909b7b6	swap	swap	sw	0	0

```

---

### Post by coffeecat on 2012-03-23
> **subvertc said:**
> 
And here is the output:


There were four other outputs requested. In fact, you've already given what seems to be the output of blkid, but it would be useful to see the rest. The fstab line that ntfs-config generated looks OK, so I'd like to see if there is a reason for the rest of your problems.

***And***:

> **coffeecat said:**
> 
Which version of Ubuntu are you using?


---

### Post by subvertc on 2012-03-23
```
/dev/sda1: UUID="9956352b-1e14-4db6-a704-543a03d1af0d" TYPE="ext4" 
/dev/sda5: UUID="e08e4f99-ece6-440f-8c53-dd4eb909b7b6" TYPE="swap" 
/dev/sdd1: LABEL="Codex Malleus Diabolicus" UUID="E8404B27404AFC36" TYPE="ntfs"
```

```
 ls -l /media
total 80
drwxrwxrwx 1 root root 16384 2012-02-08 10:49 Codex Malleus Diabolicus
drwxrwxrwx 1 root root 16384 2012-02-08 10:49 Codex Malleus Diabolicus_
drwxrwxrwx 1 root root 16384 2012-02-08 10:49 Codex_Malleus_Diabolicus
lrwxrwxrwx 1 root root     4 2010-11-30 23:12 usb -> usb0
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb0
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb1
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb2
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb3
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb4
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb5
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb6
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb7

```

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00025dbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   469968895   234983424   83  Linux
/dev/sda2       469970942   488396799     9212929    5  Extended
/dev/sda5       469970944   488396799     9212928   82  Linux swap / Solaris

Disk /dev/sdd: 1500.3 GB, 1500301908992 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5e2d0374

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  2930272064  1465136001    7  HPFS/NTFS

```

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/Codex Malleus Diabolicus type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/maitiu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=maitiu)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/Codex Malleus Diabolicus_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/Codex_Malleus_Diabolicus type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

> Which version of Ubuntu are you using?

11.04

---

### Post by coffeecat on 2012-03-23
From the evidence in your various outputs, it seems that you have managed to get into quite a hole. I will try to help you get out, but one or two things do not add up.

First, from your ls -l /media output:

```
lrwxrwxrwx 1 root root     4 2010-11-30 23:12 usb -> usb0
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb0
drwxr-xr-x 2 root root  4096 2010-11-30 23:12 usb1

... and so on
```

You installed usbmount, didn't you? Have a look at my earlier post. Uninstall it now. It is not designed for GUI systems and is only making matters worse. Also - are there any apps for mounting usb drives apart from ntfs-config, mount manager, usbmount and pysdm that you have installed? If so, please uninstall them.

Next, also from your "ls -l /media output":

```
drwxrwxrwx 1 root root 16384 2012-02-08 10:49 Codex Malleus Diabolicus
drwxrwxrwx 1 root root 16384 2012-02-08 10:49 Codex Malleus Diabolicus_
drwxrwxrwx 1 root root 16384 2012-02-08 10:49 Codex_Malleus_Diabolicus
```

Three similar mountpoints, which may explain the mutliple icons on your desktop. Also, this from the mount output which I do not understand:

```
/dev/sdc1 on /media/Codex Malleus Diabolicus_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd1 on /media/Codex_Malleus_Diabolicus type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```

/dev/sdd1 seems to be your external NTFS drive, but what is /dev/sdc1? It is not listed in your fdisk output, nor in the output of blkid. Did you have another device plugged in when you ran mount which was not plugged in when you ran the other commands?

Whatever, I suggest we try to restore your system to a default state so that automounting of external drives works in the way in which it is intended.

Step 1 - uninstall all superflous mounting apps as I have mentioned.

Step 2 - edit /etc/fstab. Run this command:

```
gksu gedit /etc/fstab
```

Now change this line:

```
#Entry for /dev/sdd1 :
UUID=E8404B27404AFC36	/media/Codex_Malleus_Diabolicus	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
```

To this:

```
#Entry for /dev/sdd1 :
#UUID=E8404B27404AFC36	/media/Codex_Malleus_Diabolicus	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
```

Simply add a hash symbol (#) before "UUID". Save and exit gedit.

Step 3 - remove all superfluous mountpoints. Run these two commands:

```
sudo rm /media/Codex*
sudo rm /media/usb*
```

Be very careful with those two commands. A typo could be destructive. It would be best to copy and paste them.

Step 4. Reboot.

Once you have rebooted, what happens when you plug your Seagate drive in? I cannot guarantee that this will work (yet) because not everything is explained. It is just possible that you have installed mounting apps which write udev rules. If so, we will need to investigate further.

---

### Post by subvertc on 2012-03-23
I removed usbmount, imputed the commands you mentioned, and rebooted.

Worked like a charm, back to normal.

---

