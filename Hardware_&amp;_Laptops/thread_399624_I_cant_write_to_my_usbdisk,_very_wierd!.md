---
title: "I cant write to my usbdisk, very wierd!?"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by Peter Sommer-Larsen on 2007-04-02
Hey.
I have made a program which generates data-files. I would like to move these datafiles
to another computer which controls a laser.
My problem is the following:

I stick my USBdisk into my computer (I have tried with others USBdisk too). Edgy finds
it and mounts it, calling it "sda1". I can now browse the disk seeing all the files, and
I can copy whatever I want to, to the disk.

The problem is just, that when I stick it into the other computer, all the data, that i copied
over is gone..!!!? That is just so weird. It even gets better... If I am very very lucky, 
sometimes i copies the files..!

Does some of you people know what could be wrong.

I also tried to do the following: (I suspect it has something to do with the mouting
of the disk)

$ sudo umount /media/usbdisk
$ sudo mount /dev/sda1 /media/usbdisk/ -t vfat -o iocharset=utf8,umask=000


Thx.
Peter

---

### Post by yabbadabbadont on 2007-04-02
Did you right-click on the disk and take the eject option before you removed it?

---

### Post by Peter Sommer-Larsen on 2007-04-02
Do you mean umount ? No i didnt. I just talket with a friend who said that
sometimes xubuntu can copy things to the usb without showing. But that is not 
the problem in my case, because my files are small.

---

### Post by yabbadabbadont on 2007-04-02
You must always guarantee that the USB disk is properly umounted before removing it.  Using the Eject option on the right-click menu does that.  If you don't, there is the very good possibility that the files you have copied are still sitting in the filesystem cache and have not yet been flushed to the disk.  It is also likely that you will eventually corrupt the filesystem on the USB disk.

---

### Post by Peter Sommer-Larsen on 2007-04-03
> **yabbadabbadont said:**
> You must always guarantee that the USB disk is properly umounted before removing it.  Using the Eject option on the right-click menu does that.  If you don't, there is the very good possibility that the files you have copied are still sitting in the filesystem cache and have not yet been flushed to the disk.  It is also likely that you will eventually corrupt the filesystem on the USB disk.

Ok thx mate.. it seems like its working..

---

### Post by Peter Sommer-Larsen on 2007-05-07
Yes now it works fine every time. Just run the command.

# sudo umount /media/usbdisk

it is now allways that it is called "usbdisk". Run the command
# ls -l /media 
to see what possible name are available.

---

