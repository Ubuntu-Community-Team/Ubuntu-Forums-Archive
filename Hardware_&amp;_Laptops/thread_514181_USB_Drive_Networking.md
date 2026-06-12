---
title: "USB Drive Networking"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by othsy2k on 2007-07-31
I just bought myself a 500Gig USB drive. I want to make it available on the network. Problem is I have no idea how to make a USB drive shareable. My internal drives are on the network just fine, but this external is a new ball of wax. Any ideas?

---

### Post by pbcartwright on 2007-07-31
when you say your  internal drives are "on the network", how?
if you do a mount, does it show the internal and external drives? If so, you should be able to share the external drive the same as your internal drives, but you do have to tell it to SHARE the drive...
is the USB drive in your /etc/fstab ?
how do you share your other drives?
if you use a program like winscp, or just ftp, from anothr machine, you can see your internal drives but not the external?

---

### Post by othsy2k on 2007-08-03
They're on the network because I right clicked on my home folder and clicked "Share Folder" and on my slave drive I right clicked on my media folder and did the same.

I think I got it. NM Thanks though.

---

