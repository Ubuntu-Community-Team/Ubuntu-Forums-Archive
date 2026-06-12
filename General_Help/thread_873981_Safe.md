---
title: "Safe?"
date: 2008-07-29
forum: General Help
---

### Post by gymtonic on 2008-07-29
Is WUBI completly safe?
And, when they say Hibernation is not supported, does that mean in Windows aswell? Because sometimes Windows goes into Screensaver mode and then turns the screen off (is this hibernation? to get out of "hibernarion" i just have to move the mouse)
thanks.
gymtonic

---

### Post by ago on 2008-07-29
Yes it is pretty safe, provided you do not pull the plug (which is bad per se'). The hibernation issue has nothing to do with windows.

---

### Post by gymtonic on 2008-07-30
I installed it this morning and and I rebooted, which was fine but in the bootloader I can only select windows vista and I can't press up or down to select ubuntu, is this normal and do I have to do some funky key combo I have to do?

---

### Post by ago on 2008-07-30
> **gymtonic said:**
> I installed it this morning and and I rebooted, which was fine but in the bootloader I can only select windows vista and I can't press up or down to select ubuntu, is this normal and do I have to do some funky key combo I have to do?

This is due to Windows/Bios not supporting your keyboard. At that stage wubi is not running at all, you would have experienced the same issue if you had installed vista and XP in dual boot... In many cases there are some BIOS settings to change the USB setup, otherwise you will have to use a standard keyboard.

---

### Post by gymtonic on 2008-07-30
oh, well, that sucks
can i just uninstall through the Wubi uninstaller?
Because if it means all this hassle then I might as just uninstall it

---

### Post by ago on 2008-07-30
> **gymtonic said:**
> oh, well, that sucks
can i just uninstall through the Wubi uninstaller?
Because if it means all this hassle then I might as just uninstall it

Sure

---

### Post by gymtonic on 2008-07-30
Well,  I figured out that my keyboard and mouse were connected by a USB hub so I plugged the keyboard and mouse directly to the computer.. Which works now, it installed perfectly the only thing is, the screen res is 800x600, sound isn't working and wireless isn't working

---

### Post by minhmeoke on 2008-07-31
Fix screen resolution with system > preferences > screen resolution.

For sound and video, find out what hardware you have: open up a terminal (applications > accessories > terminal) and type in the "lspci" command, then search ubuntuforums for solutions.

---

### Post by gymtonic on 2008-07-31
Umm... 800x600 is the maximum screen resolution, I'll boot into ubuntu and see  what the terminal commands, and I found a tutorial on here for my usb wireless adapter

---

### Post by minhmeoke on 2008-08-02
What video card do you have? If you are using an nvidia video card with proprietary drivers, then you could try "sudo apt-get install nvidia-settings", and using it to generate an xorg.conf file. Otherwise, you might have to edit the /etc/X11/xorg.conf configuration file manually to enable higher resolutions.

---

