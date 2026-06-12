---
title: "Monitor Problem"
date: 2008-10-30
forum: Hardware
---

### Post by Detailedghost on 2008-10-30
Hi there. I'm back with Ubuntu and I've got a major problem. I got a junky old Dell Dimension 2350 and I decided to upgrade it a bit. So i added some new stuff and everything works great. The only problem I have is that my Nvidia GeForce 5200 Graphics card that I updated screwed up my resolution! I updated the drivers for it and now it's running 800x600@60 when my Magnavok LCD can run up to 1024x768@60! The sad part was, it was running at 1024x768 resolution before I installed the Ubuntu drivers and now I can't fix it! I've tried all the online threads but it still won't work! Can someone please assist me? Thx

---

### Post by dawynn on 2008-10-30
I'm hearing that your system is producing 800x600 graphics -- so the card is working in some sense, correct?

Which nVidia drivers are you using?  If you're truly using the nVidia drivers and receiving output, and the driver number is greater than 100, then you're in a good place.  Legacy drivers < 100 are in a bad place at this time, but nVidia has a beta version out to try to fix this (at least 96.43.09 is out, not sure about the 7* series).  Note: nVidia has released it.  Last I checked, 96.43.09 is not in the Ubuntu repositories yet.

lsmod should confirm whether you're truly using nVidia or using nv.  Either way, having output is a good thing.  Whichever desktop you're using, there should be a menu option to change your display configuration, but this alters some between the various desktops.  What desktop are you using?  Gnome, KDE, XFCE?  Something else?  Knowing this will help us respond back with appropriate menu selections.

---

### Post by Detailedghost on 2008-10-30
Well the deal is is that there is the graphics card vga output and the intel integrated vga output. My monitor is plugged to the intel output currently, and I don't know wether that matters or not. What's ISOmode btw? 



P.S. I'm using GNOME  :guitar:

---

### Post by Detailedghost on 2008-10-31
I've made the executive decision to reinstall ubuntu. I'm upgrading it from 8.04 to 8.10 so there's a small chance that the drivers work with the new Ubuntu and not the older, 8.04 version. I hope it works. :|

---

### Post by Detailedghost on 2008-11-01
Ok well the ubuntu update didnt work on my comp. (guess the update is faulty) so i just reinstalled ubuntu 8.04. Ill try and reinstall the drivers in a bit

---

### Post by Detailedghost on 2008-11-01
Ok i fixed the resolution. I redid everything and I restarted the system and Ubuntu went into "low graphics mode" because it couldn't automatically detect my monitor. So I just set it to my model and viola!

But with one problem down, a new problem arises. After I fixed the resolution. I went into the visual effects and my "extra" went down to "none". I tried to change it to "normal" at least, but an error message comes up and says, "Desktop effects could not be enabled".

I know I'm a noob at this stuff but I'm seriously thinking about switching back to windows even though I dont want to. Can someone please respond to this thread and help me!?!?!?

---

### Post by Detailedghost on 2008-11-07
Hello? Anyone there?

---

### Post by Detailedghost on 2008-12-09
Ubuntu was corrupt. Clean install did the trick.

---

