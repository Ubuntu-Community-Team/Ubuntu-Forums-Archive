---
title: "Can't eject CD tray on Intrepid."
date: 2008-12-13
forum: Hardware
---

### Post by mmcmonster on 2008-12-13
When I boot up Intrepid, the ejct button works the first time.  Light pressure on the CD drive doesn't retract the tray, however, and hitting the button again doesn't work, either.  I have to reboot the system to get it to work again.

[COLOR=DarkOrange]BTW, there is no CD or DVD in the drive.[/COLOR]

```

 eject -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/media/cdrom'
eject: `/media/cdrom' is a link to `/media/cdrom0'
eject: `/media/cdrom0' is not mounted
eject: `/dev/scd0' can be mounted at `/media/cdrom0'
eject: `/dev/scd0' is not a multipartition device
eject: trying to eject `/dev/scd0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/scd0' using SCSI commands
eject: SCSI eject succeeded

```

It says the eject succeeded, but it really didn't.

```
$ sudo lshw -C disk
*-cdrom
       description: DVD reader
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd
       configuration: status=open

```

---

### Post by donmiguel on 2009-03-24
i have the exact same problem!!
did you manage to overcome this? Please give some feedback
cheers

---

### Post by myxiplx on 2009-04-02
Same here, it's been working absolutely fine, but today for whatever reason I can't eject the tray at all.

---

### Post by donmiguel on 2009-04-03
is your light on the disk-tray working or not? mine's not....

---

