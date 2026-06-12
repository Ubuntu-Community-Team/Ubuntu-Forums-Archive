---
title: "start directly O.S. in usb"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by menuetto on 2009-11-06
Hi,
I've installed Ubuntu Remix 9.10 in an usb-key through Live Cd + USB Sturtup Disk Creator.

Because I use it also as portable O.S. I would like to avoid the first step, where I must check for the language and for the option "Start Ubuntu without install".

Is it possible to start automatically the O.S.?

---

### Post by fishyf on 2009-11-06
I was thinking of doing this. As I understand it, if you start using the USB key that you have, it pretty much mimics the install CD and it is not the ideal way to operate.

You should get a second USB key and then install the OS onto the second USB key. I would recommend at least 4G and probably 8G as the size of the USB key to install onto. At that point, you don't need the original install USB key and can reuse it.

If you are doing this, I recommend using an extension cable for the USB key as otherwise it will be vulnerable to being knocked and damaged if you are moving your netbook. I also recommend using a backup program to backup the contents onto the inbuilt storage of your netbook.

As I said, I haven't tested this, so my suggestions might not make sense.

---

### Post by Mighty_Joe on 2009-11-06
> **fishyf said:**
> As I said, I haven't tested this, so my suggestions might not make sense.

Linux sees a USB flash drive as just another hard drive, so it is a perfectly valid destination for an install.  Of course, flash memory can wear out after a number of writes, so it is wise to tweak the install by moving logging and cache to tempfs and not using swap if you can get away with it.
See my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680") for a link to instructions on optimizing a flash drive install.

---

### Post by menuetto on 2009-11-06
Well, I had already an usb with a full installation of Ubuntu, but for the 9.10 version I've decided for the "usb live" because I've read lots of posts about the shorter life of a flash memory.

I've already tried unebootin, but it also doesn't start automatically, doesn't it?

But I think there is a method to skip the first screen and access directly to the Ubuntu boot. And I suppose, it's not difficoult to change, if you know where to change. I've looked in /boot/grub, but it looks not the right place :-k

---

### Post by Mighty_Joe on 2009-11-06
> **menuetto said:**
> Well, I had already an usb with a full installation of Ubuntu, but for the 9.10 version I've decided for the "usb live" because I've read lots of posts about the shorter life of a flash memory.

[Don't sweat it]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html").  You'll lose the drive or trade up for a bigger one long before it wears out.

---

