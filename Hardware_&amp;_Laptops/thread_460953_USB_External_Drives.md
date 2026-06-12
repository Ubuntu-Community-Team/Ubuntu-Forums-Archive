---
title: "USB External Drives"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by Man_Beach on 2007-06-01
I'm considering buying one of the cheap external hard drives such as the Maxtor 60GB OneTouch III Mini Edition or Freecom Mobile 60GB 2.5" Hard Drive [http://www.amazon.co.uk/Freecom-Mobile-Drive-USB-2-silver/dp/B000GTO9JS/ref=pd_sbs_ce_2/026-4698103-2104434](http://www.amazon.co.uk/Freecom-Mobile-Drive-USB-2-silver/dp/B000GTO9JS/ref=pd_sbs_ce_2/026-4698103-2104434) 

I only want to use it for backups (this is because I recently found that one of my backup CDs that I'd made was faulty - luckily I had an earlier backup with the data I wanted on it). Am I right in thinking that they can just be plugged in, like a USB  memory stick and will automount? And I can just copy stuff over then unmount it, unplug and put it back on the shelf ready for the next time I want to make another backup? (I presume that I'd probably need to format it first?)

---

### Post by hollowhead on 2007-06-01
Yes I've got a fujistu handydrive for the same purpose and in dapper this worked like a usb stick.   Must try it in feisty.   Hope this helps.

---

### Post by Man_Beach on 2007-06-01
Great. Should be just the job. Thanks, hollowhead.

---

### Post by jawrat on 2007-06-07
weeeeeelllll...

I just got a maxtor onetouch III 60Gb drive and plugged it in to my ubuntustudio 7.04 laptop and while it mounts, apparently the filesystem on it is NTFS and it mounts read only :(

I think i need to edit /etc/mtab or something...i'll figure it out.

---

### Post by logos34 on 2007-06-07
> apparently the filesystem on it is NTFS and it mounts read only 

That's because Linux ext3 does not natively support writing to NTFS--you need a special driver for that. (ntfs-3g)

---

### Post by Man_Beach on 2007-06-08
I don't think that'd be a problem for me.  I'd just re-format it to something more useful.

---

