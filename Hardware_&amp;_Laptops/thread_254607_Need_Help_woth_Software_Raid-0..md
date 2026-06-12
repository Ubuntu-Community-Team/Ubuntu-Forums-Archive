---
title: "Need Help woth Software Raid-0."
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by Ausus on 2006-09-10
Hi All,

I need help pease.

Steps which I followed:
Step 1)
Bios set two 80 gig's as raid 0.
Motherboard see's raid syste.

Step 2:
Used alternate amd64, boot via CD-Rom.
When through various stages off setting up system.

Step 3:
Select two HD and set them up as Raid HD.(Shows up as K-Raid)

Step 4:
Create now raid partion.
HD-1 /boot 10Gig select as boot,/ root 30Gig, 39Gig /home and 1Gig /swap.
HD-2 setup same as above.

Step 5:
Use software raid tool now.
Set up 4 raid devices if I may call it that way.

Step 6:
Select each created sotware raid device and configure.
As ext3 etc.The only thing which I battle with is.Their is no-way that I can tell the /boot partion to be bootable.Under step-4 is the only place where I can select bootable.

Step 7:
Finish off.
Now the fun starts, grup-loader does not now where to be installed.It wants to be installed hd0.

So I need some help.

Regards
I not in front of my PC to supply more info.:frown:

---

### Post by neptune39 on 2006-09-11
I found this very easy with the alternate CD. I didn't mess with my setting for the motherboard raid, as long as the installer sees the drives it should be fine.

I set it up like this

drive one:
50mb /boot with bootable yes
500mb /swap
the rest set for raid

drive 2 and 3:

500mb swap and the rest for raid

then in the installer you go into the raid set up and pick raid 0, pick the drives you want to add and done.

I then get above plus a new drive (the raid) which I format as root. This worked for me, first time I missed boot partiton and grub failed, other than that it was straight forward.

---

### Post by Ausus on 2006-09-12
Hi neptune39,

Correct me if I'm wrong, you need internet access.
I followed a Finish chaps installation guide.
He is using Raid-1 settings.
I tried Raid0 and 1, no success.

I get to to the point where grub get's up to 50%, then it sit their for ever.

It seem's my Raid partions never get mounted.
For my late reply, I was away to Cape-Town on company business.

It seems what ever you do in linux the more difficult stuff, you need internet access. The installation assumes you have a available connection to the internet.


Regards](*,)

---

