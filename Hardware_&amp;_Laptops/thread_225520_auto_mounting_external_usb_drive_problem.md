---
title: "auto mounting external usb drive problem"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by pld on 2006-07-29
Hi all,

Doing a quick search hasn't really yielded any answers to what I specifically need to know.

In 5.10 I setup udev rules to allow me to easily mount/unmount an external hdd and usb pen drive.  Everything worked fine for me.  I had fstab setup to allow me to mount my drives easily, and udev made it great by allowing me to have a consistent /dev/* to call on.

Now i have upgraded to dapper, and the next thing I know I have an icon on my desktop (XFCE) for my external drive.  Neat!  Except that it appears that the mountpoint for my drive is now in /media/My Book

ummm.  oookay.

Now, the problem is that I don't know what is creating this mountpoint!  Does anyone know where/why this is happening?!

What is doing this auto-mounting of my external drive?  I have removed autofs from my startup scripts, so it doesnt appear to be that.

One thing I noticed is that if the machine boots, but I don't login to an xfce session, but I ssh in from another terminal, then the /media/My Book mountpoint does not exist.

It doesn't exist until I login to an XFCE session.  So I think there might be something happening there that is causing this to happen.  I sincerely hope someone might be able to help me out with this, it is driving me nuts.  I want to be able to control this behaviour somehow!

tia

---

### Post by sazu on 2006-07-30
I believe it's how dapper and pmount work with USB devices nowadays. For example, I have a 250 GB USB drive called XTEND, and naturally it autocreates itself under /media/XTEND. You can modify the list of devices you want to be mounted and not mounted under /media by editing /etc/pmount.allow and /etc/pmount.deny.

---

