---
title: "Adding second hard drive"
date: 2006-10-13
forum: Hardware &amp; Laptops
---

### Post by OakRand on 2006-10-13
I want to add a second hard drive for storing a lot of data from my work. Basically I want to associate a single folder in my home directory with this new hard drive. I haven't installed a hard drive in linux before and just wanted to check somethings.

Assuming it is added as the 2nd Master, with one partition, I add an entry to /etc/fstab as so:

/dev/hdc1  /home/my_name/data  ext3  default 0 2

1. Does this look right? I am uncertain about the "default" and numerical entries.

2. Anything written to this mount point will be stored on this new hard drive, and anything written outside of this mount point will be stored on the old hard drive, correct? I'm not sure if this is true since my old hard drive has the root directory as a mount point, which my new mount point is located within, so why would data ever be written to my new drive?

3. Is there any problem with doing this using an 80GB hard drive?

---

### Post by kidders on 2006-10-13
Hi there,

You're almost there. Change "default" to "default**s**" and "0 2" to "0 1" or "0 0". Don't forget to actually create /dev/hdc1 though!

**Edit:**

> Is there any problem with doing this using an 80GB hard drive?The only problem you're likely to encounter is initial permissions-related stuff, in the even the user whose /home you mount the filesystem into isn't allowed to write in it for some reason. You can fix that in a snap with a "sudo chmod ..." or "sudo chown ..." though.

---

### Post by OakRand on 2006-10-14
Thanks kidders. I think I have the rest covered.

---

