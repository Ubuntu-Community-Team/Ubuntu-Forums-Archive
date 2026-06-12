---
title: "Anyone using JFFS2 partitions (for flash media) with Ubuntu?"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by DaBruGo on 2006-04-13
Just curious,

I was thinking about using that partition format to load Ubuntu onto a usb memory stick ... if I can find out if Ubuntu supports it.


DAVE

---

### Post by CrazyGuy123 on 2008-03-13
Digging up an old topic I know, but is it now possible?

---

### Post by paxmark1 on 2008-06-09
bump

---

### Post by jfernyhough on 2008-06-11
Nope. :)

[quote=http://linux-mtd.infradead.org/faq/jffs2.html#L_hdd_jffs2]I am going to use JFFS2 on top of my USB stick/CF card/etc, is it OK?

USB sticks, CompactFlash cards and other removable flash media are not MTD devices. They are block devices. They do contain flash chip inside, but they also contain some translation layer above which emulates block device. This translation layer is implemented in hardware. So for outside world these devices look exactly as hard drives, not like MTD devices.

Please, read this FAQ entry about using JFFS2 on top of hard drives.

So, the answer is probably yes, you technically can, but be sure you realize why you do this. In general it is bad idea. It is much better to use any conventional file system like ext2.

Also note, these devices are "black boxes". The way they implement this flash-to-block device translation layer is not usually published. And in many cases the algorithms used at this layer are far from brilliant. For example, many USB sticks and other cards lose data in case of unclean reboots/power cuts. So, be very careful. [/quote]

Hmm... maybe I should just write [http://linux-mtd.infradead.org/faq/jffs2.html#L_hdd_jffs2](http://linux-mtd.infradead.org/faq/jffs2.html#L_hdd_jffs2).

Essentially USB pens etc. have a controller built-in that performs wear-levelling etc. So apparently any old (non-journalling?) filesystem will do the job.

---

### Post by paxmark1 on 2008-06-14
thanks for the info.  looks like ext2 would work. 
tired of rsync; mc and other file managers complaining about permissions of usb sticks.
 Read alot of web pages, on jffs2 but the one listed really is well done.

---

