---
title: "USB Pendrive automount stopped working!"
date: 2006-05-20
forum: Hardware &amp; Laptops
---

### Post by jon_benge on 2006-05-20
Hi guys

Unfortunately the USB pendrive automount function in Ubuntu has ceased working! :( The device icon no longer appears on the desktop.

A summary of what happens:

If I plug my pendrive into the USB port, nothing shows up on the desktop. If I click on 'Places' then 'Computer' it actually shows up under 'SigmaTel MSCN Music Player'. So I know that the device is being detected.

However, If I double click 'SigmaTel.....' then I get the following error message:

```
"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted".
```

If I click 'Show more details', then i get the following:

```
"mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount"
```

The pendrive is formatted in vfat if that helps?

Anyway, as I said, it used to automount fine. So I must have done something to kill it off. But what??

For the moment I have implemented a workaround. I have added an entry in FSTAB that looks like this:

```
/dev/sda1       /media/pendrive vfat    noauto,rw,user,iocharset=utf8,umask=000 0       0
```

'Pendrive' shows up in 'Computer' and I can mount it if I double click it. When I do this, the icon shows up on the desktop. However, not the nice IPOD icon that used to show up! :???: 

Any ideas?

---

### Post by jon_benge on 2006-05-28
Does anyone know why my USB automount has stopped working?

please!!! :neutral:

---

### Post by PapaWiskas on 2006-05-30
OK here is what I did to fix my issue.
This is all taken from my history in synaptic....keep in mind, I am not an expert, but I did fix my problem after reading and trying a bunch of stuff on automounting that did not work....so I did this myself, now my USB and CDROMS/DVDS automount fine and show icons on the desktop.

Here is the first thing I did...

Completely removed the following packages:
hal

Removed the following packages:
gnome-power-manager
gnome-session
hal-device-manager
hwdb-client

Then I did the following...
Installed the following packages:
gnome-power-manager (2.14.3-0ubuntu11)
gnome-session (2.14.1-0ubuntu11)
gnome-utils (2.14.0-0ubuntu5)
gnome-volume-manager (1.5.15-0ubuntu10)
hal (0.5.7-1ubuntu1
hal-device-manager (0.5.7-1ubuntu1
hwdb-client (0.6-0ubuntu10)

And now everything works again, dont ask me how or why because I dont know.

---

