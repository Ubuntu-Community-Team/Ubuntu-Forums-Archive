---
title: "Block Device Floppy Suggestion"
date: 2010-08-20
forum: Hardware
---

### Post by and003 on 2010-08-20
This thread I have established concerns the problems that some Ubuntu 10.04 users, myself included, had with trying to mount their 1.44 MB floppy drive. I think, but I'm not sure, that I know what the problem might be.

When I tried to install the 1.44 MB floppy drive after specifying the filesystem type, I was greeted with the following message: 

Unable  to mount location
Error mounting:
mount: /dev/fd0 is not a valid  block device

I think if /dev/fd0 can be made into a valid block device, then the floppy can be mounted. The problem is, how can /dev/fd0 be made into a valid block device?

---

### Post by and003 on 2010-08-21
I found some step-by-step instructions on how to mount my floppy drive in Ubuntu 10.04, so there is no need for my previous suggestion.

Those instructions are found here:
[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/120571)

---

