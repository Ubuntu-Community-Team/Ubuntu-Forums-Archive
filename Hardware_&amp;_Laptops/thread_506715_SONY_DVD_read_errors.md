---
title: "SONY DVD read errors"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by Little Jawa on 2007-07-22
Hello all,

 I have recently (two weeks ago) installed Ubuntu Feisty Fawn, and I am pretty happy with it.
 My only remaining problems are for my webcam (wich is clearly not (yet) supported), and my DVD drive.
 For this one, I need help, because all what I tried remained unusefull.

 First : my DVD is a SONY DW-Q120A
 It is plugged as secondary master on the IDE controller. There is nothing in primary IDE, and nothing as slave on secondary IDE. My hard drive is on SATA1.
 When I look the "Hardware information" tool in gnome interface, the drive is correctly listed under the IDE controller, but is is viewed as "SCSI device", and actually the fstab entry for it lists it as "scd0" instead of "hdc".

 Now the problem : whatever CD I put in the drive is seen. The CD is mounted, be it at boot time or during normal usage. I can see the drive, with correct drive name, and I can browse the content. I can even see audio CD and SoundJuicer can recognize audio CDs name and track names... until here, the world is beautiful.

 It turns ugly when I try accessing data in the disk : files appear corrupted, at the best. Most of the time, the system will issue errors like "the file extension pretends to be [filetype] but is actually plain text" and refuses to open the file.
 Basic text files actually opens well (as far as I can tell), but others (bitmaps, PDF, even Audio tracks being played) are corrupted.

 I made tests with multiple CDs, including the Ubuntu LiveCD I made the installation from.
 Wich points me to the first question : why does the LiveCD correctly boots and access itself ? I tested accessing the very same file when booting from the CD, and it works well. When I boot from hard drive and access the CD, everything is corrupted.
 What options does it use that is not set in my hard drive installation, and how could I put this same setting, as it seems to work ?

 I have tested multiple things, like modifying fstab to use HDC instead of scd0, but the result is exactly the same (CD are still mounting automatically anyway...).
 I used different filesystems and charsets in fstab. Some of them prevented the CD mounting. Others just gave the same errors. I know reverted to the default settings I had after installation, except for hdc replacing scd0

 Can anyone give me hints ? What can I check ?
 Is there a way to put a "standard driver" instead of any specific one ? Even if the burner function don't work, I'd like to - at least - access my CDs, for beginning. It will always be time to work it out later when I need to burn something.

 Any help is appreciated.

 Regards,
 Little Jawa

---

### Post by vanadium on 2007-07-22
The issues you list are strange and point to software issues rather than a hardware problem. My DVD RW drive ( in a portable) is also Sony, the fstab line looks like

```

/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

```

Con you copy data to your hard drive and then access it normally?

---

### Post by Little Jawa on 2007-07-22
Thanks for answering. I really appreciate any help.

> **vanadium said:**
> 
```

/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

```


Tried it also, with no success

> **vanadium said:**
> Con you copy data to your hard drive and then access it normally?

No. I tried copying one file from the Ubuntu LiveCD (the "start.bmp" image standing at the root), and I get "I/O error, do you want to retry ?". It is repeated as long as I click "yes".
The resulting copy is corrupted.

On the same topic : I tried booting from my Windows partition and copy the content of the CD to the hard drive. Then, this data is fully accessible from Ubuntu... I just wanted to make sure the problem did not come from the CD itself.

---

### Post by Little Jawa on 2007-07-25
How can I know wich driver is used for my DVD ?
 How can I change it to a "generic" one, such as the one used by the LiveCD ?
 I know I would probably not be able to burn anything with such driver, but accessing my CDs would be a good start...

---

### Post by Little Jawa on 2007-08-01
When I boot from the LiveCD and look at the "Hardware information" data, the DVD drive is seen as an IDE device.
 When I boot from the hard drive, it is listed as SCSI device.

 From what I understand, this is because my drive is a CD burner, and then must use "SCSI emulation" or something like that. Since the LiveCD can access the CD, is it possible that this SCSI emulation makes the CD unreadable ? If so : how can I deactivate it ?

---

