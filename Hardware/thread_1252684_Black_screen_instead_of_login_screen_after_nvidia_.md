---
title: "Black screen instead of login screen after nvidia driver activation"
date: 2009-08-29
forum: Hardware
---

### Post by gowron on 2009-08-29
Hi to all, 
    I am pretty new to Linux and I am having some issues with my video card (a 9400 GT) on Ubuntu 9.04.

After the OS installation I tried to activate the suggested nvidia drivers (180.44, tried also with version 173) using the Hardware Drivers utility. However, after rebooting the system, just after the Ubuntu loading bar, I can't get to the login screen and I get a black screen. The system hangs and I have to manually restart (I can't get to a terminal using CTRL-ALT-F1) and boot into recovery mode using the xfix option.
I also tried with two different LCD monitors connected to the card VGA output.

The problem seems similar to the one discussed here  [https://answers.launchpad.net/ubuntu/+source/xorg/+question/68054](https://answers.launchpad.net/ubuntu/+source/xorg/+question/68054)

I was able to get it work following these steps:
1) Activating the 180 driver without rebooting
2) Editing xorg.conf adding the line Option "UseDisplayDevice" "CRT-1" to the Device section
3) Killing the Xorg process

After these steps X restart and I can get to the login screen, the nvidia drivers result activated, I can change the monitor resolution, I can see the GPU temperature, etc...
However, after rebooting the system, I can't get to the login screen again.

Is there anyone with a working 9400GT?

Thanks in advance

---

### Post by WrathofthePenguin on 2009-08-29
I'm researching a similar issue (which is why I found your post). I'm about to go through this guide, which may help you. The 9400GT is not specifically mentioned here, but that may simply be because nobody has tried it and reported on it yet.

[Howto on Nvidia 185.18 drivers]("http://ubuntuforums.org/showthread.php?t=1125400")

Good luck!

---

### Post by gowron on 2009-08-29
> **WrathofthePenguin said:**
> I'm researching a similar issue (which is why I found your post). I'm about to go through this guide, which may help you. The 9400GT is not specifically mentioned here, but that may simply be because nobody has tried it and reported on it yet.

[Howto on Nvidia 185.18 drivers]("http://ubuntuforums.org/showthread.php?t=1125400")

Good luck!

Thanks. I'll give it a try as soon as possible.

In the last attempt:
1) I activated the nvidia driver (180)
2) sudo nvidia-xconfig
3) I added the line Option "UseDisplayDevice" "CRT" to the Screen section of xorg.conf (not to the Device one like before)
4) I changed the Monitor section in xorg.conf
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection
5) I killed the Xorg process

This time X crashed without allowing me to login so I rebooted manually. However I forgot to enter recovery mode and to fix Xorg. I was able to login :P (checking the log I see that Xorg changed "UseDisplayDevice" value from "CRT" to "CRT-1").
I changed the resolution of the screen without problems and rebooted to check if everything was working. Well... after reboot I wasn't able to login again :(

---

### Post by gowron on 2009-08-29
Ok, I managed to install version 185.18 of the driver following the howto. However it was useless :(

After launching sudo nvidia-xconfig (as suggested in the howto) I added the line Option "UseDisplayDevice" "CRT-1" in the Screen section of xorg.conf.
Then I closed the session and got the usual black screen. 
After rebooting (without entering recovery mode and using xfix) i was able to login normally with the nvidia driver. :P

I rebooted normally without doing anything and got a black screen again. I can't understand why... Everything seems fine until I reboot. 
Is there anything that can change xorg.conf (or something else) during reboot ?

---

### Post by gowron on 2009-09-03
I need help... I wasn't able to solve anything even if I've tried almost everything I found on the Net.

In my last attempts I've tried various xorg.conf configurations... 

I've read somewhere that similar problems could be caused by the inability of the system to acquire the monitor EDID. Then I noticed that my monitor (Samsung Syncmaster 2032BW) send a faulty EDID to the pc... I was able to save its EDID during one of the my successful login with the nvidia driver activated, then I added the line Option "CustomEDID" "CRT-1: PathToEDIDfile" to the Device section of xorg.conf so to let the system to acquire this EDID file.

I've also added the line Option "UseDisplayDevice" "CRT-1" to the Screen section as usual.

Just to be sure, I've even added the BusID "PCI:1:0:0" line to let the system know where my video card was.

Then, after rebooting, I was able to login with the driver activated. This lasts for three reboot procedures (the only thing I've done between one reboot and the other was to save dmesg and xorg.0.log messages). Prior to the third reboot, I've changed the resolution from 800x600 to 1650x1020 using nvidia-settings. The only strange thing I noticed was that  between the allowed resolutions there was one resolution above 1650x1020 (my monitor's maximum resolution). I think that the EDID should prevent this situation or not ?

However, after the third consecutive successful login, I rebooted thinking my problem had gone... this lasts till the usual black screen appeared :(. 
The only error contained in the xorg.0.log file is ```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```. This error does not appear when my system boot up correctly.

I've read on the Net that my motherboard (Asus P5Q-EM, with an integrated graphic board) may have problems with nvidia card even on windows. 
Can it be an hardware problem? I think not... I mean, the fact that sometimes I'm able to login (when I've just modified xorg.conf configuration) and certain times not suggests this to be a software problem.


Now I think I'm going to update the motherboard bios, then check if everything works under windows (this was supposed to be a Linux only system) and then with ubuntu 8.10.

Does anyone have any suggestion??

---

### Post by gowron on 2009-09-05
Well.. in the end, after upgrading the motherboard bios, everything started working :D

---

