---
title: "auto-mounting ext4: confirmation on exacly what to write in fstab"
date: 2012-02-23
forum: Hardware
---

### Post by th1 on 2012-02-23
well, I finally realized that maybe I should't ask for help in a thread marked 'solved' lol

can someone help me out:

**sudo blkid -c /dev/null**
```
/dev/sda1: LABEL="Main Data" UUID="9A58141A5813F3AB" TYPE="ntfs" 
/dev/sda2: UUID="2eedf535-3598-410d-84d2-e28ff2928add" TYPE="ext2" 
/dev/sda3: UUID="987cebe9-f1c7-4043-9fd0-e77b7e103833" TYPE="swap" 
/dev/sda5: UUID="16943a4c-9c9c-4b4e-9c21-5c4ad4e3f6c9" TYPE="ext4" 
/dev/sda6: UUID="2f9b4f20-6c23-4fa4-a04a-4d686ee0aa24" TYPE="ext4" 
/dev/sdb1: UUID="a9b9b337-de93-432b-8108-7b9c7bfac549" TYPE="ext4" 
/dev/sdc1: LABEL="Dados" UUID="F80C3EF20C3EAC0E" TYPE="ntfs" 
/dev/sdc5: LABEL="What?" UUID="78FC5CC3FC5C7CF6" TYPE="ntfs" 
```**mount**
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /boot type ext2 (rw)
/dev/sda6 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tiago/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tiago)
/dev/sdc5 on /media/What? type fuseblk (rw,nosuid,nodev,allow_other,blksize=1024,default_permissions)

```**cat /etc/fstab**
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=16943a4c-9c9c-4b4e-9c21-5c4ad4e3f6c9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=2eedf535-3598-410d-84d2-e28ff2928add /boot           ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=2f9b4f20-6c23-4fa4-a04a-4d686ee0aa24 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=987cebe9-f1c7-4043-9fd0-e77b7e103833 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I'd like to make:
**/dev/sdb1: UUID="a9b9b337-de93-432b-8108-7b9c7bfac549" TYPE="ext4" **

auto-mount, so I can place all the music there (its an internal 40GB HDD) I formated it as ext4 using gparted

my understanding is that I need to do this: (but I'm afraid it might not  be quite it because I didn't named the drive 'MusicData' and I don't  konw if I should use "0" and "2" for step 2)

1- gksu gedit /etc/fstab
2- UUID=**a9b9b337-de93-432b-8108-7b9c7bfac549**   /media/**MusicData**    ext4    relatime    [COLOR=DarkOrange]**?    ?**[/COLOR]
3- sudo umount /dev/sdb1
4- sudo mkdir -p "/media/MusicData"
5- sudo mount -a

---

### Post by roelforg on 2012-02-23
Let me show you the line i added for my extra HD:
```

/dev/sdb1 /data ext4 defaults 0 1

```Doing:
drive /dev/sdb1 will be mounted on /data as an ext4 fs with default settings (should work out most of the times).
And it will be fsck'd every now and then.

---

### Post by Morbius1 on 2012-02-23
> I'd like to make:
**/dev/sdb1: UUID="a9b9b337-de93-432b-8108-7b9c7bfac549" TYPE="ext4" **

auto-mount, so I can place all the music there (its an internal 40GB HDD) I formated it as ext4 using gparted

my understanding is that I need to do this: (but I'm afraid it might not   be quite it because I didn't named the drive 'MusicData' and I don't   konw if I should use "0" and "2" for step 2)

1- gksu gedit /etc/fstab
2- UUID=**a9b9b337-de93-432b-8108-7b9c7bfac549**   /media/**MusicData**    ext4    relatime    [COLOR=DarkOrange]**?    ?**[/COLOR]
3- sudo umount /dev/sdb1
4- sudo mkdir -p "/media/MusicData"
5- sudo mount -aThere's nothing wrong with that statement except the ending. Just add a "0 2" to the ending:
```
UUID=a9b9b337-de93-432b-8108-7b9c7bfac549   /media/MusicData    ext4    relatime 0 2
```When you do the "sudo mount -a" it will tell you if you made any typos.

The last digit determines the relative frequency of a filesystem check at boot. A "0" turns it off, a "1" is usually reserved for the Linux OS partition, and a "2" is for data partitions like the one you are mounting.

Just remember that if this is a newly formatted partition you won't be able to write to it because by default it's owned by root with write access to root but read only access to everyone else. So you will have to take ownership of the partition **after it mounts**:
```
sudo chown your-name /media/MusicData
```

---

### Post by dandnsmith on 2012-02-24
I may be misinformed, but I seem to remember seeing that you shouldn't try to mount it under /media, as you'll be in a fight with the automount stuff for CDs, USBs ...
Make it anywhere else (I use /mnt/datax and so on), and the system will be happy.

---

### Post by Morbius1 on 2012-02-24
That should only become an issue if the CD or USB has a label that matches that mountpoint - in this case: MusicData. But if the USB does have that label it will automatically mount to **/media/MusicData_** which admittedly could be confusing to the user.

Mounting to /mnt does have the advantage of not producing a mount icon on the desktop however since mounting anything to your home folder or to /media produces an icon on the desktop automatically. Mouning it anywhere else does not.

---

### Post by th1 on 2012-02-24
I got it working! thanks!

---

