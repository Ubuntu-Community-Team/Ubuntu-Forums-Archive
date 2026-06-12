---
title: "auto-mounting external usb drive by uuid to specific folders?!"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by stani on 2006-10-18
Hi,
I have an external drive with two partitions (ext3+fat32) which I want to be recognized when they are mounted automatically and be mounted to specific folders (/media/backup /media/current).I didn't succeed. It still mounts as usbdisk and usbdisk-1. I thought I needed to use the uuid, which I got through blkid.

I tried with fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=40b5a0b3-5650-4b39-a45a-1d9cdd5bd036 	/               ext3    	defaults,errors=remount-ro 	0       1
# /dev/sda5
UUID=7d84e133-3d8b-448a-a7dc-1074cf24a8e2 	none            swap    	sw              		0       0
/dev/hdb        				/media/cdrom0   udf,iso9660	user,noauto     		0       0
/dev/           				/media/floppy0  auto    	rw,user,noauto  		0       0
#usb disk
UUID=2445b2ea-ddfd-4af1-b14b-e68eb1930ce8 	/media/backup   ext3    	rw,user,noauto 			0       0
UUID=4536-A4D8 					/media/current 	vfat    	rw,user,noauto 			0       0
```

I also tried with a hal policy (/etc/hal/fdi/policy/10-local.fdi):
```
<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="volume.uuid" string="2445b2ea-ddfd-4af1-b14b-e68eb1930ce8">
      <merge key="volume.label" type="string">/media/backup</merge>
    </match>
  </device>
</deviceinfo>
```

Anyone knows what I should do? When I do it manually, it works fine:
```
sudo mount /dev/sdb5 /media/backup
```

... but I'd like to let it work when I plug and unplug my hard drive.

Stani

---

### Post by kidders on 2006-10-18
Hi there,

I've never tried to do this the way you outlined, but it seems odd to me that it didn't cooperate for you :-( I thought I'd describe how *I* would do it, in case it offers you more succcess. Your way might well be prettier, though!

[LIST=1]
[*]Read about udev
[*]Create a udev rule keyed to the actual device's UID (rather than the filesystems' UUIDs), instructing udev to create static /dev entries for your device.
[*]Modify /etc/fstab to refer to the new /dev entries.
[/LIST]

I do this with my iPod, for instance. When I plug it in, I get /dev/ipod1, /dev/ipod2... (one for each partition). Now, since my /dev entries no longer depend on the order I plug my USB devices in in (in in :confused:), I can construct things like:

```

/dev/ipod3 hfs /mnt/ipod defaults 0 0

```

Any help?

---

### Post by qpieus on 2006-10-18
kidders is on the money. Here's a link to a thread where someone wanted mount his ipod to a certain folder.
[http://ubuntuforums.org/showthread.php?t=251615](http://ubuntuforums.org/showthread.php?t=251615)
In there I posted a link to a thread that has some good info on udev rules:
[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by kidders on 2006-10-18
> **qpieus said:**
> kidders is on the money.Wheee :-) I wasn't quite sure whether to expect the next poster to say "You idiot!".

---

### Post by qpieus on 2006-10-18
> **kidders said:**
> Wheee :-) I wasn't quite sure whether to expect the next poster to say "You idiot!".
Nah, I don't know enough to call anyone an idiot!

---

### Post by stani on 2006-10-19
Thanks a lot, I'll look into it.

Stani

---

