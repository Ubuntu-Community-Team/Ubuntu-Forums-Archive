---
title: "Transferring Internal Hard Drive Data?"
date: 2012-08-04
forum: Hardware
---

### Post by HoCo xXSamXx on 2012-08-04
I have a 250gb HD in my dell laptop. If I were to buy a new 1tb HD, what would be the best way to transfer ALL the data? Partitions and everything.

Thanks!
HoCo

---

### Post by papibe on 2012-08-04
Hi HoCo xXSamXx,

Take a look at [Clonzilla]("http://clonezilla.org/"). It's a live CD/USB that let's you clone the whole disk.

There are a few extra steps after that, but that should get you started.

Regards.

---

### Post by ahallubuntu on 2012-08-05
You will probably want a SATA USB hard drive adapter or enclosure, so you can attach both drives to the laptop at the same time.   (They can be bought for as cheap as $4 on eBay, more if you want one more quickly.) Then, you could boot something like Clonezilla.  I've actually had mixed luck with Clonezilla over the years; sometimes it's worked perfectly, sometimes it doesn't work at all.  Maybe it's improved in recent years.

Sometimes a new drive comes with software for cloning your old drive.  But it may or may not support Linux.  I also use True Image from Acronis for cloning; the latest versions support Linux ext4 partitions.

---

### Post by lindsay7 on 2012-08-05
Clonezill and True Image are easier to clone drives if the clone to a drive that is the same size. So, I suggest that you partition your new dive first so that you have a 250 gig partition to clone to the new drive. You can set up the other partitions as you like.

---

