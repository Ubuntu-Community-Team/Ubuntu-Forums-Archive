---
title: "No Longer Able to Mount NTFS Partition"
date: 2005-07-17
forum: Hardware &amp; Laptops
---

### Post by Unwiseone on 2005-07-17
I have a 9.0G primary harddrive (hda) with Ubuntu on it, and an additional 80.0G harddrive (hdb) formated as ntfs that I've stored a bunch of music and video on. Until recently, I have been able to mount the ntfs hd with no problem. However two or so months ago (?) -- or when that last update to the kernal image appeared in the Update Manager -- I found that I could no longer mount my ntfs partition. Whenever I tried to mount it I got the following error message:

```
mount: special device /dev/hdb1 does not exist
```

Curious, I checked the /dev folder, and lo and behold while /dev/hdb does exist /dev/hdb1 does not. I did some Googling and found that you can create nodes with the mknod command, but I'm apprehensive of trying methods that I'm unfamiliar with, especially   if they have nothing to do with my problem. 

Here's some more info on my filesystem...

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/shared   ntfs    umask=0222 	0 	0
```

result of fdisk -l:

```
Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1185     9518481   83  Linux
/dev/hda2            1186        1240      441787+   5  Extended
/dev/hda5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
180 heads, 63 sectors/track, 14116 cylinders
Units = cylinders of 11340 * 512 = 5806080 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?           1       14116    80035798+   7  HPFS/NTFS
```

Any help would be geatly appreciated.

---

### Post by amohanty on 2005-07-18
Backup your fstab.

In fstab replace:
/dev/hdb1       /media/shared   ntfs    umask=0222 	0 	0
with
/dev/hdb       /media/shared   ntfs    umask=0222 	0 	0

reboot.

I am not sure what changes were made to the newer kernel to bring this about, but this did fix the problem for me. For some reason entire drives are not assigned a number after drive spec.

HTH
AM

---

### Post by Unwiseone on 2005-07-18
Now the mount command complains:

```
mount: /dev/hdb already mounted or /media/shared busy
```

I'm not sure what would cause that, even after a restart.

---

### Post by amohanty on 2005-07-18
YOu dont need to reboot to reload your fstab.

First unmount your /media/shared:

>> sudo umount /media/shared

then reload fstab

>> sudo mount -a

Please post the result.

AM

---

### Post by Unwiseone on 2005-07-18
Yeah. I tried editing /etc/fstab then 'mount -a' to no avail.

result of 'sudo mount -a':
```
mount: /dev/hdb already mounted or /media/shared busy
```

Only then did I restart.

'/etc/fstab':
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb        /media/shared   ntfs    umask=0222 	0 	0
```

result of 'sudo fdisk -l':
```
Disk /dev/hda: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1185     9518481   83  Linux
/dev/hda2            1186        1240      441787+   5  Extended
/dev/hda5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
180 heads, 63 sectors/track, 14116 cylinders
Units = cylinders of 11340 * 512 = 5806080 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?           1       14116    80035798+   7  HPFS/NTFS

```

result of 'df -h':
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             9.0G  4.8G  3.8G  56% /
tmpfs                 126M     0  126M   0% /dev/shm
/dev                  9.0G  4.8G  3.8G  56% /.dev
none                  5.0M  2.8M  2.3M  55% /dev

```

---

### Post by amohanty on 2005-07-18
Did you unmount before trying mount -a

---

### Post by Unwiseone on 2005-07-18
No I didn't. Ok, just tried 'sudo umount /dev/hdb' and 'sudo umount /media/shared' and got the following responses:

```
umount: /dev/hdb: not mounted
```
and
```
umount: /media/shared: not mounted
```

---

### Post by amohanty on 2005-07-18
Ok heres what I have for my ntfs partition:
/dev/sda1       /mnt/win        ntfs    auto,user,exec,ro,umask=0220    0       0

try this, of course replace /mnt/win with /media/shared and reboot.

AM

---

### Post by Unwiseone on 2005-07-18
Unfortunately I'm still getting the same error message: "/dev/hdb already mounted or /media/shared busy". I'll Google a bit to see if I can find a solution, but any other suggestions you might have would also be greatly appreciated.

---

### Post by locutus24 on 2005-07-18
Had the same problem, did a reformat used this tutorial [http://www.linuxforum.com/linux_tutorials/1/1.php](http://www.linuxforum.com/linux_tutorials/1/1.php) mounted right up and now i have access to all my stuff. A reformat myabe a bit over doing it but i was having other problems, so for me a reformat wasnt that bad of a descion

---

### Post by amohanty on 2005-07-18
Well reformatting is a bit extreme.

Can you post the results of a mount -l
AM

---

### Post by Unwiseone on 2005-07-18
I probably would have reformatted already if I didn't stand to loose nearly 80Gb of data.

result of 'mount -l':
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
```

Do any of the repositories have a copy of the kernel image before the last update? My mounting of NTFS partitions worked fine then.

---

### Post by amohanty on 2005-07-18
Ok just try this:

1. cd /mnt
2. mkdir win
3. mount -t ntfs /dev/hdb /mnt/win

if that doesnt work try:
4. mount -t ntfs /dev/hdb1 /mnt/win

please post the results.

AM

---

### Post by Unwiseone on 2005-07-18
*Sigh*. Still no luck.

result of 'sudo mount -t ntfs /dev/hdb /mnt/win':
```
mount: /dev/hdb already mounted or /mnt/win busy
```
result of 'sudo mount -t ntfs /dev/hdb1 /mnt/win':
```
mount: special device /dev/hdb1 does not exist
```

Thanks for your continued help though.   ](*,)

---

### Post by amohanty on 2005-07-19
Thats kind of wierd:

Can you post the results of the following:


>> fuser -uav -m /mnt/win
>> fuser -uav -m /media/shared
>> fuser -uav -m /dev/hdb

This will show us who the fsck is using the drive behind the scenes, and thus giving the filesystem busy mesg.

AM

---

### Post by Unwiseone on 2005-07-19
results of 'fuser -uav -m /mnt/win':
```
                     USER        PID ACCESS COMMAND
/mnt/win             root          1 ....m  init
                     root       1100 ....m  udevd
                     root       4822 ....m  dhclient3
                     root       5700 ....m  syslogd
                     root       5715 ....m  dd
                     klog       5717 ....m  klogd
                     root       5750 ....m  gdm
                     root       5763 ....m  gdm
                     root       5778 ....m  cupsd
                     root       5964 ....m  Xorg
                     root       6323 ....m  acpid
                     root       6387 ....m  dbus-daemon-1
                     root       6474 ....m  hald
                     root       6487 ....m  inetd
                     root       6608 ....m  master
                     root       6619 ....m  qmgr
                     root       6779 ....m  atd
                     root       6790 ....m  cron
                     root       6812 ....m  getty
                     root       6813 ....m  getty
                     root       6814 ....m  getty
                     root       6815 ....m  getty
                     root       6816 ....m  getty
                     root       6817 ....m  getty
                     vasco      6941 frce.  sh
                     root       6987 ....m  ssh-agent
                     vasco      6990 .rce.  dbus-launch
                     vasco      6991 .rce.  dbus-daemon-1
                     vasco      7004 .rce.  sh
                     vasco      7005 .rce.  xscreensaver
                     root       7008 ....m  ssh-agent
                     vasco      7011 .rce.  xfce4-session
                     vasco      7014 .rce.  dbus-daemon-1
                     vasco      7018 frce.  xfce-mcs-manage
                     vasco      7021 .rce.  xfwm4
                     vasco      7023 frce.  xfce4-panel
                     vasco      7025 .rce.  xftaskbar4
                     vasco      7027 frce.  xfdesktop
                     vasco      7049 frce.  gconfd-2
                     vasco     11017 frce.  java
                     vasco     11527 .rce.  mousepad
                     vasco     11743 .rce.  gaim
                     vasco     11785 frce.  mozilla-bin
                     root      11987 ....m  pickup
                     vasco     13078 .rce.  gnome-terminal
                     vasco     13082 .rce.  bonobo-activati
                     root      13085 ....m  gnome-pty-helpe
                     vasco     13086 .rce.  bash
                     vasco     13106 .rce.  bash
                     vasco     13120 .r.e.  fuser

```

results of 'fuser -uav -m /media/shared':
 ```
                    USER        PID ACCESS COMMAND
/media/shared        root          1 ....m  init
                     root       1100 ....m  udevd
                     root       4822 ....m  dhclient3
                     root       5700 ....m  syslogd
                     root       5715 ....m  dd
                     klog       5717 ....m  klogd
                     root       5750 ....m  gdm
                     root       5763 ....m  gdm
                     root       5778 ....m  cupsd
                     root       5964 ....m  Xorg
                     root       6323 ....m  acpid
                     root       6387 ....m  dbus-daemon-1
                     root       6474 ....m  hald
                     root       6487 ....m  inetd
                     root       6608 ....m  master
                     root       6619 ....m  qmgr
                     root       6779 ....m  atd
                     root       6790 ....m  cron
                     root       6812 ....m  getty
                     root       6813 ....m  getty
                     root       6814 ....m  getty
                     root       6815 ....m  getty
                     root       6816 ....m  getty
                     root       6817 ....m  getty
                     vasco      6941 frce.  sh
                     root       6987 ....m  ssh-agent
                     vasco      6990 .rce.  dbus-launch
                     vasco      6991 .rce.  dbus-daemon-1
                     vasco      7004 .rce.  sh
                     vasco      7005 .rce.  xscreensaver
                     root       7008 ....m  ssh-agent
                     vasco      7011 .rce.  xfce4-session
                     vasco      7014 .rce.  dbus-daemon-1
                     vasco      7018 frce.  xfce-mcs-manage
                     vasco      7021 .rce.  xfwm4
                     vasco      7023 frce.  xfce4-panel
                     vasco      7025 .rce.  xftaskbar4
                     vasco      7027 frce.  xfdesktop
                     vasco      7049 frce.  gconfd-2
                     vasco     11017 frce.  java
                     vasco     11527 .rce.  mousepad
                     vasco     11743 .rce.  gaim
                     vasco     11785 frce.  mozilla-bin
                     root      11987 ....m  pickup
                     vasco     13078 .rce.  gnome-terminal
                     vasco     13082 .rce.  bonobo-activati
                     root      13085 ....m  gnome-pty-helpe
                     vasco     13086 .rce.  bash
                     vasco     13106 .rce.  bash
                     vasco     13147 .r.e.  fuser
```

results of 'fuser -uav -m /dev/hdb':
```
                     USER        PID ACCESS COMMAND
/dev/hdb
```

---

### Post by Unwiseone on 2005-07-19
Just for the heck of it I downloaded the Ubuntu Live CD to see if I could mount my NTFS partition in that enviroment. Unfortunately I recived the same errors I reported above. Is it possible that the current torrent for the i386 Live CD is updated with the most recent version of the kernel image? 

Strangely enough, I tried the Live CD on my dad's Dell laptop and was able to mount his NTFS formatted hd with no problem.  :-?

---

### Post by amohanty on 2005-07-20
Man from the fuser it seems that you are booting and running your core system off of the /mnt/win partition which is kind of impossible. 

I am sorry man I am not guru enough to be able to tell you whats going on there. I would think that your install is royally screwed up somehow, I have never seen this happen in my 12 years of linux usage. I would suggest reinstalling ubuntu if you can.

Or scream at the top of your lungs for help.

AM

---

### Post by amohanty on 2005-07-20
Just though of something:

get into single user mode:
>> sudo telinit 1

this will quit xserver and throw you at the command line.
then run the fuser set you just did. Ideally you should not see anything. If you do, boot into recovery mode from grub, and do the same.

Once you can get to a point where you cannot see anything, remove all references from fstab to /dev/hdb and /mnt/win. Delete /mnt/win. And reboot.

If you can reboot normally and startup the app, try running: fuser on /dev/hdb

and post the results.

AM

---

### Post by Unwiseone on 2005-07-21
Ok, after executing 'telinit 1', at the command line I ran the fuser set and got much the same results as the last post I made. I then rebooted and entered the recovery mode from grub and got the same results. I then removed any reference to '/dev/hdb' and '/mnt/win' in '/etc/fstab', saved and rebooted again. 

After I logged into the desktop I ran the fuser set again once more got the same results:

results of 'fuser -uav -m /media/shared' :
```
                     USER        PID ACCESS COMMAND
/media/shared        root          1 ....m  init
                     root       1100 ....m  udevd
                     root       5156 ....m  dhclient3
                     root       5671 ....m  syslogd
                     root       5686 ....m  dd
                     klog       5688 ....m  klogd
                     root       5721 ....m  gdm
                     root       5736 ....m  cupsd
                     root       5744 ....m  gdm
                     root       5780 ....m  Xorg
                     root       6266 ....m  acpid
                     root       6348 ....m  dbus-daemon-1
                     root       6360 ....m  hald
                     root       6373 ....m  inetd
                     root       6593 ....m  master
                     root       6608 ....m  pickup
                     root       6609 ....m  qmgr
                     root       6755 ....m  anacron
                     root       6766 ....m  atd
                     root       6777 ....m  cron
                     root       6799 ....m  getty
                     root       6800 ....m  getty
                     root       6801 ....m  getty
                     root       6802 ....m  getty
                     root       6803 ....m  getty
                     root       6804 ....m  getty
                     vasco      6901 frce.  sh
                     root       6947 ....m  ssh-agent
                     vasco      6950 .rce.  dbus-launch
                     vasco      6951 .rce.  dbus-daemon-1
                     vasco      6964 .rce.  sh
                     vasco      6965 .rce.  xscreensaver
                     root       6968 ....m  ssh-agent
                     vasco      6971 .rce.  xfce4-session
                     vasco      6974 .rce.  dbus-daemon-1
                     vasco      6978 frce.  xfce-mcs-manage
                     vasco      6981 .rce.  xfwm4
                     vasco      6983 frce.  xfce4-panel
                     vasco      6985 .rce.  xftaskbar4
                     vasco      6987 frce.  xfdesktop
                     vasco      6989 .rce.  mousepad
                     vasco      6993 frce.  gconfd-2
                     vasco      7009 frce.  mozilla-bin
                     vasco      7033 .rce.  gnome-terminal
                     vasco      7035 .rce.  bonobo-activati
                     root       7036 ....m  gnome-pty-helpe
                     vasco      7037 .rce.  bash
                     vasco      7047 .r.e.  fuser
```

results of 'fuser -uav -m /mnt/win' :
```
                     USER        PID ACCESS COMMAND
/mnt/win             root          1 ....m  init
                     root       1100 ....m  udevd
                     root       5156 ....m  dhclient3
                     root       5686 ....m  dd
                     klog       5688 ....m  klogd
                     root       5721 ....m  gdm
                     root       5744 ....m  gdm
                     root       5780 ....m  Xorg
                     root       6266 ....m  acpid
                     root       6348 ....m  dbus-daemon-1
                     root       6360 ....m  hald
                     root       6373 ....m  inetd
                     root       6593 ....m  master
                     root       6608 ....m  pickup
                     root       6609 ....m  qmgr
                     root       6766 ....m  atd
                     root       6777 ....m  cron
                     root       6799 ....m  getty
                     root       6800 ....m  getty
                     root       6801 ....m  getty
                     root       6802 ....m  getty
                     root       6803 ....m  getty
                     root       6804 ....m  getty
                     vasco      6901 frce.  sh
                     root       6947 ....m  ssh-agent
                     vasco      6950 .rce.  dbus-launch
                     vasco      6951 .rce.  dbus-daemon-1
                     vasco      6964 .rce.  sh
                     vasco      6965 .rce.  xscreensaver
                     root       6968 ....m  ssh-agent
                     vasco      6971 .rce.  xfce4-session
                     vasco      6974 .rce.  dbus-daemon-1
                     vasco      6978 frce.  xfce-mcs-manage
                     vasco      6981 .rce.  xfwm4
                     vasco      6983 frce.  xfce4-panel
                     vasco      6985 .rce.  xftaskbar4
                     vasco      6987 frce.  xfdesktop
                     vasco      6989 .rce.  mousepad
                     vasco      6993 frce.  gconfd-2
                     vasco      7009 frce.  mozilla-bin
                     vasco      7033 .rce.  gnome-terminal
                     vasco      7035 .rce.  bonobo-activati
                     root       7036 ....m  gnome-pty-helpe
                     vasco      7037 .rce.  bash
                     root       7136 ....m  cupsd
                     root       7222 ....m  syslogd
                     vasco      7231 .r.e.  fuser
```

results of 'fuser -uav -m /dev/hdb' :
```
                     USER        PID ACCESS COMMAND
/dev/hdb
```

---

### Post by sbassett on 2005-07-21
Did you happen to access this drive or modify it in anyway. I was looking over your posts, and it looks like the partition got hosed somehow.```
This doesn't look like a partition table
Probably you selected the wrong device.
```

---

### Post by TSJason on 2005-07-22
I'm running into the same type of problem but not just with my ntfs partition, but also with another reiserfs I have:

fstab entry:
```
/dev/hda1       /archives2      reiserfs defaults       0       0
```

command line:
```
jason@tiamat:/$ sudo mount /archives2
mount: /dev/hda1 already mounted or /archives2 busy
jason@tiamat:/$ sudo fuser -muav /dev/hda

                     USER        PID ACCESS COMMAND
/dev/hda
jason@tiamat:/$ 

```

At this point I'm like "what the??"

So I do:

```

jason@tiamat:/$ lsof |grep archives2
gam_serve 14997      jason  148r      DIR                8,3       48      77639 /archives2
jason@tiamat:/$ sudo ps auxSww |grep gam_serve
jason    14997  0.3  0.5  15540  2928 ?        S    Jul20  11:07 /usr/lib/gamin/gam_server
jason    23827  0.0  0.1   4152   824 pts/5    S+   00:15   0:00 grep gam_serve

```

Oh alright, fine then:

```

jason@tiamat:/$ sudo kill -9 14997
jason@tiamat:/$ sudo mount /archives2
mount: /dev/hda1 already mounted or /archives2 busy

```

At this point, I'm screaming and pulling out hair...double check it:

```

jason@tiamat:/$ lsof |grep archives2
gam_serve 23889      jason   13r      DIR                8,3       48      77639 /archives2

```

It freaking reappered! A quick google show's it's a bug in the gamin File and directory monitoring system....booooooo!
It cannot be removed either because it's a dependenacy for a ton of apps including firefox and kde  ](*,) 
Fine, we're playing dirty:

```

jason@tiamat:/$ sudo chmod 000 /usr/lib/gamin/gam_server
jason@tiamat:/$ sudo kill -9 23889
jason@tiamat:/$ sudo lsof |grep archives2
jason@tiamat:/$ sudo mount /archives2
mount: /dev/hda1 already mounted or /archives2 busy
jason@tiamat:/$

```

And here I am...still bashing my head into this brick wall...any suggestions?

---

### Post by black hole sun on 2005-07-22
[QUOTE=Unwiseone]Ok, after executing 'telinit 1', at the command line I ran the fuser set and got much the same results as the last post I made. I then rebooted and entered the recovery mode from grub and got the same results. I then removed any reference to '/dev/hdb' and '/mnt/win' in '/etc/fstab', saved and rebooted again. 

After I logged into the desktop I ran the fuser set again once more got the same results:

results of 'fuser -uav -m /media/shared' :
```
                     USER        PID ACCESS COMMAND
/media/shared        root          1 ....m  init
                     root       1100 ....m  udevd
                     root       5156 ....m  dhclient3
                     root       5671 ....m  syslogd
                     root       5686 ....m  dd
                     klog       5688 ....m  klogd
                     root       5721 ....m  gdm
                     root       5736 ....m  cupsd
                     root       5744 ....m  gdm
                     root       5780 ....m  Xorg
                     root       6266 ....m  acpid
                     root       6348 ....m  dbus-daemon-1
                     root       6360 ....m  hald
                     root       6373 ....m  inetd
                     root       6593 ....m  master
                     root       6608 ....m  pickup
                     root       6609 ....m  qmgr
                     root       6755 ....m  anacron
                     root       6766 ....m  atd
                     root       6777 ....m  cron
                     root       6799 ....m  getty
                     root       6800 ....m  getty
                     root       6801 ....m  getty
                     root       6802 ....m  getty
                     root       6803 ....m  getty
                     root       6804 ....m  getty
                     vasco      6901 frce.  sh
                     root       6947 ....m  ssh-agent
                     vasco      6950 .rce.  dbus-launch
                     vasco      6951 .rce.  dbus-daemon-1
                     vasco      6964 .rce.  sh
                     vasco      6965 .rce.  xscreensaver
                     root       6968 ....m  ssh-agent
                     vasco      6971 .rce.  xfce4-session
                     vasco      6974 .rce.  dbus-daemon-1
                     vasco      6978 frce.  xfce-mcs-manage
                     vasco      6981 .rce.  xfwm4
                     vasco      6983 frce.  xfce4-panel
                     vasco      6985 .rce.  xftaskbar4
                     vasco      6987 frce.  xfdesktop
                     vasco      6989 .rce.  mousepad
                     vasco      6993 frce.  gconfd-2
                     vasco      7009 frce.  mozilla-bin
                     vasco      7033 .rce.  gnome-terminal
                     vasco      7035 .rce.  bonobo-activati
                     root       7036 ....m  gnome-pty-helpe
                     vasco      7037 .rce.  bash
                     vasco      7047 .r.e.  fuser
```

results of 'fuser -uav -m /mnt/win' :
```
                     USER        PID ACCESS COMMAND
/mnt/win             root          1 ....m  init
                     root       1100 ....m  udevd
                     root       5156 ....m  dhclient3
                     root       5686 ....m  dd
                     klog       5688 ....m  klogd
                     root       5721 ....m  gdm
                     root       5744 ....m  gdm
                     root       5780 ....m  Xorg
                     root       6266 ....m  acpid
                     root       6348 ....m  dbus-daemon-1
                     root       6360 ....m  hald
                     root       6373 ....m  inetd
                     root       6593 ....m  master
                     root       6608 ....m  pickup
                     root       6609 ....m  qmgr
                     root       6766 ....m  atd
                     root       6777 ....m  cron
                     root       6799 ....m  getty
                     root       6800 ....m  getty
                     root       6801 ....m  getty
                     root       6802 ....m  getty
                     root       6803 ....m  getty
                     root       6804 ....m  getty
                     vasco      6901 frce.  sh
                     root       6947 ....m  ssh-agent
                     vasco      6950 .rce.  dbus-launch
                     vasco      6951 .rce.  dbus-daemon-1
                     vasco      6964 .rce.  sh
                     vasco      6965 .rce.  xscreensaver
                     root       6968 ....m  ssh-agent
                     vasco      6971 .rce.  xfce4-session
                     vasco      6974 .rce.  dbus-daemon-1
                     vasco      6978 frce.  xfce-mcs-manage
                     vasco      6981 .rce.  xfwm4
                     vasco      6983 frce.  xfce4-panel
                     vasco      6985 .rce.  xftaskbar4
                     vasco      6987 frce.  xfdesktop
                     vasco      6989 .rce.  mousepad
                     vasco      6993 frce.  gconfd-2
                     vasco      7009 frce.  mozilla-bin
                     vasco      7033 .rce.  gnome-terminal
                     vasco      7035 .rce.  bonobo-activati
                     root       7036 ....m  gnome-pty-helpe
                     vasco      7037 .rce.  bash
                     root       7136 ....m  cupsd
                     root       7222 ....m  syslogd
                     vasco      7231 .r.e.  fuser
```

results of 'fuser -uav -m /dev/hdb' :
```
                     USER        PID ACCESS COMMAND
/dev/hdb
```[/QUOTE]
 Few things; type

```
lsmod
```

If "ntfs" does not show up, then it's no wonder you're unable to mount the drive. 

If that is the case, type;

```
sudo modprobe ntfs
sudo /sbin/udevstart
``` and try mounting again, use /dev/hdb1 not /dev/hdb!

---

### Post by Unwiseone on 2005-07-22
[QUOTE=sbassett]Did you happen to access this drive or modify it in anyway. I was looking over your posts, and it looks like the partition got hosed somehow.[/QUOTE]

That's possible. However, I was having this problem before I 'fsck' on it. Tonight I pulled the ntfs hard drive in question out of my ubuntu box, and popped it into my winxp box and it ran a diagostic on it. No errors, bad sectors, boot sector, nothing. I can read and write to it with no problem under XP.

Tomorrow I think I take the vfat hard drive out of my winxp box and put in in my ubuntu machine and see if I can mount that. If I can't I'll know the problem isn't with my ntfs hd, but with my ubuntu system.

[QUOTE=black hole sun]Few things; type

```
lsmod
```

If "ntfs" does not show up, then it's no wonder you're unable to mount the drive. 

If that is the case, type;

```
sudo modprobe ntfs
sudo /sbin/udevstart
``` and try mounting again, use /dev/hdb1 not /dev/hdb![/QUOTE]

Ran 'lsmod' and "ntfs" was the first in the list. I ran the other commands anyway and still got the same error messages. Trying to mount '/dev/hdb1' gives: 
```
mount: special device /dev/hdb1 does not exist
```

And trying to mount '/dev/hdb' gives:
```
mount: /dev/hdb already mounted or /media/shared busy

```

TSJason, were you able to mount ntfs and vfat partitions before you started having this problem?

---

### Post by TSJason on 2005-07-22
Hi,

 I have the same problem with my nfts drive that the reiserfs drive exhibits. As you said, mine also is perfect when I throw it into my XP box.

fstab entry:

/dev/hdb1       /archives3      ntfs    defaults        0       0

jason@tiamat:~$ sudo mount /archives3
mount: /dev/hdb1 already mounted or /archives3 busy
jason@tiamat:~$ lsmod |grep ntfs
ntfs                   92928  0
jason@tiamat:~$ lsmod |grep reiser
reiserfs              225328  2

Everything *I* can think of is how it should be.

---

### Post by TSJason on 2005-07-22
Yikes! I suspected it was a kernel issue so I recompiled with a few different settings and finally I got a configuration that mounts it properly. If anyone is interested in my .config let me know...I'm not even totally sure which setting it was. I'm using 2.6.13-rc3 on my amd64.

---

### Post by Unwiseone on 2005-07-22
I'm thinking that's what I may have to do myself, though I'm not to familiar with compiling the kernel, but I'm sure I'm capable of following a good guide for the process. The only problem is I wouldn't even know what setting I was looking to change! I'm running 2.6.10-5-686 currently, BTW.

---

### Post by sandyeggoboy on 2005-07-22
I have had to reformat several times myself becuase of this issue. I would like to know what I am doing wrong, not just reformat the drive and never figure it out.

My system:

/dev/hda1 / ext3 user,noauto 0 0
/dev/hda5 /swap swap
/dev/hdb1 /mnt/some_data1 vfat user,noauto 0 0
/dev/hdb2 /mnt/some_data2 vfat user,noauto 0 0
/dev/hdb3 /mnt/some_data3 vfat user,noauto 0 0
/dev/hdc5 /home/user1/Apple hfsplus ro,user,noauto 0 0

I have the /dev/hdc device with a removable drive tray so i can work with other operating systems. Maybe this is what is causing some of this?


Thanks,

Deric Stowell

---

### Post by TSJason on 2005-07-22
Hi,


 Luca wrote a pretty easy-to-follow guide for recompiling.
[http://ubuntuforums.org/showthread.php?t=43065&highlight=recompile+kernel](http://ubuntuforums.org/showthread.php?t=43065&highlight=recompile+kernel)

Not exactly how I do it but an excellent guide, nontheless.

---

### Post by Unwiseone on 2005-07-22
Thanks, I'll check that guide out. What exactly would you do differently though?

---

### Post by TSJason on 2005-07-22
Hi,

  Nothing extreme. I tend to grab the newest patched kernel from kernel.org (in the linux/kernel/v2.6/testing/ directory) and switch over to single user mode for my local machine to compile it more quickly. You will be amazed at the speed difference in compiling if you aren't running X at the same time. Basically that means replacing the 'make xconfig' with 'make menuconfig' instead.

 Also, I don't know if you already have a custom kernel in there, but you can keep your old settings by copying the .config file from the previous source tree to the new one.

---

### Post by jeffreyvergara.NET on 2005-09-13
[QUOTE=TSJason]Hi,

  Nothing extreme. I tend to grab the newest patched kernel from kernel.org (in the linux/kernel/v2.6/testing/ directory) and switch over to single user mode for my local machine to compile it more quickly. You will be amazed at the speed difference in compiling if you aren't running X at the same time. Basically that means replacing the 'make xconfig' with 'make menuconfig' instead.

 Also, I don't know if you already have a custom kernel in there, but you can keep your old settings by copying the .config file from the previous source tree to the new one.[/QUOTE]
 hello, i managed to mount and see my 40GB Hard drive, but i could not access it, it says: The folder contents could not be displayed. you dont have the permission necessary to view the contents of "my mnt/folder"

---

### Post by thefool on 2006-01-07
i had the same problem:

"This doesn't look like a partition table
Probably you selected the wrong device."

my partition table wasn't in the first sector

use gpart/gparted for linux or for windows use partition magic or partition table doctor to repair/move it...

---

