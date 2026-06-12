---
title: "Stupid question Re: sudo"
date: 2006-02-16
forum: Installation &amp; Upgrades
---

### Post by deadfolk on 2006-02-16
Hi all,

I have just (finally) got a basic, (vesa only) version of Ubuntu running, and need to get it networked with my wireless card so I can start installing drivers and such, so I'm following a guide I found for ndiswrapper.

What, you may ask, has this to do with sudo?  Well, it seems that when I try to run any commands with sudo (including the ones I need to install a couple of files for ndiswrapper), nothing happens.  No error message, no feedback at all.  It goes straight back to the command prompt.

Can anyone please help me out?

Thanks in advance,

DF

---

### Post by st1100pilot on 2006-02-16
Some commands (like mkdir) don't give you feedback, they just do the operation, and give you another command line. Is this the case for you?

---

### Post by deadfolk on 2006-02-16
Afraid not.

For example:
```

$ cd /
$ mkdir test
mkdir: cannot create directory 'test': Permission denied
$ sudo mkdir test
Password:
<*password entered here...*>
$ ls test
ls: test: No such file or directory
```

---

### Post by tiris on 2006-02-17
Someone should really answer this question in this thread.
I am having the same problem and am not able to run any administrative programs.

```

:~$sudo cat /etc/fstab
Password:
:~$

```

This is not right and I don’t even know where to begin on trying to solve this problem.

---

### Post by public_void on 2006-02-17
It sounds like the "Executing system administration tasks" check box is unchecked. I know some program do nothing if that option is uncheck and you type your password in to sudo. Does anyone have any accounts that do allow you to use sudo. If so then in that account go to Administration -> User and Groups. Select your group and click properties, then under the User privileges tab. Check "Executing system administration tasks".

---

### Post by tiris on 2006-02-17
I have only one user on the machine and the sudo thing won't work. I can't even get into the users and groups program.

Is there any way to check this through the terminal?
I can use the (recovery mode) to login the text only terminal. With sudo not working this is the only way that I have to perform administrative tasks.

---

### Post by tiris on 2006-02-17
I figured out the problem. I was messing around with FUSE installation just before the problem. I added the group fuse and added myself to that group. It is my suspicion that one of these programs trashed the /etc/group file. It appears that the groups where in tact just that the users were removed.

This is the /etc/group file when the problem exists:
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:hal
floppy:x:25:hal
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:hal
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
tiris:x:1000:
lpadmin:x:104:
scanner:x:105:
admin:x:106:
crontab:x:107:
ssh:x:108:
slocate:x:109:
messagebus:x:110:
hal:x:111:
saned:x:112:
gdm:x:113:
fuse:x:114:tiris

```

This is after I added myself to the admin groups:
```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:tiris
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:hal
floppy:x:25:hal
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:hal
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
tiris:x:1000:
lpadmin:x:104:tiris
scanner:x:105:
admin:x:106:tiris
crontab:x:107:
ssh:x:108:
slocate:x:109:
messagebus:x:110:
hal:x:111:
saned:x:112:
gdm:x:113:
fuse:x:114:tiris

```

After making the changes the problem is gone. Now the question is why did the file get trashed? Maybe I will look into that more, maybe not.

---

