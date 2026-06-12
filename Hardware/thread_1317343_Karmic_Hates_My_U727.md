---
title: "Karmic Hates My U727"
date: 2009-11-06
forum: Hardware
---

### Post by jasonditz on 2009-11-06
So I'm trying to get this Novatel U727 working with my assorted Ubuntu systems. They all detect it as a CD-ROM at first, and once I eject that they all seem to notice what it actually is. But...

My laptop, running AMD64 jaunty, connects instantly after ejecting the CD-ROM, and seems to run flawlessly. 

My netbook, running i386 hardy, tries to connect but instantly says "disconnected" This keeps happening no matter how many times I try. 

My desktop, running AMD64 karmic, hates it with a passion. It never connects, and will only sometimes even try. Moreover it has a nasty tendency for weird errors to crop up afterwards, like making lsusb sometimes, but not always, eat up 400% CPU and be uninterruptible, or freezing the USB keyboard until reboot. 

Am I just having a weird case of bad luck, or is this a known issue other people are having?

---

### Post by jasonditz on 2009-11-07
So I've been fiddling with this for awhile and I think I'm close...

Here's what I did:

sudo eject /dev/sr1

sudo modprobe usbserial vendor=0x1410 product=0x4100

sudo modprobe option

----

After that the Network Manager actually sees the thing, and will even connect, long enough that I was able to log in to AIM through pidgin. Though I never got a "disconnected" message or anything the connection seemed to stop responding after a few minutes. I don't think it's a signal issue because the Jaunty laptop still works fine.

The same procedure (with /dev/sr0) seems to get my hardy Netbook to see it too, but Network Manager instantly reports "disconnected" when I try to use it.

---

### Post by phillyphilphil on 2009-12-19
Hi guys,

I am having trouble with this same exact issue.  Search return this being a problem for many and that a bug has been filed.  Has anyone had any luck in getting U727 to work in Karmic?

---

