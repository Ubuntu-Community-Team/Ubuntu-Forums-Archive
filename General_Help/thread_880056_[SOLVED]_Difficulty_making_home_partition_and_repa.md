---
title: "[SOLVED] Difficulty making home partition and repairing ensuing mess"
date: 2008-08-04
forum: General Help
---

### Post by MaxIBoy on 2008-08-04
I found [this]("http://www.psychocats.net/ubuntu/separatehome") howto for making a home partition, and decided to give it a shot. After finishing (I followed the directions to the letter, I swear,) I got errors on log-in, after entering username and password. So I figured the tutorial didn't work, went back to the liveCD, and followed the directions for reversing it. Once again, I got errors on log-in. I went back to the liveCD and discovered that the folder for my log-in account weren't in the directory called "home," they were in the directory called "home_backup" *inside* the directory called "home." So I went into the terminal and typed: ```
sudo mv '/home/home_backup/maxtothemax' '/home'
```

Now I STILL get errors.
```
/etc/gdm/Xsession: Beginning session setup...
Can't save user-dirs.dirs
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Could not create gnome accelerators directory '/home/maxtothemax/.gnome2/accels': Permission denied
```

I have this suspicion that something got left behind in that "home_backup" folder, especially since the liveCD won't let me delete it.


What did I do wrong/how do I fix this?

---

### Post by ibuclaw on 2008-08-04
was is the output of
```
ls -ld /home/maxtothemax
```
You may just haven't set the permissions right on ALL subdirectories.

Regards
Iain

---

### Post by LowSky on 2008-08-04
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
 right off the website you supplied...
[quote=http://www.psychocats.net/ubuntu/separatehome]What if it doesn't work?
You know, it really should work, but if you somehow messed up your /etc/fstab and didn't configure it correctly... well, that's why we have a live CD, so we can fix things. 

Boot up the live CD, go to a terminal, and type:

```

sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab
```[/quote]

---

### Post by MaxIBoy on 2008-08-04
Lowsky: That's exactly what I did.

Tinivole: I'll be able to tell you in a moment, lemmie just get my liveCD.

---

### Post by MaxIBoy on 2008-08-04
```
ubuntu@ubuntu:~$ ls -ld /home/maxothemax
ls: cannot access /home/maxothemax: No such file or directory
ubuntu@ubuntu:~$ ls -ld '/media/disk/home/maxtothemax' 
drwxr-xr-x 99 root root 4096 2008-08-03 00:43 /media/disk/home/maxtothemax
ubuntu@ubuntu:~$ Is that what you meant? I'm on a liveCD here.
```

---

### Post by ibuclaw on 2008-08-04
I've just had a quick browse through the site, and I think you should change your fstab line to how ubuntu sets it up.

ie:
```
UUID=318942d7-cdf0-4830-b34c-ffccc5aae3bf /home ext3    relatime    0   2
```
to get the UUID number of your partition, run
```
sudo blkid /dev/sda5
```
or whatever the location of your new home partition is.

[EDIT]
YES! It is a permissions problem, your entire directory is owned by root.
To change it and fix your issue, use chown and your username
```
sudo chown maxtothemax:maxtothemax /media/disk/home/maxtothemax -R
```
Replace "max:max" with your actual username, of course, if it is something entirely different.

Regards
Iain

---

### Post by MaxIBoy on 2008-08-04
Here is the contents of fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1f42771d-2847-4cee-8ad3-2e5ccd14510e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=2d11a112-e75a-4da3-95a5-385e39208648 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Here is the output from the suggested command:
```
ubuntu@ubuntu:~$ sudo blkid /dev/sda2
/dev/sda2: UUID="1f42771d-2847-4cee-8ad3-2e5ccd14510e" TYPE="ext3" 
ubuntu@ubuntu:~$ 

```

Seems to match up okay.

---

### Post by MaxIBoy on 2008-08-04
```
ubuntu@ubuntu:~$ sudo chown maxtothemax:maxtothemax /media/disk/home/maxtothemax -R
chown: invalid user: `maxtothemax:maxtothemax'
```

---

### Post by Paradoxalley on 2008-08-04
> **MaxIBoy said:**
> ```
ubuntu@ubuntu:~$ sudo chown maxtothemax:maxtothemax /media/disk/home/maxtothemax -R
chown: invalid user: `maxtothemax:maxtothemax'
```

what it looks like is that at some point during this process you have changed the permissions on your home directory, Tinivole was trying to get you to change the ownership of your home directory to reflect the username that you log in as. If you haven't fixed it already, This is how I would proceed:

1 - at a terminal prompt type: cat /media/disk/etc/passwd
from this output, you should be able to determine your username (usually the last entry with user ID 1000)

2 - again, at the terminal type: cat /media/disk/etc/fstab and verify that no other partitions are mounting on /home (if you aren't certain how to read this file let me know or post the output from this command). If something is mounting at /home then ignore the rest of this post as it will not help you (I can adjust the instructions to fit)

3 - in a terminal type: sudo bash
     this will drop you into a root shell so we can stop typing sudo before everything, just be extra careful as you can cause lots of damage now ;-)

4- in the root terminal type: cd /media/disk/home
then type the following (replacing username with the username we determined in step 1 above):
chown -R username:username ./maxtothemax

if you are still getting the invalid username error or cannot find your username in the 1st step, let me know and I (or someone else here can assist)

Good luck,
Seth

---

### Post by MaxIBoy on 2008-08-04
Should I try it with "maxtothemax" instead of "maxothemax:maxtothemax?"

EDIT:
Whoop, nother reply I didn't see. Yes, I will try that and see how it works.

FURTHER EDIT:
Still getting invalid user.

---

### Post by Paradoxalley on 2008-08-04
the context of the statement you are typing is:

chown (CHange OWNership) username:groupname foldername -R (Recursive)
so, you need to match username and groupname and just specifying a username will not adequately set new ownership...

EDIT:
your username and your primary group can be determined by looking at two files:

/media/disk/etc/passwd (usernames)
/media/disk/etc/group (groupnames)

---

### Post by MaxIBoy on 2008-08-04
Okay. I tried your instructions, still getting that "invalid user" error.

---

### Post by Paradoxalley on 2008-08-04
can you post the results of the following:
at a terminal type: cat /media/disk/etc/passwd

and at a terminal:
cat /media/disk/etc/fstab

thanks

---

### Post by ibuclaw on 2008-08-04
Oops, I forgot, I believe you may have to chroot onto the disk first.

```
sudo chroot /media/disk
```
And then run
```
chown maxtothemax:maxtothemax /home/maxtothemax -R
```

Also, I wasn't aware that you reversed it.

If you have set the permissions right in the first place, it would have worked. (the separate home partition, that is)

Regards
Iain

---

### Post by Paradoxalley on 2008-08-04
absolutely correct!
sorry, I was looking right past that
you do have to chroot to have the usernames interpreted properly

---

### Post by MaxIBoy on 2008-08-04
```
ubuntu@ubuntu:~$ cat /media/disk/etc/passwd 
root:x:0:0:root:/root:/bin/bash 
daemon:x:1:1:daemon:/usr/sbin:/bin/sh 
bin:x:2:2:bin:/bin:/bin/sh 
sys:x:3:3:sys:/dev:/bin/sh 
sync:x:4:65534:sync:/bin:/bin/sync 
games:x:5:60:games:/usr/games:/bin/sh 
man:x:6:12:man:/var/cache/man:/bin/sh 
lp:x:7:7:lp:/var/spool/lpd:/bin/sh 
mail:x:8:8:mail:/var/mail:/bin/sh 
news:x:9:9:news:/var/spool/news:/bin/sh 
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh 
proxy:x:13:13:proxy:/bin:/bin/sh 
www-data:x:33:33:www-data:/var/www:/bin/sh 
backup:x:34:34:backup:/var/backups:/bin/sh 
list:x:38:38:Mailing List Manager:/var/list:/bin/sh 
irc:x:39:39:ircd:/var/run/ircd:/bin/sh 
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh 
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh 
libuuid:x:100:101::/var/lib/libuuid:/bin/sh 
dhcp:x:101:102::/nonexistent:/bin/false 
syslog:x:102:103::/home/syslog:/bin/false 
klog:x:103:104::/home/klog:/bin/false 
hplip:x:104:7:HPLIP system user,,,:/var/run/hplip:/bin/false 
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false 
gdm:x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false 
pulse:x:107:116:PulseAudio daemon,,,:/var/run/pulse:/bin/false 
messagebus:x:108:119::/var/run/dbus:/bin/false 
avahi:x:109:120:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false 
polkituser:x:110:122:PolicyKit,,,:/var/run/PolicyKit:/bin/false 
haldaemon:x:111:123:Hardware abstraction layer,,,:/var/run/hald:/bin/false 
maxtothemax:x:1000:1000:max,,,:/home/maxtothemax:/bin/bash 
ubuntu@ubuntu:~$ cat /media/disk/etc/fstab 
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda2 
UUID=1f42771d-2847-4cee-8ad3-2e5ccd14510e /               ext3    relatime,errors=remount-ro 0       1 
# /dev/sda3 
UUID=2d11a112-e75a-4da3-95a5-385e39208648 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
ubuntu@ubuntu:~$ 

```

EDIT: Saw tinyvole's post; the chown command finished and didn't error out. I'm going to try rebooting now.


FURTHER EDIT:
WORKS NOW! Thanks guys!

---

