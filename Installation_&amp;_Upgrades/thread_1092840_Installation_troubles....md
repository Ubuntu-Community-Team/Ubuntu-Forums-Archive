---
title: "Installation troubles..."
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by alms66 on 2009-03-10
So I had Ubuntu 7.10 installed and working perfectly on my computer.  I did the upgrade to 8.04 and when it was done, Ubuntu has never worked again.  I've tried 8.10 and 9.04, neither works.  I have since installed Linux Mint, which works perfectly fine.

It always hangs in the same place, right after scanning hardware and displaying my cardreader information.  I'm going to go into the case and disconnect that to try and get Ubuntu installed again - though I don't know if that will work.  If someone has other ideas, please post.

Also, I guess I should report this as a bug when I get more information, right?  Where/How do I do that?

---

### Post by Neo_The_User on 2009-03-10
Card reader? what kind?

---

### Post by alms66 on 2009-03-10
I'm not sure of the brand of the card reader - it's a 9-in-1 usb card reader.

I disconnected the card reader and it still hangs during installation - this time at the Razor mouse, which is usb...
So I disconnected that and it still hung...
the last lines output are about loading the USB module.  I have a usb mouse and usb keyboard in additon to the card reader.  So at this point I tried a different keyboard and the same thing...

The very final line prior to the card reader info (when it's connected) is always the same though:

squashfs: version 3.3 (2007/10/31) Phillip Lougher

---

### Post by Neo_The_User on 2009-03-10
Try a PS/2 keyboard.

---

### Post by alms66 on 2009-03-11
Yep, the other keyboard I tried was PS/2, but it still hangs...

This computer is the exact same configuration I had when I was running 7.10 (including card reader), with a new mouse and keyboard.  If those two things aren't the problem, it's got to be something that changed in the code.

---

### Post by alms66 on 2009-03-11
Oh, and I also forgot to mention that this happens both during installation and trying to run the live cd...

I really want to get Ubuntu back, so thanks for any help you can give.

---

### Post by Neo_The_User on 2009-03-11
yeah I'm out of ideas

---

### Post by alms66 on 2009-03-11
Me too, that's why I'm posting...:D

---

### Post by alms66 on 2009-03-14
Ok, so I've got 7.10 back up and running on this computer.  For the guys looking into this bug, here are the computer specs:

 (1) Mini-Tower mATX Chassis w/350W PS K8M800 Motherboard
 (1) AMD Athlon 64 Processor 3400+
 (1) 2GB DDR400 PC3200 Memory (1024MB x 2)    
 (1) Barracuda Serial ATA (SATA) Hard Drive 120GB (7200 RPM)    
 (1) Diablo Tek GeForce 6800GS 512MB AGP8x video card  
 (1) 16x DVD-/+R/RW Dual Layer Drive
 (1) 10/100/1000 Gigabit NIC    
 (1) SoundBlaster Live 24-Bit PCI Sound Card (no Game Port)    
 (1) USB keyboard   
 (1) 9-in-1 USB Card Reader    
 (1) Razor Copperhead USB Mouse

---

### Post by alms66 on 2009-04-27
So, I figured if it's just a bug in the graphical installer, the alternate cd should install.  No, same problem.

Maybe, I should be able to upgrade from 7.10 to 9.04...
It took a while, yes.

I made it to 8.04 or 8.10 (I think 8.10, but I'm not 100% certain), then with the upgrade to the next version and restart, it did the same thing as above.

---

### Post by alms66 on 2009-04-29
Downloaded and installed the 32 bit version, and it works perfectly...

---

### Post by alms66 on 2009-08-22
I downloaded 9.10, and this problem is solved in that installation.

---

### Post by alms66 on 2009-10-18
...and now it's back again.

---

