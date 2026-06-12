---
title: "Problems installing 9.04 on Dell Latitude XT Tablet"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by jldeanley77 on 2009-05-14
Hi 
 
New to Linux and wanted to Dual Boot my Dell Latitude XT Tablet with Vista and Ubuntu 9.04.  I shrunk my volume in Vista Ultimate and freed up 20GB of space.  I created the 9.04 CD and it boots to the menu to do the Install but I get the following error "modprobe: Fatal: Could not load /Lib/modules/2.6.28-11-generic/modules.dep: No such file or directory.  Not sure if this is relevant but I have an External DVD drive hooked to it that came with it to do the install.  Then it comes up with BusyBox v1.10.2 and puts me at a prompt (inintramfs)  Not sure how to resolve this
 
Any help is greatly appreciated
 
Joel

---

### Post by Matsuri on 2009-05-14
Try having the CD run a diagnostic check on itself. This option is seen from the main menu on the CD. Just so we can rule out faulty CD. I know you just made the CD but I've had crazy stuff happen before.

---

### Post by jldeanley77 on 2009-05-14
Matsuri,
 
Thanks for the response...I clicked on the Disc Diagnostic and it is blinking at the end with a curser at the bottom.  The very end line says [0.956015] ---[end trace 4eaa2a86a8e2da22]---
 
Doesnt show any errors on this screen
 
Joel

---

### Post by jldeanley77 on 2009-05-15
anyone have any idea how i can resolve this issue?

---

### Post by Newtothegame on 2009-06-18
Ok I read about this in another forum. But if you want to get rid of the busy box error on load, what you need to do is when you see the Ubuntu screen hits a load bar, unplug the usb and plug it back in. Sounds cheesy but it works. 

Also there is a forum out there talking about how to exit the error but this fix worked for me so I stayed with it.

---

### Post by gohanssjn on 2009-06-30
> **Newtothegame said:**
> Ok I read about this in another forum. But if you want to get rid of the busy box error on load, what you need to do is when you see the Ubuntu screen hits a load bar, unplug the usb and plug it back in. Sounds cheesy but it works. 

Also there is a forum out there talking about how to exit the error but this fix worked for me so I stayed with it.

Haha, that's exactly how I installed 9.04 a few months ago.  So yes, I can confirm it works.  Basically, when the install starts, it 'reboots' the USB devices, but they never reinitialise.  Unpluging and plugging back in turns them back on.

---

### Post by mscyber07 on 2009-08-20
You just need the alternate disc image.  The text-based one.  If you search for it on the ubuntu homepage, you'll find that it's one of the first few hits.

        Good Luck!

---

