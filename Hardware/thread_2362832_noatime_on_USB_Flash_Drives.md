---
title: "noatime on USB Flash Drives"
date: 2017-06-02
forum: Hardware
---

### Post by Zauber Paracelsus on 2017-06-02
I have a USB flash drive that is formatted with the ntfs filesystem.  Currently when it is automounted, it is mounted with the relatime option.

I wish to change it so that it is automounted with the atime option.  Among other things, I use this flash drive to perform backups of my files, and usually do so once or twice a week.  Because of this, relatime hurts writing speed because the time between writes is usually well over a day.

How do I do this?  I am assuming I need to add a custom rule to /etc/udev/rules.d ?

---

### Post by oldfred on 2017-06-02
NTFS is not as fast as it is not a native file system. Are you using USB3 flash drive even if USB2 port. I found about 10% faster on my old system that only has USB2 ports. And brand of flash drive can make a huge difference.
Might be easier just to unmount and use an rsync script that also includes a mount.

This is my mount, but this one is to an internal ext4 partition:

```
my_mount="/mnt/backup"

# ! not - moved to install script
#if [ ! -d /mnt/backup ]; then
#     mkdir /mnt/backup
#fi
 
#mount -t ext4 /dev/sdb5 /mnt/backup


if grep -qs "$my_mount" /proc/mounts; then
  echo "It's mounted."
else
  echo "It's not mounted."
  mount -t ext4 /dev/sdb5 $my_mount
  if [ $? -eq 0 ]; then
   echo "Mount success!"
  else
   echo "Something went wrong with the mount..."
   exit $?
  fi
fi
```

And I exclude a lot of cache, temporary or other misc files that are not required.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[URL="http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997"]http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997

[/URL]
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites) 

[URL="http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997"]
[/URL]

---

### Post by Zauber Paracelsus on 2017-06-03
I tried the mounting trick, but had trouble with ownership (it kept going to root instead of user).  I eventually got it right, but then ran the find command to see if I had any files larger than 4gb.  I didn't, so I just reformatted my flash drive to vfat.

As for the USB drive itself, it's [this one]("https://www.amazon.com/SanDisk-Ultra-256GB-Flash-SDCZ48-256G-U46/dp/B00YFI1A66").  And yeah, the USB port it is plugged into is USB 3.0.

EDIT: And yes, the USB drive is USB 3.0

---

### Post by oldfred on 2017-06-03
If NTFS or FAT32 it will always be root as they do not support Linux style ownership & permissions.
 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion. 


Generally better to use NTFS if partition is larger. If if only for Ubuntu use ext4.
FAT32 ok for smaller partition, but FAT32 has both file size limit, but no journal. Without journal running chkdsk or dosfsck can take a lot longer or may not be able to recover from errors.

---

