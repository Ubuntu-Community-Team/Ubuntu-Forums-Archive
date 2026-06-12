---
title: "USB HDD Mount"
date: 2009-06-02
forum: Hardware
---

### Post by nunyez on 2009-06-02
I'm using an external USB drive that is plugged in and on all the time. I have rtorrent installed to init.d which fails miserably because the drive doesn't actually mount (I guess..) until I first browse it. Here's a screenshot of my Places menu:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=116194&stc=1&d=1243974310[/IMG]

Note how it is greyed out. After I click it and browse it there is no longer greying in the menu. And now if I restart rtorrent it will see my drive.

My fstab is untouched. Help appreciated.

xubuntu 8.04 hardy

---

### Post by Grandma_DOG on 2009-06-02
I have a similar problem, an external HDD that won't auto mount.

When I look at ```
tail -f /var/log/messages
``` it spits out this and starts to increment up the address.

Any ideas of what's going on?

Jun  2 22:24:00 vesta kernel: [  758.651467] usb 2-2: configuration #1 chosen from 1 choice
Jun  2 22:24:01 vesta kernel: [  759.063804] usb 2-2: USB disconnect, address 78
Jun  2 22:24:02 vesta kernel: [  760.004895] usb 2-2: new high speed USB device using ehci_hcd and address 79
Jun  2 22:24:02 vesta kernel: [  760.137136] usb 2-2: configuration #1 chosen from 1 choice
Jun  2 22:24:02 vesta kernel: [  760.549489] usb 2-2: USB disconnect, address 79
Jun  2 22:24:03 vesta kernel: [  761.491118] usb 2-2: new high speed USB device using ehci_hcd and address 80
Jun  2 22:24:03 vesta kernel: [  761.623940] usb 2-2: configuration #1 chosen from 1 choice
Jun  2 22:24:04 vesta kernel: [  762.032419] usb 2-2: USB disconnect, address 80
Jun  2 22:24:05 vesta kernel: [  762.973339] usb 2-2: new high speed USB device using ehci_hcd and address 81
Jun  2 22:24:05 vesta kernel: [  763.105618] usb 2-2: configuration #1 chosen from 1 choice
Jun  2 22:24:05 vesta kernel: [  763.518223] usb 2-2: USB disconnect, address 81
Jun  2 22:24:06 vesta kernel: [  764.459561] usb 2-2: new high speed USB device using ehci_hcd and address 82
Jun  2 22:24:06 vesta kernel: [  764.591796] usb 2-2: configuration #1 chosen from 1 choice
Jun  2 22:24:06 vesta kernel: [  764.668541] usb 2-2: USB disconnect, address 82

---

### Post by kerry_s on 2009-06-03
> **nunyez said:**
> I'm using an external USB drive that is plugged in and on all the time. I have rtorrent installed to init.d which fails miserably because the drive doesn't actually mount (I guess..) until I first browse it. Here's a screenshot of my Places menu:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=116194&stc=1&d=1243974310[/IMG]

Note how it is greyed out. After I click it and browse it there is no longer greying in the menu. And now if I restart rtorrent it will see my drive.

My fstab is untouched. Help appreciated.

xubuntu 8.04 hardy

it has to be in /etc/fstab to automount. 

**alt+f2 > gksudo mousepad /etc/fstab**

**/dev/sda?       /media/?               auto defaults          0       0**

you didn't give enough info for the drive so i don't know what to tell you to put.

another way would be just to put an entry in /etc/rc.local

**mount /dev/sda? &**

replace "?" with a actual number.

---

### Post by nunyez on 2009-06-03
Hi kerry_s, thanks for the reply. There is nothing in my fstab relating to my usb disk. My USB hdd is /dev/sdb1 (see ss at bottom) and this is not located in my fstab. I did add the new home partition mount which is just my os drive but the other partition.

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=260ec9bb-ce5d-4486-a68e-36e06093d4a3 /               ext3    relatime,errors=remount-ro 0       1
UUID=98f25365-5e62-4856-a371-b2fb47780b35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# new home partition mount
/dev/sda3 /home ext3 nodev,nosuid 0 2
```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=116279&stc=1&d=1244033180[/IMG]

---

### Post by nunyez on 2009-06-03
Can mount fine with: ```
$ sudo mount UUID=e41ca5bd-a4d2-4fc3-aa82-586080394b36 /media/usb -o auto,users,rw
```

But when I add this to fstab it does not mount unless I use the above command **or** comment this entry out and have it mounted by the sys automatically:
```
UUID=e41ca5bd-a4d2-4fc3-aa82-586080394b36   /media/usb   ext3   auto,user,rw 0 0
```

Is there a way to get the USB hdd that is always plugged in to auto-mount? I've seen posts doing pretty much the same thing I am with success :(  Is the failure logged to syslog or somewhere else? Can't seem to find it amongst the others in syslog

---

### Post by kerry_s on 2009-06-03
you only need it at startup, right?
so use /etc/rc.local, just put:

**mount /dev/sdb1 &**

---

### Post by nunyez on 2009-06-03
> **kerry_s said:**
> you only need it at startup, right?
so use /etc/rc.local, just put:

**mount /dev/sdb1 &**

That's correct. I don't have any problem doing it this way but it annoys me I can't get it with fstab. Do you see something I am doing wrong? Also, the & will run it in the background allowing other events to fire right? It's pretty important the mount is complete before rtorrent starts which is part of my init.d. I don't know or much I like it there so perhaps I'll omit the ampersand and place rtorrents start after my mount. What do you think?

---

### Post by kerry_s on 2009-06-03
for the fstab id go:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=260ec9bb-ce5d-4486-a68e-36e06093d4a3 /               ext3    relatime,errors=remount-ro 0       1
UUID=98f25365-5e62-4856-a371-b2fb47780b35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[B]# usb drive
/dev/sdb1 /media/usb auto default 0  0[/B]

# new home partition mount
/dev/sda3 /home ext3 nodev,nosuid 0 2
```

##note you will have to create a "usb" folder in /media so it can use.##

yes the "&" backgrounds it and lets it continue if there's an error, like if you don't have the drive plugged in, other wise if there's an error your system will just stop. this is the safer bet.

as for rtorrent, if your running it in init.d, it's running as root, big security issue, it has access to your whole system, it should be in your startup with the desktop running as the user.

---

### Post by nunyez on 2009-06-03
> **kerry_s said:**
> for the fstab id go:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=260ec9bb-ce5d-4486-a68e-36e06093d4a3 /               ext3    relatime,errors=remount-ro 0       1
UUID=98f25365-5e62-4856-a371-b2fb47780b35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[B]# usb drive
/dev/sdb1 /media/usb auto default 0  0[/B]

# new home partition mount
/dev/sda3 /home ext3 nodev,nosuid 0 2
```

##note you will have to create a "usb" folder in /media so it can use.##

yes the "&" backgrounds it and lets it continue if there's an error, like if you don't have the drive plugged in, other wise if there's an error your system will just stop. this is the safer bet.

as for rtorrent, if your running it in init.d, it's running as root, big security issue, it has access to your whole system, it should be in your startup with the desktop running as the user.


It's actually running as it's own user with limited privs. It's one of the startup scripts found on rtorrents common tasks page. I'll see if your fstab gives me any luck. But even still which combination do you think? 
1. Fstab assuming it'll work plus rtorrent init.d
2. Mount and rtorrent start as part of rc.local
3. Some other combination?

---

### Post by kerry_s on 2009-06-03
no, thoughts. go with what works the most dependable for you.

---

### Post by nunyez on 2009-06-04
> **kerry_s said:**
> for the fstab id go:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=260ec9bb-ce5d-4486-a68e-36e06093d4a3 /               ext3    relatime,errors=remount-ro 0       1
UUID=98f25365-5e62-4856-a371-b2fb47780b35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

[B]# usb drive
/dev/sdb1 /media/usb auto defaults,users 0  0[/B]

# new home partition mount
/dev/sda3 /home ext3 nodev,nosuid 0 2
```

##note you will have to create a "usb" folder in /media so it can use.##


Not sure if I believe my eyes, but that worked. Fixed your default typo to defaults and added users otherwise "only root can mount" would appear. I don't know if it was the auto on filesystem type or if it was the placement before my new home directory, but thanks!

---

### Post by baeda on 2009-06-09
> **nunyez said:**
> Can mount fine with: ```
$ sudo mount UUID=e41ca5bd-a4d2-4fc3-aa82-586080394b36 /media/usb -o auto,users,rw
```

But when I add this to fstab it does not mount unless I use the above command **or** comment this entry out and have it mounted by the sys automatically:
```
UUID=e41ca5bd-a4d2-4fc3-aa82-586080394b36   /media/usb   ext3   auto,user,rw 0 0
```

Is there a way to get the USB hdd that is always plugged in to auto-mount? I've seen posts doing pretty much the same thing I am with success :(  Is the failure logged to syslog or somewhere else? Can't seem to find it amongst the others in syslog

Adding this to /etc/fstab worked for me fine:
```
UUID=e41ca5bd-a4d2-4fc3-aa82-586080394b36   /media/usb   ext3   auto,user,rw 0 0
```

---

