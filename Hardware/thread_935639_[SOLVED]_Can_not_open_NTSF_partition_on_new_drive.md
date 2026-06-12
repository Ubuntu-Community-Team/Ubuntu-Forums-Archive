---
title: "[SOLVED] Can not open NTSF partition on new drive"
date: 2008-10-01
forum: Hardware
---

### Post by Gerard08 on 2008-10-01
I removed the drive from an USB external drive formatted for windows, and installed it in my all linux desktop running Hardy-Heron 8.04. The 2 NTSF partitions show up in the removable media, but when I try to mount them I receive an error message. I have a small collection of mp3 files I'd like to transfer but do not know how to access these partitions.  I have used gparted on this drive, and it also recognizes them but can't "access" them.
I installed NTSF-config, and when I tried to mount the partitions it simply closed without doing anything. Any help is appreciated.  Here's the fdisk readout:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cf54c30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2255    18113256    7  HPFS/NTFS
/dev/sda2            2256        9729    60034905    f  W95 Ext'd (LBA)
/dev/sda5            2256        5769    28226173+   7  HPFS/NTFS
/dev/sda6            5770        9008    26017236    b  W95 FAT32
/dev/sda7            9009        9729     5791401   83  Linux

---

### Post by SuperSonic4 on 2008-10-01
NTFS not NTSF ;)

Does using nautilus as root work? ```
gksudo nautilus
``` and then mount them?

If not you can try to force mount them[COLOR="Red"]***At your own risk!***[/COLOR] (I'm guessing it's sda1 and sda5)

```
sudo mount -t ntfs-3g /dev/sda1 /media/<drive label> -o force
```
```
sudo mount -t ntfs-3g /dev/sda5 /media/<drive label> -o force
```

where <drive label> is what you want it to appear as such as "Music", "Video" or just "Windows Drive" or "4G Media". If it's not sda1 or sda5 just change the number to the one you want.

---

### Post by Gerard08 on 2008-10-01
Yes, GkSudo Nautilus works OK. I still get the same message as before--

---

### Post by Victormd on 2008-10-01
The last time you used the drives with windows, did you shut them down properly? You said that it was an external HD, did you do a "safely remove device" or did you simply unplug it? If you simply unpluged it, you're going to need to either use a force mount switch (can't remember what it is but I know there is one) or hook your HD up in a windows comp., boot and shut down (this will release the HD)...

If you did shut it down properly, then the force mount switch should do the trick. I'm going to see if I can find it or if someone else jumps in...

EDIT: Just saw SuperSonic4's post with the force mount option... :)

---

### Post by Gerard08 on 2008-10-01
Right on! That's the detail-verbose part of the error message-- saying the drive was not removed properly.  I'm usually good about doing that on my windows laptop--but its conceivable that's what happened--I unplugged w/o removing the drive. Since I have installed the drive I'd prefer to force it--I have the music files burned to disk--so I could always retrieve the data.  I have a roomy case, so it's also possible to just remove the drive and reverse the process.

OK did force mount:

$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/sda1: No such file or directory

And this came up in NTSF-config

Mounting /media/Main Back-up _VOL2 failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/Main Back-up _VOL2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/Main Back-up _VOL2 ntfs-3g force 0 0

---

### Post by Victormd on 2008-10-01
> **Gerard08 said:**
> $LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/sda1: No such file or directory


You'll need to create the mountpoint:
```
sudo mkdir /media/sda1
```
and
```
sudo mkdir /media/sda5
```
(or whatever name you want to give it...)

Then force mount...

---

### Post by Gerard08 on 2008-10-01
OK Having trouble.  
gerard@desktop:~$ sudo mount -t ntfs-3g /media/sda5 /Main Back-up_VOL2 -o force

Here I used the existing label on the drive with the new mount point you gave me. See anything wrong?

I'm going to sleep. I'll check back tomorrow if you or anyone else can spot the trouble.  Thanks.

---

### Post by Victormd on 2008-10-01
> **Gerard08 said:**
> OK Having trouble.  
gerard@desktop:~$ sudo mount -t ntfs-3g /media/sda5 /Main Back-up_VOL2 -o force

Here I used the existing label on the drive with the new mount point you gave me. See anything wrong?

You're missing the drive name (i.e., /dev/sda1) and your volume name has spaces (this can be tricky but if you want to use it anyways, let me know):

Assuming that you've created the mountpoints (per my previous post), do:
```
sudo mount -t ntfs /dev/sda1 /media/sda1 -o force
```
and
```
sudo mount -t ntfs /dev/sda5 /media/sda5 -o force
```
(in Hardy you don't need to set the file system as ntfs-3g, you can use ntfs)

---

### Post by Gerard08 on 2008-10-02
Solved. I woke up this morning having stopped at the entry last night: ```
gerard@desktop:~$ sudo mount -t ntfs-3g /media/sda5 /Main Back-up_VOL2 -o force
```

I rebooted my computer this morning: I was able to open both of the ntsf partitions on this drive, with the file systems intact.  Here's the mount output:

```
gerard@desktop:~$ sudo mount
[sudo] password for gerard: 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
/dev/sda6 on /usr type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/gerard/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gerard)
/dev/sdb1 on /media/Secondary Storage_VOL1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb5 on /media/Main Back-up _VOL2_ type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```
I did create the mount points you recommended.  Maybe that was all that was needed after all? A bit of newbee luck?

Thanks to all. If anyone has time, I'd like to know what to write on the fstab file to make these mount at start up. And it sounds like the partition names should be renamed too. I've got tunes! :-)

---

### Post by SuperSonic4 on 2008-10-02
Doesn't ntfs-config automount ntfs drives for you? I use it to handle my Music drive so Amarok can open on startup :D

---

### Post by Gerard08 on 2008-10-02
OK, so I can leave out any entry in fstab, and when I need to make a play list just open the directory like I did this morning.  I wonder.. When I downloaded Ntsf-config last night I did not restart--I went directly to my mount problem--so really it wasn't so much the force-mount that worked?  Maybe the NTSF-config was all that was needed?

---

### Post by Victormd on 2008-10-02
I think it might have been a mix of both... :)
You did need to force mount it to release the "Windows-lock" over NTFS and once you did that (even though it didn't mount right away), when you restarted, the HD was unlocked and able to mount automatically...

---

