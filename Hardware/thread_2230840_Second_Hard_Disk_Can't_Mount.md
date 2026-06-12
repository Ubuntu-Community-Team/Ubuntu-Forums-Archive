---
title: "Second Hard Disk: Can't Mount"
date: 2014-06-21
forum: Hardware
---

### Post by alevelwetskyh on 2014-06-21
Hi, I am a relatively new Ubuntu user (12.04) and having difficulty with a second internal hard disk drive. I have partioned it and everything seems OK. However I cannot access it. I've attached below the output of commands I think may be relevant. Any help is appreciated! 


sudo blkid; ls -l /media/
/dev/sda1: UUID="a6ef0937-81f3-480c-a22d-5eadcb56fd80" TYPE="ext4" 
/dev/sda5: UUID="75e2c841-72bc-4b5a-8714-cf7641f5b0ae" TYPE="swap" 
/dev/sdb1: LABEL="Stevenson2" UUID="7ba533b3-b4d6-4a70-8dd5-004d2ae24ce6" TYPE="ext4" 
total 4
drwxr-xr-x 3 root root 4096 Jul 16  2013 sdb1

ls -l /media
total 4
drwxr-xr-x 3 root root 4096 Jul 16  2013 sdb1


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=a6ef0937-81f3-480c-a22d-5eadcb56fd80  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=75e2c841-72bc-4b5a-8714-cf7641f5b0ae  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ext4  users,user           0  0

---

### Post by ajgreeny on 2014-06-21
First you need to make a mountpoint folder for the second disk either in /media or in /mnt.  If in /media it will always show in the places pane of nautilus or whatever file manager you use; if in /mnt it will not show, but it is really up to you.
```
sudo mkdir /media/disk2
```.  You now need to make that folder belong to you with ```
sudo chown user:user /media/disk2
```

Remove the final line in fstab that I assume you have added and add the second disk to your fstab file to mount it at boot with ```
gksudo gedit /etc/fstab
``` and at the end of the file add two lines
```
# /dev/sdb1 mounted as data disk
UUID=7ba533b3-b4d6-4a70-8dd5-004d2ae24ce6 /media/disk2 ext4 defaults, relatime 0 0
```
I think ubuntu now mounts ext4 partitions with the option relatime as default, but leave it in as it will not hurt to include it.
You can test the new fstab before you reboot with ```
sudo mount -a
``` and if there are no errors reported all is well, and the disk should now be mounted and available for you to read and write.

---

