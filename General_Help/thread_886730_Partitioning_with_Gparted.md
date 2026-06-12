---
title: "Partitioning with Gparted"
date: 2008-08-11
forum: General Help
---

### Post by Ezlo4 on 2008-08-11
Okay so I'm trying to partition my hard drive in order to install Vista. I am using Ubuntu and am trying to making a new partition. 

I open up Gparted and the device it says I am using is /dev/sda. However, in most of the guides I read, it says /dev/hda.

I can't resize or move anything. Please help.

---

### Post by Titan8990 on 2008-08-11
hda indicates a IDE hard drive while sda indicates a SATA drive. There is really no difference.

---

### Post by Ezlo4 on 2008-08-11
> **Titan8990 said:**
> hda indicates a IDE hard drive while sda indicates a SATA drive. There is really no difference.

Okay. But I still can't resize my partition.

---

### Post by cszikszoy on 2008-08-11
You probably can't resize it because it's currently mounted.  You can't resize your system disk while your system is running.  To resize, you'll need to use the LiveCD.  gParted is on the live CD for this reason :)

---

### Post by OutOfReach on 2008-08-11
You can't resize the partition because it's currently in use, or mounted. As cszikszoy said you need to boot from a LiveCD, any LiveCD that has GParted included, and resize from there.

---

### Post by sandysandy on 2008-08-11
burn a gparted CD (as image)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

gparted tutorial is here

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by cybrsaylr on 2008-08-11
> **sandysandy said:**
> burn a gparted CD (as image)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

gparted tutorial is here

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

Thnaks for the link.
I was wondering about using Gparted also.

---

### Post by Ezlo4 on 2008-08-11
Okay, I was able to partition my hard drive. However, when prompted on the location to where I would install Vista, it said Vista could not find anything. 

Any suggestions on what I should do?

---

### Post by kernelhaxor on 2008-08-11
> **Ezlo4 said:**
> Okay, I was able to partition my hard drive. However, when prompted on the location to where I would install Vista, it said Vista could not find anything. 

Any suggestions on what I should do?

did u format that new partition with ntfs?  if not, I would try reformatting the new partition with ntfs first ..

---

### Post by Ezlo4 on 2008-08-11
> **kernelhaxor said:**
> did u format that new partition with ntfs?  if not, I would try reformatting the new partition with ntfs first ..

Err... how do I do that?:confused:

---

### Post by ntu on 2008-08-11
You can format with gparted

---

### Post by Ezlo4 on 2008-08-12
Okay.

I was able to format the partition as ntfs. But still, nothing shows up.

---

### Post by Ezlo4 on 2008-08-12
guys

i srsly need help ;__;

---

### Post by ntu on 2008-08-12
> **Ezlo4 said:**
> Okay.

I was able to format the partition as ntfs. But still, nothing shows up.

Where are you looking? Presumably it shows a ntfs partition in Gparted?

---

### Post by M4rotku on 2008-08-12
From my experience with Vista, it has always installed over the entire disk no matter what I tried.  I always had to install Vista and the reinstall Ubuntu.

---

