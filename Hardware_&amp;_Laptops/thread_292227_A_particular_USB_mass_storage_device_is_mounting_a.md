---
title: "A particular USB mass storage device is mounting as read only"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by articnomad on 2006-11-03
I'm trying to get my iAudio X5 to mount as read and write on Ubuntu 6.10. Unfortunately, it "appears" as if the device is mounted as read only. I've tried mounting as read+write but still that doesn't seem to work. I'm sure it's not a problem with the device, as read and write worked fine on my sisters Windows laptop. Does anyone have any suggestions?

---

### Post by Jussi Kukkonen on 2006-11-03
> I've tried mounting as read+write but still that doesn't seem to work. 
Details about that would help... the mount commands (or /etc/fstab), what's in etc/mtab, etc.

---

### Post by articnomad on 2006-11-03
Command used:

```
sudo mount -a
```

etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=d5b45984-1282-4d74-96e8-8e2f5fa51ecb / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=6a520457-be93-4589-9205-12d03fd5fb03 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /mnt/usb0       vfat    umask=002      0      0
```

---

### Post by articnomad on 2006-11-09
Even after reinstalling Ubuntu problem persisted. Switched to Kubuntu and everything works fine now.

---

### Post by tictactatic on 2006-12-20
Glad your switch to Kubuntu did the trick, but I am under Kubuntu, and am experiencing the same problem with the X5. Any idea what fixed your problem?

---

### Post by SZF2001 on 2007-01-04
Is there a way to just format a USB mass storage device, from the terminal or something?

---

### Post by ssm on 2007-01-04
--------------------------------------------------------------------------------

Hello,

Can someone please tell me if the diNovo Edge from Ligtech works in Linux or not?

I would like to know if it works in Edgy.
HELP: [www.unreadedpost.com]("www.unreadedpost.com")

---

### Post by botezuma on 2007-01-09
hi,
I can mount my IAudio X5L on Ubuntu 6.10 but after I move files from it by using Windows XP and then connect it to the computer using Ubuntu it shows me the amount of space is not freed but ... vanished. It now has just 15 Gb total space. Can anyone help please?

---

