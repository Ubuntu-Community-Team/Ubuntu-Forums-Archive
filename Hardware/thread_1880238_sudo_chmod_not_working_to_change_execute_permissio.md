---
title: "sudo chmod not working to change execute permissions!"
date: 2011-11-13
forum: Hardware
---

### Post by saiganeshb on 2011-11-13
Hi,
I recently installed ubuntu 11.04 and I am trying to install matlab into a separate directory in a drive (separate from my ubuntu installation). (See attached screenshot.png). I decided to work on a simpler problem by writing a small line in a script to see if it'll execute. But this failed too (Check screenshot-1.png)

From what I've searched around, I guess there is some 'noexec' -> 'exec' conversion solution for some problems, but I am not sure if that'll work with my laptop. I am getting the same result, even after re-installing ubuntu 11.04 multiple times. 

The following are the contents of my /etc/fstab and /etc/mtab files. Request someone to respond quickly as i need an urgent solution. Thanks for your help!

output of /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ec30680f-350a-4c07-a3ac-6706d48aaef3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=8aae1921-0398-4b87-bc76-16fd8ea509a6 none            swap    sw              0       0


```output of /etc/mtab:
```

/dev/sda7 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/saiganesh/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=saiganesh 0 0
/dev/sda5 /media/driveD fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0

```

---

### Post by Morbius1 on 2011-11-13
[1] You cant chmod an ntfs partition since there are no linux permissions "bits" to set on a Windows filesystem.

[2] It appears you are mounting "driveD" through Nautilus or Places since by default it will mount with permissions for you to read / write but not execute any of the files within it. Your solution is to mount the partition with the permissions you want it to have:

[a] Run the following command to get the right UUID number for /dev/sda5:
```
sudo blkid -c /dev/null
```[b] Unmount the partition:
```
sudo umount /media/driveD
```[c] Create a permanent mount point:
```
sudo mkdir /media/driveD
```[d] Add the following line to /etc/fstab:
```
UUID=DA9056C19056A3B3 /media/driveD ntfs    defaults,nls=utf8,umask=000,uid=1000,windows_names 0       0
```[COLOR=Blue]*Substitute the UUID number you got from step [a] in the above line*[/COLOR]

[e] Run the following command which will test for errors and if there are none mount the partition without a reboot:
```
sudo mount -a
```

---

### Post by saiganeshb on 2011-11-13
@morbius1 Thanks a lot!! That worked perfectly :) 

quick noob questions:
1. What's the difference between changing /etc/fstab and /etc/mtab? (since there was an entry for driveD in my mtab file initially). I am assuming that the mtab file changes dynamically while the fstab file doesn't?

2.Now all my files on driveD has 777 permissions! (I might have tried sudo chmod 777 -R /media/driveD out of frustration at some point before posting on this forum). Is there a neat way to restore permissions or am I stuck with this?

3. I hope that this doesn't affect how I access my driveD files from windows 7 (this is a dual boot laptop)

---

### Post by Morbius1 on 2011-11-13
[1] mtab lists all currently mounted filesystems where fstab lists all available or a subset of those available ( for example external usb drives are usually not defined in fstab).

[2] A "chmod -R 777 /media/driveD" before the partition was mounted or after the partition was mounted would have done nothing. Whatever you do to a mount point before the mount is replaced by the mount itself - that's true for both Windows and Linux filesystems. And you can't do a chmod to a Windows filesystem after a mount.

There was a sense or urgency in your original post so I set the permissions to be wide open. You can change that using the option you already have in fstab: **umask**

Each position of that option refers to a different user:

1st posisiton = the owner of the partition ( in this case it's you since I set uid=1000 which is you )
2nd posisition = group
3rd posistion = everyone else.

The value of each digit represents the permissions that you want to remove from the default of 777:

0 - takes away nothing
1 - takes away execute
2 - takes away write
4 - takes away read

And they're additive so a 7 ( 1+2+4 ) takes way all permissions. So to return this partition to it's original state except with execute permissions you would make umask equal to 077:
```
 UUID=DA9056C19056A3B3 /media/driveD ntfs    defaults,nls=utf8,umask=077,uid=1000,windows_names 0       0
```[3] A mount in Linux of an NTFS partition is is a "view" of that partition with ownership and permissions that are in place only as long as it's mounted. Once you shut down or reboot the mount is released and Windows is none the wiser.

---

