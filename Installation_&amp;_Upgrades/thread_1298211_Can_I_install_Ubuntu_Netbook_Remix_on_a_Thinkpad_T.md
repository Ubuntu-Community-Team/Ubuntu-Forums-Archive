---
title: "Can I install Ubuntu Netbook Remix on a Thinkpad T40 (Pentium M)?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Brian Kendig on 2009-10-22
I know that Ubuntu Netbook Remix is compiled for Intel Atom processors, but is there a way to install a Pentium M-compatible build of it on a non-netbook? Or a way to turn a standard Ubuntu 9.10 Karmic Koala installation into Netbook Remix?

I'd like to put this onto a ThinkPad T40. It's a fine laptop, but its 1024x768 display doesn't give me a lot of screen real estate. It strikes me that a netbook distribution would make really good use of the space.

I understand that Netbook Remix consists of a few packages added onto Ubuntu (and none taken away?), but I can't find specifics on what packages to add or where to get them.

---

### Post by snowpine on 2009-10-22
Netbook Remix should run on any computer capable of running Ubuntu (although it has slightly higher system requirements). There are no special Atom optimizations in the Netbook Remix kernel. You can do a fresh install, or if you already have Ubuntu installed, "sudo apt-get install ubuntu-netbook-remix".

---

### Post by Brian Kendig on 2009-10-22
Thank you for the info!

Is there an installation ISO for Netbook Remix on x86 processors? The only Netbook Remix installers I could find seem to be for Atom...

Why would Netbook Remix have higher system requirements? Don't netbooks generally have slower processors and less memory than laptops?

---

### Post by snowpine on 2009-10-22
> **Brian Kendig said:**
> Thank you for the info!

Is there an installation ISO for Netbook Remix on x86 processors? The only Netbook Remix installers I could find seem to be for Atom...

Why would Netbook Remix have higher system requirements? Don't netbooks generally have slower processors and less memory than laptops?

9.04 is available as an .img, not an .iso, so you need to use a USB thumb drive for the install: 

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

I haven't tried 9.10 personally (it's still in testing), but here is the link:
[http://releases.ubuntu.com/releases/9.10/](http://releases.ubuntu.com/releases/9.10/)

You'll notice they switched to an .iso for 9.10.

Why are system requirements higher? Probably because the netbook interface is an extra layer on top of Ubuntu. Also because there has never (to my knowledge) been a netbook on the market with less than 512mb ram, so why make the requirements lower? :)

---

