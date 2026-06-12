---
title: "SD card size reported incorrectly"
date: 2011-07-01
forum: Hardware
---

### Post by marlon_smith on 2011-07-01
Hi everyone,

I'm having a problem with a 256 MB SD card that I'm using with Ubuntu.  I believe I created the problem when I emptied the card and used dd to copy a binary image onto it.  Now, I can't seem to recover the space that that image is taking up (about 11 MB).

GParted reports the card as being about 238.5 MB in size, but if I do a "dd if=/dev/zero of=/dev/mmcblk0", dd reports that it successfully wrote 250MB (250085376 bytes) to the device (which is what I would expect).  GParted also gives me a warning when I get information on the card: "/dev/mmcblk0: unrecognized disk label".  I'm not sure if that has anything to do with it.

Does anyone have any ideas?

Thanks!

Marlon

---

### Post by Ranko Kohime on 2011-07-01
> **marlon_smith said:**
> Hi everyone,

I'm having a problem with a 256 MB SD card that I'm using with Ubuntu.  I believe I created the problem when I emptied the card and used dd to copy a binary image onto it.  Now, I can't seem to recover the space that that image is taking up (about 11 MB).

GParted reports the card as being about 238.5 MB in size, but if I do a "dd if=/dev/zero of=/dev/mmcblk0", dd reports that it successfully wrote 250MB (250085376 bytes) to the device (which is what I would expect).  GParted also gives me a warning when I get information on the card: "/dev/mmcblk0: unrecognized disk label".  I'm not sure if that has anything to do with it.

Does anyone have any ideas?

Thanks!

Marlon
I've never had any success with GParted, though that may be the foreign-ness of the interface to me.  Does Palimpsest report anything different for you?

Also, given that it's 256MB, which would make it significantly aged, it's entirely possible that the card itself is on it's last legs.

---

### Post by marlon_smith on 2011-07-01
Thanks for the quick response.  Palimpsest reports it having the same free space as dd (250 MB), and allows me to format it.  Once it's formatted, I see 238.2 MB of free space.  Does that make sense?  Does it use 12MB to format (with FAT) a 250MB filesystem?

Strangely, GParted still shows the drive as being 238 MB total.  If I format it with GParted, I see 233.3 MB after.  So it seems GParted thinks the drive is smaller than it is, but uses half the space for the file tables once formatted.

Weird.  Could this be a bug in GParted?

---

### Post by coffeecat on 2011-07-01
The confusion is between megabytes (MB) and mebibytes (MiB).

250 MB = 238.4 MiB

[http://en.wikipedia.org/wiki/Megabyte](http://en.wikipedia.org/wiki/Megabyte)

[http://en.wikipedia.org/wiki/Mibibyte](http://en.wikipedia.org/wiki/Mibibyte)

Although there is also confusion about exactly what a megabyte is. Put simply, manufacturers quote their hard drive sizes in megabytes, in the metric (scientifically correct) definition of the prefix mega. So 1 megabyte = 1,000,000 bytes. 1 mebibyte = 1048576 bytes.

Have a look closely at what Gparted is telling you. Gparted reports in MiB, not MB. (Or GiB, not GB).

---

### Post by Ranko Kohime on 2011-07-02
> **marlon_smith said:**
> Thanks for the quick response.  Palimpsest reports it having the same free space as dd (250 MB), and allows me to format it.  Once it's formatted, I see 238.2 MB of free space.  Does that make sense?  Does it use 12MB to format (with FAT) a 250MB filesystem?
It has been my experience that the formatted capacity is significantly reduced, regardless of the filesystem formatted to.

Also, what coffeecat said.

---

### Post by marlon_smith on 2011-07-04
Right, of course.  Thanks guys, I appreciate it.

Marlon

---

