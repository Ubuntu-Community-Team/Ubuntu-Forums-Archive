---
title: "Can't Delete From Hard Drive"
date: 2010-02-11
forum: Hardware
---

### Post by Naro on 2010-02-11
I was transferring files from one external HDD to another external when my power went out.  When the power came back on, the files on the HDD I was transferring to are now unable to be deleted.  Does anybody have any idea what happened and how to fix it? Thanks.

---

### Post by amac777 on 2010-02-11
Probably some data corruption on the drive due to the sudden power outage. I'd recommend you run 'fsck' to check for (and repair) errors on the drive.

To run fsck, you need to first figure out what external drive it is. I'd suggest making sure the drive is plugged in and mounted and then type:

```
mount
```

You can use that information to figure out which drive. For example, on my computer, the external drive is /dev/sdb1. On your system, it may be different. After you figure out which drive it is, do these commands to unmount that drive and then run fsck (change /dev/sdb1 to your drive's location):

```
sudo umount /dev/sdb1
sudo fsck /dev/sdb1

```

---

### Post by Naro on 2010-02-11
This is what I get when I try to so sudo umount:

```
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by amac777 on 2010-02-11
From that error message it looks like the hard drive you want to check contains the / directory for your system. Assuming that is true, you won't be able to un-mount that drive. It must be checked at system start up. To do so, first, edit your fstab file:

```
sudo nano /etc/fstab
```

and make sure the last digit on the / entry is a 1. For example, in mine it looks something like this: (I've highlighted the important 1 in red)

```
UUID=9asd99fds-33334234323234 / ext3 relatime,errors=remount-ro 0 [COLOR="Red"]1[/COLOR]

```
Then, force fsck to run on the next system startup:

```
sudo touch /forcefsck
```

Lastly, reboot your computer and it should check the root drive for errors.

Edit: If you find you can't save the fstab file or create the /forcefsck because the drive is mounted read-only (due to errors), try running this command first to give yourself write access and then do the above changes:

```
sudo mount -o remount,rw /
```

---

### Post by Naro on 2010-02-11
I think I'm looking at the right part, would this be the number I'm looking for?

```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=7922c0c1-e2ae-4f6d-ab28-e7a6daa8a59e /               ext4    errors=remount-ro 0       [color=red]1[/color]
# swap was on /dev/sda5 during installation
UUID=a4531f1b-e128-45ae-bbd8-f64e52a137b6 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by amac777 on 2010-02-11
It's the line with ext4 in it. The problem is the line is too long so you need to scroll further to the right in order to see what the last digits are.

edit: or maximize the window so it's wider.

---

### Post by amac777 on 2010-02-11
> **Naro said:**
> I think I'm looking at the right part, would this be the number I'm looking for?

Yup, that's it.

---

### Post by Naro on 2010-02-11
I just got done restarting it and it did some kind of check, but nothing changed/happened after that.  Was it supposed to give me some kind of error log?

---

### Post by amac777 on 2010-02-11
Yup, look at:

```
gedit /var/log/fsck/checkroot
```

---

### Post by amac777 on 2010-02-11
How are you trying to delete the file and what is the error message?

---

### Post by Naro on 2010-02-11
Using gedit /var/log/fsck/checkroot came back with "nothing has been logged yet."

When I right click on the file, the "move to trash option" is grayed out and when I try to drag the file to the trash, I get this: [http://imgur.com/ARY35.png](http://imgur.com/ARY35.png).  When I click that though, nothing happens.  I thought it might be something with the permissions for the HDD, but when I go to that tab all it says is "The permissions of "My Book" could not be determined."

---

### Post by amac777 on 2010-02-11
Can you try deleting the file from the command line and paste both the command you type and the result here? Also, what is the output of this command?

```
mount
```

---

### Post by Naro on 2010-02-11
The file has a parentheses in it, so it comes back saying ```
bash: syntax error near unexpected token `('
```  What should I type to replace it?

Running "mount" comes back with this: ```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/name/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=name)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

---

### Post by amac777 on 2010-02-11
I'm just trying to see where the file is located so I know which drive to focus on. Can you just type the full path of the file you are trying to erase but cannot?

The reason is I see from your mount information that you have an external drive at "/media/My Book". Is that the drive from which you cannot erase files? Or are you having trouble erasing things from somewhere else?

---

### Post by Naro on 2010-02-11
It's a file inside the external HD (My Book), the full location is ```
/media/My Book/Latest Music (Tags)
```

---

### Post by amac777 on 2010-02-11
Okay. I understand now. I guess I mistakenly thought you were trying to delete a file from the / directory. Anyway, try these commands again:

```
sudo umount /dev/sdb1
sudo fsck /dev/sdb1
```

---

### Post by Naro on 2010-02-11
This is what I'm getting with fsck /dev/sdb1:

```
fsck from util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:db/54, 68:9a/1f, 69:98/fb, 70:9b/16
1) Copy original to backup
2) Copy backup to original
3) No action
? 

```

---

### Post by amac777 on 2010-02-11
Hmmm... I don't know either. It might not matter, try choosing "3: No action" for now and see what other errors are there.

Edit: by the way, that drive is using vfat, which is a really old and error prone file system. I'm not sure if you have a backup of everything on that drive, but if you do and you want, you could reformat it using ext3 (if you want to only use it with linux) or ntfs (if you need to share it with windows/mac).

---

### Post by Naro on 2010-02-11
How would I convert it to NTFS, the only options I'm seeing under "Format" are ext3 and FAT.

---

### Post by amac777 on 2010-02-12
You can use gparted:

```
sudo apt-get install gparted
```

Here's a video tutorial. 

[http://www.youtube.com/watch?v=9jT8n9PKiFE](http://www.youtube.com/watch?v=9jT8n9PKiFE)

Be very careful that you format the correct drive! (Most likely /dev/sdb in your case, but double check it in gparted to make sure both the size and vfat are correctly indicated in gparted before you format it.)

---

### Post by Naro on 2010-02-12
Thanks!  I was able to format it to NTFS and everything seems to be working fine now.  Thanks again for all the help.

---

