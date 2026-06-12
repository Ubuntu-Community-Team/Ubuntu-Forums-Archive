---
title: "[SOLVED] Playing cd"
date: 2008-08-17
forum: General Help
---

### Post by wfp on 2008-08-17
I was playing a music cd on banshee, the cd was scratched and the song was skipping so i pulled the cd out of my drive, now when i load music cd's or dvd's nothing happens.

---

### Post by tuxxy on 2008-08-17
Did you try mount the disc?

---

### Post by wfp on 2008-08-18
Thanks for the reply how does one do that. Sorry still a linux nub but willing to learn.

---

### Post by wfp on 2008-08-18
This is what i am getting from the terminal    
wayne@waynes-desktop:~$ sudo mount
[sudo] password for wayne: 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/wayne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wayne)

---

### Post by wfp on 2008-08-18
Thought this might help to.  
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=066ac81e-d42c-4602-9c82-37524bc12c9f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b2985951-e96d-4bb8-bba4-323f348f80fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/wayne/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=wayne 0 0

---

### Post by cariboo on 2008-08-18
You probably have a lock file somewhere that is preventing your cd/dvd's from loading. look in:

```
/proc/sys/dev/cdrom
```

for a file named lock. This should clear when you reboot, but you never know.

Jim

---

### Post by wfp on 2008-08-18
I have tried rebooting and checking my cables just in case. Nothing crap i can not even use the live cd to reinstall ug. wayne@waynes-desktop:~$ /proc/sys/dev/cdrom
bash: /proc/sys/dev/cdrom: No such file or directory
wayne@waynes-desktop:~$

---

### Post by cariboo on 2008-08-18
You have to cd into the directory eg:

```
cd /proc/sys/dev/cdrom
```

this might help

Jim

---

### Post by mb_webguy on 2008-08-18
I've noticed on occasion that if I remove a disc while it's being read, particularly if I remove it shortly after inserting it, that the system won't notice when I subsequently insert another disc.  Also, the icon for the disc remains on the desktop.  I'm not sure if the disc isn't being unmounted properly, or if Gnome/Nautilus isn't noticing that the disc has been unmounted, but all I have to do is right-click on the desktop icon and select Eject.

---

### Post by wfp on 2008-08-18
Thanks for your replys can some one show me how to mount cd\dvd drive.

---

### Post by cariboo on 2008-08-18
The commands are the same when manually mounting any disk inthis case if the disk is detected in a terminal:

```
sudo mount /media/cdrom0
```

Just to see ifthe cdrom is detected check the output of dmesg, to do this in a terminal type:

```
dmesg
```

You should see something like this

```
[56685.747515] UDF-fs: No VRS found
[56685.764756] ISO 9660 Extensions: Microsoft Joliet Level 3
[56685.802944] ISO 9660 Extensions: RRIP_1991A
```

One last thing to try, put the cd you where having trouble with back in the drive, then in a terminal type:

```
eject /media/cdrom0
```

To see if this will eject the cd.

Jim

---

### Post by wfp on 2008-08-19
Hey thanks again for all the help. Sorry for the long delay i opened my box again and checked the cables, noticed a lot of dust on the 3prong connection going into motherboard took that out cleaned it rebooted and lo and behold have my cdrom back. Would have posted earlier but we had to replace are cable modem box. Were having trouble in our house.We have comcast cable, and have 4 pc's hooked up wireless and every time we surf the web it causes the tv to flutter so thats another problem i am working on. Thought maybe it was a bad modem but the new one is doing the same thing not sure whats causing it. It's not my house thinking maybe it's that crappy looking old airlink router there useing. lol

---

