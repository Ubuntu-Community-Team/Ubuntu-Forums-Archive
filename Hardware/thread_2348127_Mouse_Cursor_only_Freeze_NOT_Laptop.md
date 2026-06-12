---
title: "Mouse Cursor only Freeze NOT Laptop"
date: 2017-01-01
forum: Hardware
---

### Post by wyght2 on 2017-01-01
My mouse cursor started to freeze a few days ago, at the same time I notice my desktop gave three long beeps when booting. I have Ubuntu 16.04LTS not certain how long I have used this version. I have Intel Bios version S5500.86B.01.00.0060.090920111354 size 64 KiB. I have four Kingston 16384 MB but one failed (searching around in BIOS setting showed me) I believe around the same time my mouse began to freeze. I have searched around and have not found anything telling me this could be the cause. I have a USB Microsoft Keyboard, plus a USB Microsoft Trackball. 

I have moved both USB connections keyboard only once because on Intel Bios it says three long beeps is a failed keyboard card, my mouse USB I moved to five different USB slots 4 on back 1 on front of tower. My keyboard works while the mouse cursor is frozen. I can type and move using tab or 'alt tab', also while the cursor is frozen I am still able to click right or left button scroll using the tracking wheel on my mouse. I have my cursor set to highlight if I press the Ctrl button and that works while cursor is frozen too. Often this 'seems' to unlock it but not always I would say about 50/50% one press and the cursor moves. 

If I use the mouse cursor, meaning keep it active even for two minutes it does not freeze. If I stop even for a second it freezes most of the time I would say about 75-80% I have not noticed it freezing while moving it. If I stop the cursor to click on something it may freeze or may not. I would say that is about 50/50. These percentages are best guesses.


Bus 008 Device 003: ID 045e:0024 Microsoft Corp. Trackball Explorer

I tried the following 


 echo "on" | sudo tee /sys/bus/usb/devices/usb*/power/level
 cat /sys/bus/usb/devices/usb*/power/level
 
//after reboot all usb to 'on' but mouse seemed worse. then I tried


sudo sed -i 's/quiet/usbcore.autosuspend=-1 quiet/g' /etc/default/grub

rebooted best guess, my cursor issues are worse not better


I believe my mouse issues are because one Kingston failed. I don't know how to prove this, but when stores open I will buy new RAM. 

My question (two)
is there a way to discover what is causing my mouse cursor issue?
is there anything I can do to cause this cursor to work 24/7?

---

