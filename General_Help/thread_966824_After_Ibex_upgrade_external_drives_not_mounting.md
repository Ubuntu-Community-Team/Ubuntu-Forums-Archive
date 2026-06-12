---
title: "After Ibex upgrade external drives not mounting"
date: 2008-11-01
forum: General Help
---

### Post by truxntrax on 2008-11-01
All was working ok with Hardy and then when I upgraded to Ibex my external nas devices have stopped auto mounting.  However if I run sudo mount -a in terminal the drives appear and are mounted ok.  Here are the contents of my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=830892fc-50c4-4460-8028-880474b74854 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda2
UUID=f51f6e4b-00a4-40de-977f-e3983f89a1e1 /home           ext3    defaults,relatime        0       2
# /dev/hda3
UUID=bbdf3ef0-e3e8-4b5d-ab41-91de37d41ca8 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
[B][COLOR="Red"]//192.168.1.155/Volume_1/ /media/nas/ cifs username=j***,password=******,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.190/share/ /media/popcorn/ cifs username=****,password=******,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0[/COLOR][/B]

The two lines in bold red are the ones that do not initially mount.

I hope someone can help.  Thanks in advance.

Trux

---

### Post by timroberts on 2008-11-01
I'm having a similar problem, but i can't even manually mount. I connect my external, and the read/write light comes on, but it won't mount. sudo mount -a does nothing. my fstab file is below:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=36830eed-0737-434c-8c02-b0e12b4a7318 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=10df3b8b-e4e9-444a-924d-5e5cc3815eda none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

The bottom line is me trying to get USB working in virtualbox, and that isn't working either. Buuuuut, thats another problem for another thread.

---

### Post by ttwaro on 2008-11-02
I, too, am having this exact problem. I went the upgrade route from 8.04.1 to 8.10 which worked very well. I have similar entries in my fstab for external shares. I can manually mount them but they don't mount automatically anymore like they did in 8.04.1 and previous releases. Right now this is my only known problem.

---

### Post by pholden on 2008-11-03
Almost the exact same problem here :(

Content of */etc/fstab* :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2c5dddf-e6f7-4bb1-a1bc-001fb225bc7c /     	ext3    defaults,errors=remount-ro,relatime	0	1
# /dev/sdb2
UUID=aca739fe-4125-4d33-97ee-71e83a8a6d25 /home		ext3	defaults,errors=remount-ro,relatime	0	1
# /dev/sda5
UUID=57072c62-0abc-49a6-a93a-54f8fd407673 none          swap    sw              			0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

CYBER/pholden.Staff\040Accounts.network		/home/pholden/.ncp/R-Drive	ncp	defaults,mode=664,uid=pholden,gid=pholden,owner=pholden,iocharset=utf8,volume=USERS,tcp,ipserver=10.0.0.253,passwdfile=/etc/ncppasswords,multiple	0 0
VICTORY/pholden.Staff\040Accounts.network	/home/pholden/.ncp/M-Drive	ncp	defaults,mode=664,uid=pholden,gid=pholden,owner=pholden,iocharset=utf8,volume=NETMAN,tcp,ipserver=10.0.0.254,passwdfile=/etc/ncppasswords,multiple	0 0
```
Until I upgraded to 8.10 this morning, the NCP entries would mount fine on boot up. Now I have to open a terminal and type *sudo mount -a* to mount them...

---

### Post by truxntrax on 2008-11-03
So what is common about us having this problem and what can we do to get support or debug what is going wrong?

I'm a linux noob but there must be some log file to log at that show what happens when the fstab file is processed?

Trux..

---

### Post by truxntrax on 2008-11-06
Bump - sopmeone must be able to help?!

---

### Post by danduq on 2008-11-07
I am having the same problem. Only information I could find was in /var/log/syslog

```
kernel: [ 4061.676243] CIFS VFS: Send error in SETFSUnixInfo = -5
kernel: [ 4061.676260] CIFS VFS: Negotiating Unix capabilities with the server failed. Consider mounting with the Unix Extensions
kernel: [ 4061.676264] disabled, if problems are found, by specifying the nounix mount option.
```

---

### Post by geirha on 2008-11-07
I found a launchpad bug on this issue. No fix yet, but it's a known issue and appears to be worked on. [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/286828)

---

### Post by truxntrax on 2008-11-08
Tanks for that I was starting to loose faih that it would ever be addressed...

Trux

---

