---
title: "Presario F700 hangs on hardy"
date: 2008-05-29
forum: Hardware
---

### Post by sroland81 on 2008-05-29
Hello, i have a Presario F730 notebook that i use for scientific work. is an amd 64 bit TK-55 with nVidia Go 6100 and things are going wrong. I experienced a few issues:

1) After a fresh installation and post-installation of nVidia restricted drivers the shutdown usplash is missing and instead of it i have random and fast changing horizontal and vertical white lines that freaks me out, but it shuts down at the end.

Comment: I enabled compiz-fusion and runs very smooth, anyway i use metacity most of the time. If i go through a session without enabling compiz-fusion, the shutdown usplash is still missing but i only get black screen and then expected shutdown, but if i enable and disable compiz-fusion in my session, and then shut down, the weird lines appears... don't know.

2) i installed broadcom b43 drivers with bwfcutter and stuff and i get connected... it disconnects once every 15 or 30 minutes but works ok.

3) the system hangs me very often, sometimes i have to restart the laptop 2 or 3 times in a couple of ours... and that lead me to search in the log files and "dmesg" shows lots of lines of "[  762.207796] b43-phy0 ERROR: PHY transmission error"... and i thaught that may be the wireless is responsible of system hang up. don't know.

Comment: My usually session consists in Exaile music player, or audacious, octave, firefox, pidgin, rutilt wlan manager and stuff... but when i do a lot of things or have to tasks running... the system hangs up and keyboard not respond at all, y have to press power button for a few seconds to reboot.

4) i noticed that the hard drive, once a session or so, makes a huge "clack" sound that freaks me out... i read about load cycle count and i disabled it with hdparm... but the sound persists with te computer plugged or running on battery..

i really need help in order to have a robust enough system... i can't lie to myself and pretend that ubuntu this way is robust than the downgraded XP that i installed recently on this Vista default notebook.

P.D: in the "dmesg" i obtained a few more lines when the wifi went down...

[ 1327.320993] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 1327.321003] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed in July 2008.
[ 1327.321006] b43-phy0 warning: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).
[ 1327.382001] Registered led device: b43-phy0::tx
[ 1327.382161] Registered led device: b43-phy0::rx
[ 1327.382252] Registered led device: b43-phy0::radio
[ 1351.248324] wlan0: No ProbeResp from current AP 00:60:b3:8a:24:95 - assume out of range
[ 1506.819680] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 1506.819691] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.

Thanks,

Santiago.

---

### Post by DarKnyht on 2008-06-21
I have a Presario F750US and this thread helped get it up an running. I think I had to start with 7.04 or 7.10 though because 8.04 had some issues.

[http://ubuntuforums.org/showthread.php?t=749481]("http://ubuntuforums.org/showthread.php?t=749481")

---

