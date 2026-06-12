---
title: "No Bootable Device? Please help!"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by aardvarkwal on 2009-11-09
I'd been using Ubuntu for a few months now on my primary laptop (dual booting with Vista) and only today decided to uninstall it in favor of Vista alone (planning to install on another laptop that I don't use for web design etc). The uninstall went smoothly and Vista was running on startup... however it was only when I went into the Live CD of Ubuntu in order to use GParted that everything went to hell.

I was trying to allocate all the free space I'd gained back and put it into the Vista partition. I wasn't having any problems, but when I restarted my laptop-- it went to a black screen telling me no bootable device.

My live CD is working fine but now it look likes I'm only able to use Ubuntu, and only thru the live CD.

What can I do?!

Thanks for your time and hopefully I can get some direction.


ETA: I tried putting in a Vista install CD and Vista is not even showing up there!

---

### Post by Mark Phelps on 2009-11-09
Did you use GParted to try and expand the Vista OS partition?

If so, you probably corrupted the Vista OS filesystem in the process.

You should have done a forum search here about problems with GParted and Vista before you did that.  You would have saved yourself a lot of grief.

You will need to boot from a Vista DVD and run Startup Repair several times to get Vista back.  If you don't have one, you can go to the NeoSmart Technology forums website and download a Vista recovery CD image, burn that to CD, and then boot using that.

---

