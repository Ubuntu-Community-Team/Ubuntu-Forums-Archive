---
title: "[SOLVED] [kubuntu] hal refuses to unmount usb key"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by brazzmonkey on 2008-01-14
hello there,

on kubuntu gutsy i'm unable to unmount my removable usb devices. it seems to be a hal/kde-related issue. Whenever i choose "safely remove" from the usb device cntext menu, i get the following error ::

```
hal-storage-can-unmount-volumes-mounted-by-others refused uid 1000
```

"eject" command in konsole works though but it's a much less handy way&#8230;

hal version is 0.5.9.1-6ubuntu5

what's wrong ?

thx

---

### Post by h4mx0r on 2008-01-14
do lsof /dev/device and see what program is currently being a jerk and not "hanging up the phone" on file transfer then kill it. Sorry thunar does that some to me on xfce sometimes and it gets annoying. Its mainly when I leave it viewing the usb drive as root then exit out of it. Perhaps you should try to recreate the issue and submit it as a bug report. Does kde have a daemon for its file viewer to speed up opening directories?

---

### Post by brazzmonkey on 2008-01-14
well actually this happens even when no file transfer is done. lsof /dev/sdc1 doesn't give any output.

i don't know about any kde daemon which would speed up opening directories, but i may simply be ignorant.

---

### Post by brazzmonkey on 2008-01-14
no hint ?

---

### Post by Yellow Pasque on 2008-01-14
Looks like a permissions issue to me.

What does your /etc/group file look like?

---

### Post by brazzmonkey on 2008-01-14
it look like this (i am user1 btw)

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:user1
tty:x:5:
disk:x:6:user1
lp:x:7:cupsys
mail:x:8:user1
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,user2,user1
fax:x:21:user1
voice:x:22:user1
cdrom:x:24:haldaemon,user2,user1,user3
floppy:x:25:haldaemon,user2,user1
tape:x:26:
sudo:x:27:
audio:x:29:user2,user1,user3
dip:x:30:user1
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:user2,user1,user3
sasl:x:45:
plugdev:x:46:haldaemon,user2,user1,user3
staff:x:50:
games:x:60:user1,user3
users:x:100:user1
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
ssl-cert:x:104:cupsys
crontab:x:105:
ssh:x:106:
messagebus:x:107:
avahi:x:108:
lpadmin:x:109:user2,user1
haldaemon:x:110:
scanner:x:111:cupsys,hplip,user2,user1
slocate:x:112:
user1:x:1000:
admin:x:113:user1
dirmngr:x:114:
saned:x:115:
postfix:x:116:
postdrop:x:117:
user2::1001:
burning:x:1002:user2,user1
enterprise:x:1003:user1
clamav:x:118:
user3::1004:
nvram:x:120:
netdev:x:121:
powerdev:x:122:haldaemon
mysql:x:119:
avahi-autoipd:x:123:
gdm:x:124:
boinc:x:125:

```

thanks for helping.

---

### Post by Yellow Pasque on 2008-01-14
Not sure if this will solve the issue or not:
[http://bbs.archlinux.org/viewtopic.php?id=36283](http://bbs.archlinux.org/viewtopic.php?id=36283)

EDIT: Make a backup of the file first.

---

### Post by brazzmonkey on 2008-01-15
Temüjin, this actually works !

all i did was ```
$ cd /media
$ sudo mv .hal-mtab .hal-mtab.old
```

thank you, you gave me the right path to follow ! this is weird, i haven't been able to find this archlinux forums thread with google and co.  it seems their forums are not referenced by search engines.
/me thinks maybe i should use arch again&#8230;

---

### Post by Yellow Pasque on 2008-01-15
Cool. 

I used Yahoo and searched for "hal-storage-can-unmount-volumes-mounted-by-others refused" (with the quotes).

---

### Post by h4mx0r on 2008-04-02
wow that makes no sense what so ever, can you like give an analogy?

---

