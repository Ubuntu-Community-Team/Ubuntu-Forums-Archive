---
title: "My /dev/hdc DVD drive is mounted on /media/usbdisk ???"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2007-01-22
I have 3 optical drives in my system (all IDE):
[LIST]
[*]/dev/hda (ide0 channel 0) - DVDRW drive
[*]/dev/hdb (ide0 channel 1) - CDRW drive
[*]/dev/hdc (ide1 channel 0) - DVDROM drive
[/LIST]
When media is inserted, they get automatically mounted as follows:

[LIST]
[*]dev/hda (DVDRW)     => /media/cdrom0
[*]/dev/hdb (CDRW)      => /media/cdrecorder
[*]/dev/hdc (DVD-ROM) => /media/usbdisk
[/LIST]

Hmmm... I can live with that a DVDRW drive is mapped to a "cdrom" slot (cdrom0).
But... a DVD-ROM mapped to a usbdisk ???

There must be a confustion here, right?

How do I make /dev/hdc map (by default, as the system knows how to do automatically with /dev/hda and /dev/hdb) to something like /media/cdrom2 ?

Is there a way to accomplish that?

Thanks,
Alex

---

### Post by xp_newbie on 2007-01-22
Hmmm... No real answer yet, but I think that I am getting there: I just discovered the documentation for the Linux Filesystem Hierarchy which seems to explain what's going in the /media directory:  [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/media.html]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/media.html")

More specifically, it says:

> The following directories, or symbolic links to directories, must be in /media,
if the corresponding subsystem is installed:

floppy - Floppy drive (optional)
cdrom - CD-ROM drive (optional)
cdrecorder - CD writer (optional)
zip - Zip drive (optional)


Now... in my system there is cdrecorder and cdrom (link to cdrom0) but no cdrom1... Instead there is only usbdisk. The automounter picks usbdisk, for lack of cdrom1, instead.

Any idea how the automounter works? Where can I read about it?

Thanks,
Alex

---

