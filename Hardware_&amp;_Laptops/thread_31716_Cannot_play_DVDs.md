---
title: "Cannot play DVD:s"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by Ces on 2005-05-04
Firstly, I've tried looking for an answer in both these forums and the wiki, though no answer could be found by me...

I've just bought and inserted a DVD-player (Lite-On LTD 166 S). Though, when I insert a DVD or CD nothing happens. No link on the desktop, no folder opening (as was the case with my CD-player). Any ideas?

Perhaps (un)relevant notes: I also have a CD-burner, and Hoary was updated to from Warty.


cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by Xerampelinae on 2005-05-04
My preferred method.  There are many programs that play dvds (you could use totem instead of xine)

```

sudo apt-get install libdvdcss2 xine-ui
xine  (then click on dvd in the little toolbar thing)

```

The important thing is to install libdvdcss2.

---

### Post by Ces on 2005-05-04
I've installed those packages, and running xine gives:

> The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: not disc in drive). (/dev/dvd)

And yes, I have a disc in the drive.

---

### Post by Ces on 2005-05-04
Well, if I was to install a new drive (e.g. a DVD drive as is the case for me right now), how would I know

1. if the drive has been set up correctly,
2. what the new drive is called, and
3. if the old drive (which the new one replaced) is completely removed from the system?


If you couldn't guess, I'm fairly new at tinkering with Linux. *smiles*

---

### Post by Ces on 2005-05-04
I've been trying a lot of things, here is a break-down of some of them.

1. created **/media/dvd -> cdrom0**

/media/cdrom -> cdrom0
/media/cdrom0
/media/dvd -> cdrom0
/media/floppy -> floppy0
/media/floppy0


2. created **/dev/dvd -> /dev/hdc**

/dev/dvd -> /dev/hdc
/dev/hda
/dev/hda1
/dev/hda2
/dev/hda5
/dev/hdd

[COLOR=DarkGreen]*QUESTION: How do I get **/dev/hdc** to exist?*[/COLOR]


3. in **/etc/fstab** this drive(?) exists:

> /dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

4. but in **/etc/mtab** I cannot find it at all:

> /dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
[COLOR=DarkGreen]*QUESTION: Something I need to change/do?*[/COLOR]

---

### Post by Xerampelinae on 2005-05-04
Does the bios recognize this drive?  Does it display it as found when you boot?

Try putting the DVD drive as the secondary master IDE, with no secondary slave.  Just to test.  (that is, remove your cd drive and make the DVD the master).

I've never had to do anything special for an IDE device to work... can you boot from a cd with it?  If not, I think it's a hardware problem.

---

