---
title: "no root access on new install - HELP!"
date: 2008-08-02
forum: General Help
---

### Post by NathanScriv on 2008-08-02
:confused:

I have just installed Xubuntu 8.4 and have run into some difficulties.

When I try and run the Synaptic Package Manager, it says "User Root Does Not Exist"

Sudo -i says "no passwd entry for root!"
Finger root says "no such user"

In the "Users Settings" app it is blank, there are no users or groups shown. I cannot add any users or groups.

The only thing that I did was this:

I was following some out of date instructions on how to set up a printer in Xubuntu, which required adding a cups user to a 'shadow' group. I created the 'shadow' group then realised there is a print manager available in settings so I deleted the 'shadow' group.

How can I fix this?? As you can probably tell I'm new to Linux so am not fully comfortable with shell access, but I can follow directions.

---

### Post by howlingmadhowie on 2008-08-02
there already should be a shadow group with groupid 42.

if you can't get root permissions by using sudo, to correct the problem you'll probably need a livecd and then mount the partition and edit /etc/groups by hand.

as an example, here is the contents of my /etc/group (my main user is called stefan and i've installed a fair bit of software)
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:stefan
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:stefan
fax:x:21:
voice:x:22:
cdrom:x:24:stefan
floppy:x:25:stefan
tape:x:26:
sudo:x:27:
audio:x:29:pulse,stefan
dip:x:30:stefan
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:stefan
sasl:x:45:
plugdev:x:46:stefan
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip
nvram:x:106:
fuse:x:107:stefan
ssl-cert:x:108:
lpadmin:x:109:stefan
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:115:stefan
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
stefan:x:1000:
mysql:x:124:
```

---

