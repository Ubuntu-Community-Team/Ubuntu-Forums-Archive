---
title: "Matrox Video Card"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by calmlunatic on 2009-01-28
I've recently installed Ubuntu 8.10 on a rather old system AMD 500 and after installation and updates I figured I'd need to install the driver for the Matrox G400 Video card to allow the display to go above the default limit of 800x600. However, upon opening up the hardware drivers window the video card (and none of the other hardware either for that matter) are listed. 

So I'm wondering if there's any way to be able to get this video card and any of the other associated hardware (sound card, network card etc.) to show up on the list to be able to install their native drivers or would I have to use the "sudo" method to install them?

Thanks.

---

### Post by Mark Phelps on 2009-01-28
Don't know your experience with GNU/Linux, but it's not at all like the MS Windows arena.  The drivers window you opened is for proprietary drivers, not for open source drivers included in Ubuntu.  This is typically used to install ATI/AMD or Nvidia video drivers, because both of the manufacturers provide third-party drivers.

Ubuntu scans the hardware during the installation and loads all the open source drivers needed (those that it can find). If you're getting any video at all, that means it found something that works.  

Given that Matrox has been out of business for years, unless you can track down a website, and even then, one that has Linux-specific drivers, you're going to have to live with the current drivers.

---

### Post by Tarim on 2009-10-01
Actually Matrox is still in business, just not the mainstream presence that they once were.

 They do offer Linux display only drivers (ie no TV support) for a few of their legacy video cards here: 
 
[http://www.matrox.com/graphics/en/support/drivers/latest/](http://www.matrox.com/graphics/en/support/drivers/latest/)  
 
Everything else Mark said is spot on.

---

