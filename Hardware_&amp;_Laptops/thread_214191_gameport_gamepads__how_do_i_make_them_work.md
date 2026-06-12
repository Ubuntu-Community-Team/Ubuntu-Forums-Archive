---
title: "gameport gamepads : how do i make them work?"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by lopzided on 2006-07-12
i have an InterAct Hammerhead FX 3dFX gamepad that connects through the PC gameport. i have read and read through the forums, and have still not been able to figure out how to enable it with ubuntu. i know it works, because i had no troubles using it with windows.

does anyone know how to install a gamepad through the gameport?

thanks in advance!

i have the driver/install disk that came with it, which is for windows.

NOTE: this was posted back in march on the breezy forum...however, i have since reinstalled and upgraded to dapper, and i'm still having the same problem!  please help!

---

### Post by setakht on 2006-07-12
Joystick loading doesn't work in Linux like it does in Windows. Joysticks are controlled by modules in the kernel.  You need to know two things to get them working.  First is the kind of gameport driver your system uses.  Ubuntu should already have loaded this if your gameport is supported (modules are often loaded automatically at boot up for many devices). To check type "lsmod" into a terminal and browse through the modules.  You should see something like gameport or gp somewhere.  If not, you'll need to google to see what module your gameport needs to work.  Second, your joystick is supported by the interact module, which needs to be loaded after the gameport driver.  Unfortunately, since gameport joysticks aren't plug and play it won't be automatically loaded.  To do it without having to reboot, open a terminal and do "sudo modprobe interact" -- if you get any errors you may have to google for the right module.  You also can use the "dmesg" command in the terminal to see a line by line output of kernel events, and if the joystick works it should be listed at the bottom.  Lastly, if you want the module to be loaded on boot, you'll have to add "interact" to the bottom of the list in /etc/modules.

---

### Post by lopzided on 2006-07-12
setakht, thank you for your reply!  however, i'm still having problems...

i checked lsmod, and it's there...it looks like this :

> gameport               17160  2 interact,snd_ens1370

also, i modprobe'd interact, and added it to /etc/modules.

however, when i run jscalibrator (to see if its been found), it wasn't...my usb gamepad shows up (js0), and works fine...however, still no sign of the gamepad plugged into the gameport.

any further suggestions?  again, thank you for your time!

---

### Post by lopzided on 2006-07-14
bump

---

### Post by lopzided on 2006-07-19
bump

---

### Post by lopzided on 2006-07-24
sigh...bump

---

### Post by AR_Kozz on 2007-01-23
This is an old thread but I saw you refer to in a much more recent one.  I've got the same type of sound card, run byt the snd_ens1370 driver.  I also connected everything right, loaded the correct modules, and - nothing. I've modprobed in every possible module combination, used MAKEDEV to make the js0 device, and followed all the HOW-TO's I could find here, to the letter.  One of them mentioned adding an options line for the gameport needed for ens_1371 cards, and I hoped maybe ens_1370 needed the same thing. It killed the sound on my computer but it still doesn't detect the device.

  I've been stumped by this problem too it's driving me nuts, I've tried 3 different joysticks/gamepads.  Anyone at all know anything special about gameports and cards that use the snd_ens1370 module?

---

