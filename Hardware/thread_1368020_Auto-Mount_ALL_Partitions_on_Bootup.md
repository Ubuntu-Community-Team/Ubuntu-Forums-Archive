---
title: "Auto-Mount *ALL* Partitions on Bootup"
date: 2009-12-30
forum: Hardware
---

### Post by mattclements on 2009-12-30
Hello all,
Right - I will explain what I need, and then why for those that wish to know a reason.

I would like Ubuntu to automatically detect *ALL* Hard Drives (SATA) plugged into the PC I am working on, and mount them as /media/whatever.

This happens with IDE drivers currently plugged in to a USB Adapter, but not SATA Drives plugged into the board directly (obviously before the PC is powered on).

The reason for this is we are using the machine as an Anti-Virus machine for a PC Repair Shop. The script will look at all partitions mounted in /media/* and scan them, cleaning any viruses off the Disk.

Regards,
Matt

---

### Post by mattclements on 2010-01-10
Bump! Anyone?

---

### Post by jocko on 2010-01-10
Open up a terminal and run these commands, then post the output of each command in this thread:
```
cat /etc/fstab
```
```
sudo fdisk -l
```
```
sudo blkid

```

---

### Post by mattclements on 2010-01-11
With the standard setup (No Extra Drives Plugged In)

```
antivirus@Plankton:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2c539b80-0e6b-46c2-85c4-3f311460b23a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=41991f6f-b4e5-4c50-b8f3-96bd13ca8e26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

```
antivirus@Plankton:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4403bd1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9824    78911248+  83  Linux
/dev/sda2            9825       10011     1502077+   5  Extended
/dev/sda5            9825       10011     1502046   82  Linux swap / Solaris
```


```
antivirus@Plankton:~$ sudo blkid
/dev/sda1: UUID="2c539b80-0e6b-46c2-85c4-3f311460b23a" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="41991f6f-b4e5-4c50-b8f3-96bd13ca8e26"
```

---

### Post by mattclements on 2010-01-11
With a 2nd Hard Drive Plugged In (SATA - For an AV Scan)

```
antivirus@Plankton:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2c539b80-0e6b-46c2-85c4-3f311460b23a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=41991f6f-b4e5-4c50-b8f3-96bd13ca8e26 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

```
antivirus@Plankton:~$ sudo fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71320d70

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4403bd1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9824    78911248+  83  Linux
/dev/sdb2            9825       10011     1502077+   5  Extended
/dev/sdb5            9825       10011     1502046   82  Linux swap / Solaris

```

```
antivirus@Plankton:~$ sudo blkid
/dev/sda1: UUID="CAE0552AE0551DCF" TYPE="ntfs" 
/dev/sdb1: UUID="2c539b80-0e6b-46c2-85c4-3f311460b23a" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="41991f6f-b4e5-4c50-b8f3-96bd13ca8e26" 

```

Regards,
Matt

---

### Post by jocko on 2010-01-11
Ok. So you use your sata drive as a removable drive? I'm not sure how this will work when the drive is unplugged, but try this.
First make a folder where you want to mount the partition:
```
sudo mkdir /media/[COLOR=Red]foldername[/COLOR]
```Then add a line for mounting that partition in fstab:
```
gksudo gedit /etc/fstab
```Add the following line to the end of the file:

```
UUID=[COLOR=Blue]CAE0552AE0551DCF[/COLOR] /media/[COLOR=Red]foldername[/COLOR]        ntfs defaults,nls=utf8,umask=007,gid=46 0       1
```"[COLOR=Red]foldername[/COLOR]" has to be the same as the name of the folder you created above.
To mount it immediately, type:
```
sudo mount -a
```Reboot both with the drive connected and disconnected to make sure everything works fine.
If you have more drives you have to repeat the process for each partition, getting the correct UUID for each from the output of "sudo blkid". Also remember that if you format the partition it will get a new UUID, so you need to change fstab again. [More help and good tips here.]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by estyles on 2010-01-11
If I understand the question correctly, then the answer given is not going to help you.  The idea is to automatically mount all partitions, regardless of how many there are, and not to have to manually add entries to fstab every time you want to do it.

I can't give you a full answer, but I think I can outline the steps you'll need to take.

First off, you're going to have to do it with a shell script.  Ideally, we need that shell script to execute with root privileges - I'm not entirely sure how to do that.  You might be able to get around this by prefixing the command with sudo, but I'm not sure how that interacts with a shell script that is executing on login - will it stop to ask for your password?  That would be annoying...

The script should do an fdisk -l, then attempt to mount all drives that it finds there.  The command will be something like the following: "sudo fdisk -l | grep -oG /dev/sd.[0-9][0-9]* | mount".  I'm not sure about the commandline for mount, so you might have to look that up...  The part of the grep command that says "[0-9][0-9]*" should really be [0-9]+, but for some reason I couldn't get that to work on the commandline.

You then need to add this shell script to your startup applications (there's a menu in System->Preferences), so that it runs on startup.

---

### Post by mattclements on 2010-01-11
That sounds perfect to me estyles! When scanning the drive we call a shell script using Sudo so I can include it there - any more ideas of the code to grep & mount etc?

Regards,
Matt

---

### Post by estyles on 2010-01-12
the grep code seems to work - the mount command does not.

I'm not sure there's a way to automatically mount without creating the mount points first (I'd hoped there was something like "mount --justmountitplease" that would mount like the GUI mounting in Gnome that I believe creates a directory in media and then mounts it there with read-write permissions).

So, you might have to write a more in-depth shell script.  Frex, take the output from the fdisk | grep thing (which outputs all attached harddrives, one per line), then iterate through it, creating a directory in media (edit: you should probably mount it in /mnt, not /media) for each one and then calling a mount command on each one.  I.e. a loop rather than a single line command.

You might also want to avoid mounting the drives that are already mounted, but that might not be necessary depending on what you intend to do with the mounted drives.  (edit: if the main harddrive is always detected as /dev/sda, then you can change the grep command to: grep -oG /dev/sd[b-z][0-9][0-9]*, and it won't have partitions from sda in the list, but from your fdisk outputs, it looks like when you mounted a second drive, the first one got pushed down to sdb...)

Anyway, the shell script involved is a little beyond my on-hand knowledge, and I don't really have the time to research it, but it should definitely be possible and not incredibly difficult if you read up on shell scripting a bit.

---

### Post by verzonnen on 2010-01-22
Here is a simple script that might be what you are looking for, I used some of the suggestion from the other in here, I hope this works for you.  It does require to be run as root, so make sure there is nothing in there that can destroy your system.

BASEDIR="/mnt"

for PARTITION in `fdisk -l | grep -v swap | egrep -o /dev/sd.[0-9]+` ; do
  mount | grep -q "^$PARTITION"
  if [ $? -eq 1 ] ; then
    blkid $PARTITION > /dev/null
    if [ $? -eq 0 ] ; then
      MOUNTPOINT=$BASEDIR/`echo $PARTITION | egrep -o sd.[0-9]+`
      mkdir -p $MOUNTPOINT
      mount $PARTITION $MOUNTPOINT
    fi
  fi
done
exit 0

---

