---
title: "External USB Hard Drive for Linux Installation"
date: 2014-03-27
forum: Hardware
---

### Post by KAWill70 on 2014-03-27
I'm looking for suggestions on External USB Hard Drives for installing Linux.

I was just about ready to order a 500 GB Western Digital Passport drive until I read that it has hidden partitions and can be very difficult to reformat.  Would Seagate or some other vendor be a better choice?  Does the Passport Drive actually have a potential problem with that hidden partition?

---

### Post by jp734 on 2014-03-27
I had an extra ide hard drive so I just purchased an enclosure for it using USB connection. Works like a charm. Would recommend if you have extra ide or sata drive just sitting around somewhere.

---

### Post by houstonbofh on 2014-03-28
While it is actually trivial to remove, I refuse to support companies that treat customers as product and don't really want you to own the stuff you buy.  So, white box it...

Here are two USB 3.0 laptop drive enclosures...
[http://www.directron.com/tl202u3bk.html](http://www.directron.com/tl202u3bk.html)
[http://www.directron.com/ec25ap.html](http://www.directron.com/ec25ap.html)

And a fast 500gig Hitachi drive...
[http://www.directron.com/0j26005.html](http://www.directron.com/0j26005.html)

All in for about $60 USD.

---

### Post by sudodus on 2014-03-28
> **KAWill70 said:**
> I'm looking for suggestions on External USB Hard Drives for installing Linux.

I was just about ready to order a 500 GB Western Digital Passport drive until I read that it has hidden partitions and can be very difficult to reformat.  Would Seagate or some other vendor be a better choice?  Does the Passport Drive actually have a potential problem with that hidden partition?

I think most USB drives can be reformatted with ***gparted***. A hidden partition is probably not a problem.

But I agree with the previous posts, that it is a good idea to get a standard hard disk drive and put it into an enclosure with USB 3 or {USB 2 plus eSATA] connections.

See also this link for general information about creating a USB boot drive (it applies to HDDs and SSDs too, not only 'pendrives' or 'sticks')

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by KAWill70 on 2014-03-28
Thanks all for the help and suggestions.  I like the idea of the inexpensive IDE or SATA drive with USB conversion cable and small power supply.

Here are two articles discussing the hidden partition on the Passport drive.  Gparted apparently cannot remove the partition.  However, it was mentioned that the HP USB Disk Storage Format Tool will solve the problem.  I have used that tool before with Flash drives.

[http://www.dedoimedo.com/computers/passport-vcd.html](http://www.dedoimedo.com/computers/passport-vcd.html)

[http://www.reddit.com/r/linux/comments/17b64a/psa_avoid_wd_passport_drives_you_cant_reformat/](http://www.reddit.com/r/linux/comments/17b64a/psa_avoid_wd_passport_drives_you_cant_reformat/)

---

### Post by Navneet_Kumar on 2014-03-28
i would reccommend the Samsung Pro E-series sata disk to be used as USB hard drive,since it gives a better performance and is reliable.WD is also competitive with it.

---

### Post by sudodus on 2014-03-28
I see what you mean. It takes a special tool to get rid of the VCD partition.

---

