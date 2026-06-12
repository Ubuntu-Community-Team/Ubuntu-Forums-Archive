---
title: "Vaio VGN series and ATI Mobility 9600 torture"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by branik on 2008-03-09
Hello everyone
I've trying to set up a sony vaio VGN S 170 notebook with U710. The installation process is competing just fine and I have the full 1280X800 resolution on the display. My trouble begins  once the installation is complete. Stangely enough I can't get the screen working, It's funny because the xorg.conf once the installation finishes is the same as the one running under the live cd session, meaning the Sections Device, Monitor and Screen read the same. I've tried everything there is out there with no joy. What really makes my head spin is that the as I said the live cd session works just fine. I really don't get why the installation is troublesome. For example when live cd starts I can see the initial bar filling up. When I do my first reboot I see blank screen. The same goes with an extern monitor. To get video on screen I have to edit xorg.conf file and write the "vesa" entry as driver and set the resolution 1024X768.

I would be grateful if someone could guide me to get this box working.

---

### Post by Yellow Pasque on 2008-03-09
Try booting with the ati driver (I'm assuming you're using the ati/radeon driver and not the proprietary fglrx/Catalyst, right?). When you get to the blank screen, try hitting Ctrl+Alt+F1 and see if you can get to a terminal. If you can, save your /var/log/Xorg.0.log file to your home folder so that you can post it when you boot with the vesa driver. 

Before you edit your xorg.conf back, try hitting Ctrl+Alt+Backspace and/or Ctrl+Alt+F7 to see if that magically gets a visble screen.

---

### Post by branik on 2008-03-09
Here are three logs. 
Xorg.0.log.ATI1280 is with ATI drv and 1280X800 res (**no image** on screen nor to the external monitor which had its led blinking, showing overscan (Samsung SyncMaster), 
Xorg.0.log.ati1024 is with ATI drv and 1024 res (**no image either**)
Xorg.0.log vesa drv - 1024 res (**no image again** - now it that something cause i had that drv -res combo working just a little while ago).
I say once please help cause I'm going nuts.

---

### Post by branik on 2008-03-09
Anyone??

---

