---
title: "editing fstab"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by JulesH on 2005-06-11
Hi,

When I try to use Totem on my IBM T21 to play DVD's, I get the folllowing message:

"Failed to find mountpoint for device /dev/hdd in etc/fstab".

Looking in fstab, there is no entry for the CD-RW/DVD-ROM I am using for playing DVD's etc. but there is an entry for a CD-ROM drive, (which Ubuntu was installed from), which I use for booting from CD (the CD-RW/DVD-ROM is not bootable on my machine).

How do I add the correct entries for this drive?


My fstab currently looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

The drive I want to add is a Sony CD/RW/DVD-ROM type CRX820E.

I tried to add a new entry:
/dev/hdd        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0

or:

/dev/hdc        /media/cdrom1   udf,iso9660 rw,user,noauto  0       0

Neither work, and I get the following error message when I try to play a DVD: "Error 8192".

What's up?

Regards,
Jules

---

### Post by Xian on 2005-06-11
[QUOTE=JulesH]I tried to add a new entry:
/dev/hdc /media/cdrom1 udf,iso9660 rw,user,noauto 0 0[/QUOTE]

Have you verified that there is a cdrom1 path?

```
$ sudo mkdir /media/cdrom1
```

---

### Post by JulesH on 2005-06-11
Thanks, I added the path you gave, now Totem goes a step futher, and now I get this error message:

"Totem could not play 'DVD://'. There were no decoders found to handle the stream in file "DVD://, you might need to install the corresponding plug-ins".

Which plug-ins I need, I don't know yet.

Jules

---

### Post by voidlogic on 2005-06-11
I always grab all gstreamer and vlc plugins. VLC seems to work much better than totem (and crash less) in my experence. I would venture to say your current issue is plugins. Try googling it, I help a kided in my dorm last year, and we found how to install DVD codecs by googling it. Sorry I can't be more specific. It can be done, Good Luck.  ;-) 

voidlogic

---------------
I need HELP! 
[http://www.ubuntuforums.org/showthread.php?p=202288#post202288](http://www.ubuntuforums.org/showthread.php?p=202288#post202288)
 ](*,)  ](*,)  ](*,)

---

### Post by Alexander Kirillov on 2005-06-11
[QUOTE=JulesH]Thanks, I added the path you gave, now Totem goes a step futher, and now I get this error message:

"Totem could not play 'DVD://'. There were no decoders found to handle the stream in file "DVD://, you might need to install the corresponding plug-ins".

Which plug-ins I need, I don't know yet.

Jules[/QUOTE]
 Remove totem-gstreamer and istall totem-xine instead. Also install libdvdcss2. See instructions at 
ubuntuguide.org

---

