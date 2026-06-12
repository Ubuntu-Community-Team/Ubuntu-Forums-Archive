---
title: "Moving Filesystem to a Different Drive"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by BitTorrentBuddha on 2006-05-21
Would it be possible using (slightly modified) directions from [this tutorial](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) to move my root partition and home partition to a different drive? What would be the risks involved in doing this?

---

### Post by tonyr on 2006-05-21
Moving the root partition is not as straightforward as that tutorial describes.  A
straight copy is definitely out of the question, and it is best done when booted
from some other kernel, like the rescue mode in a Dapper install cd or a
Live CD (in Breezy; I'm not sure Dapper has one yet).  There are several
hands-on modifications that must be done, including **/etc/fstab** entries
and **GRUB** reinstallation (or **LILO**, if your are using that).  

Many say simply reinstalling Ubuntu on the second drive is a much easier
and less risky way to go, and that is way I have chosen to do it in the past.

---

### Post by BitTorrentBuddha on 2006-05-23
would moving my home partition to a separate drive be easy though (I'm assuming yes)

---

### Post by tonyr on 2006-05-23
Yes indeedy.  The tutorial works for that.  Just substitute the correct path names
for your particular setup.  Your second drive will be mounted somewhere (on my
Dapper system all partitions show up mounted on directories in **/media**).  You will
need to make appropriate modifications to **/etc/fstab** to mount your new **home**
partition on **/home**.

---

### Post by BitTorrentBuddha on 2006-05-23
One more question while we're on the topic. When I was installing stuff on my motherboard I mixed up the IDE ribbons (my cd-rw drive is listed as hda, my harddrive as hdb) if i were to switch the ribbons around on the motherboard, all I would need to change is /etc/fstab from hdb1 as the root partition to hda1, power down, switch the cables, and power back on, right? (It just kind of bugs me that my hard drive is on my secondary IDE interface)

---

### Post by tonyr on 2006-05-23
I think there are ramifications for **grub** in there, too.  The **menu.lst** file has a
particular mapping terminology for device names.  I've been using **lilo** recently,
so I don't have the details at my fingertips.  In the worst case you might have
to redo the **grub** installation.  At the very least you would have to modify
the device/partition specs in **menu.lst.**  Research this very carefully before
you do anything.  You could end up not being able to boot from the hard drive
at all.  Have a fallback plan (i.e, know how to boot in rescue mode from an
install cd or live cd).

---

### Post by BitTorrentBuddha on 2006-05-23
In that case, forget it, it's just a mild annoyance lol.

---

