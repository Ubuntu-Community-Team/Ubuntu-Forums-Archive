---
title: "SOLUTION: Suddenly unable to mount HDD,  running Ubuntu Live"
date: 2013-04-08
forum: Hardware
---

### Post by RED666 on 2013-04-08
Some months ago, I had a problem with my Sitecom Nas. It crashed because the unit's OS failed. I turned to Ubuntu to save my data, I used Ubuntu Live Cd to copy the data from 1 of the Nas's disks to the hdisk in my WIndows7 pc.

Then I got lazy and didn't look at the situation anymore untill now. Now, I want to wipe the Nas's disks and with it working again, copy my (saved) data from the Win7 pc back to the Nas.

But for some reason, now, when I start the Win7 pc with Ubuntu Live CD I cannot access my harddisk. Previously this was not a problem. What am I missing ??? anybody got an idea?


[ATTACH=CONFIG]241132[/ATTACH][ATTACH=CONFIG]241131[/ATTACH]


SOLUTION [here]("http://ubuntuforums.org/showthread.php?t=2133606&p=12595080#post12595080")

---

### Post by RED666 on 2013-04-08
Would be nice if someone could give me a push in the right direction!!!
I may have left something to be desired in the clarity of my question.

I'm not able to mount any partition from the pc's harddisk running from a Ubuntu LiveCD **(USB pen drive actually**)
Previously they automounted without a hitch....

I get:
Error mounting /dev/sda2 at /media/ubuntu/Boot: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sda2" "/media/ubuntu/Boot"' exited with non-zero exit status 21: mount: according to mtab, /dev/sda2 is already mounted on /media/ubuntu/Boot

But neither the "Boot" or "sda2" dir exists. As far as I can see...

fstab says:
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0



Please somebody!

---

### Post by ahallubuntu on 2013-04-08
~

---

### Post by RED666 on 2013-04-09
Thx for the reply

root@ubuntu:~# df
df: cannot read table of mounted file systems: Is a directory


Mount list? You mean the lines in fstab?? What you see above is what I got..
B.t.w. I was reading that mtab(current config no?)  should be a file but mine is a directory.....

---

### Post by RED666 on 2013-04-09
Solved it... myself... again... lol

For some reason my mtab file was changed to a directory, in it two files utab and utab.lock. I removed the files first then the directory. Rebooted.

Problem solved. Now I'm able to mount the volume at will!

This is what fstab en mtab look like now:

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
root@ubuntu:~# cat /etc/mtab
/cow / overlayfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
/dev/sdb1 /cdrom vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0
gvfsd-fuse /run/user/ubuntu/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=ubuntu 0 0
/dev/sda2 /media/ubuntu/Boot fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
root@ubuntu:~#

---

### Post by RED666 on 2013-04-09
Solved it... myself... again... lol

For some reason my mtab file was changed to a directory, in it two files utab and utab.lock. I removed the files first then the directory. Rebooted.

Problem solved. Now I'm able to mount the volume at will!

This is what fstab en mtab look like now:
> 

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0


root@ubuntu:~# cat /etc/mtab
/cow / overlayfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
/dev/sdb1 /cdrom vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0
gvfsd-fuse /run/user/ubuntu/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=ubuntu 0 0
/dev/sda2 /media/ubuntu/Boot fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0
root@ubuntu:~#



---

