---
title: "Hard Drive and USB write problems"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by Hunterjelly on 2007-06-01
WAZZUP!!!

Okay, right to the point: I have a secondary Hard Drive and a Removable Flash Drive. I wanna be able to write to them. I have formated them both to Ext3 by using Gnome Partition Editor. However, I can only read from them and not write, which is a problem:p.

I also have a USB External Hard Drive that I use for grabbing files off of friends computers, it is NTFS (or is it NTSF?). Anyway, I downloaded something like gNTFS or something, but when I ran it I just lost the ability to mount the drive.

So, any help you (I wanna say guys, but thats not correct :P) people can give me? Just so you know, I did search the board for all these problems, but nothing seemed to help me.

Thanks.

---

### Post by Hunterjelly on 2007-06-01
7 hour, no-reply bump.

---

### Post by ivesjd on 2007-06-01
Could you re-phrase it and ask exactly what you want to do? And give us a little bit more info.

---

### Post by Hunterjelly on 2007-06-01
I formated a secondary HDD and a Flash drive to ext3, and I cannot write to them. I also have an NTFS external HDD that I cannot write to (the NTSF drivers just messed up the HDD and I could not mount it).

The questions should be obvious, but if not:** I want to be able to write to all these drives, not just read from them.**

---

### Post by Hunterjelly on 2007-06-02
13 Hour, no-reply bump.

---

### Post by Jeanpaul145 on 2007-06-02
let's see if I can help:

About the drives formatted in ext3:
Could you please post the contents of /etc/fstab and /etc/mtab here?
I ask because it is possible that your drives are (auto)mounted as read-only.

And with the NTFS (=New Technology File System): Maybe someone else can help you there, as I have no experience with writing NTFS partitions in Linux-based OSes.

---

### Post by Hunterjelly on 2007-06-02
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=dd503804-1ad2-4e26-b89a-484cc3c9408e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=112252cf-7ba3-44e5-be7d-7716ba8111b9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

> /dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

Note: None of the drives are currently mounted.

---

### Post by Jeanpaul145 on 2007-06-02
All right. you need the mount points for those drives of yours (something like /media/disk , for example). One way you can check that is by mounting the drives, then looking in /media or /mnt for those drives. With that info, look in (the then current version of) /etc/fstab and /etc/mtab.
If those drives are present in those files (as they should be), you should check the same lines of those drives for "errors=remount-ro" or "ro", basically meaning "remount as readonly when an error occurs" and just plain "mount as read-only", respectively.
In case of the first of those 2, you should know that there occurs an error somewhere after (or while) the mounting, which causes the remount-readonly thing to happen. You should, in that case, try to find out what error occurs, and why.
In the latter case, just remove the "ro" (without the quotes) from the line(s).

---

### Post by Hunterjelly on 2007-06-02
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=dd503804-1ad2-4e26-b89a-484cc3c9408e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=112252cf-7ba3-44e5-be7d-7716ba8111b9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

> /dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sda1 /media/disk ext3 rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/disk-1 ntfs rw,nosuid,nodev,umask=222,utf8 0 0

That look right?

---

### Post by Jeanpaul145 on 2007-06-02
Assuming that /media/disk and /media/disk-1 are the mount points of the partitions you were talking about, then you SHOULD be able to write to them (even the ntfs partition).

---

### Post by Hunterjelly on 2007-06-02
> Error while copying to "/media/disk-1".
You do not have permissions to write to this folder.

> Error while copying to "/media/disk".
You do not have permissions to write to this folder.

Disk is the Flash Drive and Disk-1 should be the external.
Same thing with Disk-2 (which I forgot to mount before), Disk-2 is my second internal HDD.

---

### Post by Hunterjelly on 2007-06-02
Disk, -1, and -2 all have the same "You do not have permissions to write to this folder." error.

Disk should be my Flash Drive, -1 should be my External HDD, and -2 should be my secondary internal HDD.

(Sorry for the double post there, it looked like there was an error)

---

### Post by Jeanpaul145 on 2007-06-02
try opening a shell (for example bash), and do the following:

- sudo -i                (this requires you to enter your root password)
- copy a file you have access to any of the drives.

If it does not complain here about writing permissions, then you should check the permissions of the drives.
If it does complain, something else is going on (I'm not exactly sure WHAT at the moment).

---

### Post by Hunterjelly on 2007-06-02
Umm... Yeah I'm a total newbie, so I don't know how to copy files VIA Bash.

---

### Post by Jeanpaul145 on 2007-06-02
All right:-\"
the copy command under most shells is "cp"
in it's simplest form, it is used as "cp <source> <destination>"

---

### Post by Hunterjelly on 2007-06-02
> root@xblade:/home/zachary# cp /home/zachary/Desktop/Documents/Steam.html /media/disk-1
cp: cannot create regular file `/media/disk-1/Steam.html': Read-only file system
root@xblade:/home/zachary#
That was the NTFS external HDD.

> root@xblade:/home/zachary# cp /home/zachary/Desktop/Documents/Steam.html /media/disk
root@xblade:/home/zachary# 
Annd wow! It actually copied the .html file! However, when draging a file to the HDD via GNOME I got the permission denied message again.

---

### Post by Jeanpaul145 on 2007-06-02
The NTFS part is easily explainable:
NTFS support in Linux had te be reverse-engineered from working implementations.
As such, it is STILL possible that a write to an NTFS partition can instantly corrupt the whole partition. Because of this, by default you can't write to an NTFS partition (it is possible to configure Linux to write to NTFS, but it's probably more effort than it's worth.).

and the Ext3 partition:
When you were using the terminal to copy the file, it was as root.
However, when you use a GUI to copy files, that same Gui frontend is started up with the same privileges as yourself (the non-root user, to be exact).
You can test this by opening up a terminal and typing "sudo nautilus", and then providing your root password.
BE CAREFUL!!! root privileges are potentially HAZARDOUS TO YOUR SYSTEM!!!
(so I would reccomend opening up nautilus in root mode, copying a NON-ESSENTIAL FILE and closing the root-privileged nautilus immediately).

Let me know if I'm correct.

---

### Post by Hunterjelly on 2007-06-02
Affirmative, I was able to copy files to the drive by using the 'sudo nautilus' command. But it sure would be nice to not have to open up Bash, type that in, then move files... It's just extra work that I'd rather not do.

Would there be a workaround for that?

---

### Post by Jeanpaul145 on 2007-06-02
Let's try the easy way first:
Do you, by any chance, have symbolic links to those drives on your desktop when they are mounted?
because if you do, try the following:
- right mouse click on one of the links.
- go to the permissions tab.
- set the right permissions. This requires a bit of explaining:
    There are (at least standard) 3 types of permissions: for yourself, for the various groups (just to NOT make this complicated, we'll skip this for now) and everyone else.
Set the permissions for yourself to "create and delete files" (If I'm right that's not the currently selected option.)
Click on the button that says "aply permissions to enclodes files"
-close this dialog and repeat for the other (non-ntfs) drive.

Let me know if it works!

---

### Post by Hunterjelly on 2007-06-02
When I click the permissions tab VIA the desktop, all the options are greyed out. When I do the same thing from the 'Computer' option in 'Places' they are not greyed out, but everything sais read-only and it won't let me change them "The permissions could not be changed. Sorry, couldn't change the permissions of "37.3 GB Volume (2): disk".".

---

### Post by Jeanpaul145 on 2007-06-02
Perhaps you are not recognised as the owner of the files then.
Then you'll have to open up a terminal and do "sudo chown <new_owner> <mount_directory_name>" . this will change the owner of the mount directory, and hopefully, also your mounted disk.
HTH!

---

### Post by Hunterjelly on 2007-06-02
> zachary@xblade:~$ sudo chown zachary disk
chown: cannot access `disk': No such file or directory

I tried writing both 'disk' and 'hdb'.

---

### Post by Jeanpaul145 on 2007-06-02
if the mount directory is /media/disk it becomes "sudo chown zachary /media/disk" .
You must use either absolute (as shown in the previous line) or relative pathnames (which you COULD use, but in this case absolute is much simpeler:D)

---

### Post by treggmo on 2007-06-03
Hunterjelly,
Was it NTFS 3G you installed? Take a look at these:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[https://bugs.launchpad.net/ubuntu/+bug/108980](https://bugs.launchpad.net/ubuntu/+bug/108980)

I have a dual boot laptop (XP and Feisty) and all NTFS partitions are mounted at boot for Read and Write.
Follow the instructions to use the NTFS Configuration Tool and enable it for internal and external drives. I don't use an external drive so read up on if you need it attached for the program to see it. It would probably be best to attach it so that /etc/fstab will be updated by the tool. When you are done, check /etc/fstab to see the changes. I made a copy of the original fstab before doing the installation. I'm new to Linux but doing this was not difficult although I did do a lot of reading before I attempted it. I used step 3 only on this page:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Good luck!

---

### Post by Hunterjelly on 2007-06-03
Thank you very much Jean, I can now copy to my other intenal drive. But of coarse, this is Linux, so there is still something else wrong...

When I want to delete a file I cannot right click it and say 'Move To Trash' but instead I have to click the 'Delete' key. My guess is that items can only be moved to the trash that are in the Main Hard Drive (filesystem).

Do you know of anyway to get around that? If you don't then don't even worry about it, not a big deal at all, pressing 1 key is faster than clicking two mouse buttons anyway.


As for you Treggmo.. That you very much, I will definatly give that a try. And yes, I'm quite sure that they were called NTFS 3G. Although I'm now wondering if it is possible to make WinXP read ext3...?

---

### Post by Hunterjelly on 2007-06-03
11 hour, no-reply bump.

---

### Post by Hunterjelly on 2007-06-07
3 day, no-reply bump.......

---

