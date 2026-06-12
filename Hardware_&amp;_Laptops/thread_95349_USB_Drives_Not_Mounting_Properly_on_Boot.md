---
title: "USB Drives Not Mounting Properly on Boot"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by sailor420 on 2005-11-26
I have two USB hard drives plugged into a PCMCIA card. Ubuntu detects them just fine, and I added the entries into /etc/fstab so that they should automatically mount themselves on boot. However, this doesn't happen for some reason--but if I unplug them, and then plug them back in and mount -a, they mount up just fine.

It seems to me like it's a problem with the order it tries to mount them, as one of the drives is NTFS and one is EXT3, and the entries in /etc/fstab assume sda is NTFS, and sdb is EXT3. So I tried switching that to see if it fixed it, to no avail. So I tried switching the plugs they were plugged into, to see if it was mounting them based on which plug it was plugged into. Still nothing.

Any ideas? It's a little annoying having to mount -a every boot.

The relevant lines of /etc/fstab are:

```

/dev/sda1	/mnt/usb1	ntfs	nls=utf8,umask=0222	0	0
/dev/sdb1	/mnt/usb2	ext3	defaults	0	0

```

---

### Post by Mustard on 2005-11-26
I'd read this thread and see if it was relevant.

[http://www.ubuntuforums.org/showthread.php?t=77141](http://www.ubuntuforums.org/showthread.php?t=77141)

---

### Post by sailor420 on 2005-11-27
That seems to be a different problem. They actually do mount themselves on boot, just not where they are supposed to be mounted, so nothing works...

---

### Post by lisje on 2005-11-27
the problem is that usb-harddrives are mounted by hotplug... at least mine are 
because of that they are not mounted the way it is written in fstab :(
it sucks bigtime if you ask me :(

---

### Post by sailor420 on 2005-11-27
[QUOTE=lisje]the problem is that usb-harddrives are mounted by hotplug... at least mine are 
because of that they are not mounted the way it is written in fstab :(
it sucks bigtime if you ask me :([/QUOTE]

So then is there anyway to control how they are mounted?

---

### Post by lisje on 2005-11-28
Okay here is what I found... I had to install my ubuntu again yesterday and this time I had my usb-harddrive plugged in and turned on (while installing). Appearantly now my drives do not mount anymore with hotplug.
They are still mounted but seemingly not with hotplug anymore.
So I was able to define a mount point for my usb-drive in fstab.

the problem that I can not change the names of the drives on my desktop still remains for me. But I'll have to live with that I think.

---

