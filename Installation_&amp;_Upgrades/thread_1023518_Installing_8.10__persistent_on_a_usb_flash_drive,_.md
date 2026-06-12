---
title: "Installing 8.10  persistent on a usb flash drive, question."
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by besby11 on 2008-12-28
Hay Fourm,

 OK so I received a nice 8 gig flash drive for Xmas this year and thought I would put it to good use by installing 8.10 on it using this guide on pendrivelinux.com [http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/]("http://www.pendrivelinux.com/2008/11/04/live-ubuntu-810-usb-persistent-install-windows/") I like this idea because the install is persistent compared to running it like a live CD. The only issue is that after I get it all setup it gives me about a gig of room or so left when actual I have about 6 or so gigs. So by the time I'm done installing updates and everything, it says im out of room. I opened up gparted to see if there was any partition restrictions, but it shows 1 large partition without any type or logical separation or anything. I cannot understand why it doesn't take advantage of the full drive space. If there is anyone out there that can help me it would be great! THNX!!

---

### Post by tommcd on 2008-12-28
If you have Ubuntu 8.10 installed on your computer, then you can create a usb flash drive install simply by going to System > Administration > Create a USB startup disk.

---

### Post by ChrisB111 on 2008-12-28
I had the same problem, as said use the *System > Administration > Create USB Startup Disk* option either in the live CD or on an existing ubuntu system. I lets you choose the space given to the system.

I personally use [Slax]("http://www.slax.org/") on usb, I think its a lot more stable and suited to running on usb than ubuntu.

Good luck,

Chris

---

