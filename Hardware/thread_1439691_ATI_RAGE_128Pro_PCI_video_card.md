---
title: "ATI RAGE 128Pro PCI video card"
date: 2010-03-26
forum: Hardware
---

### Post by sdtrott on 2010-03-26
I recently had to install an ATI RAGE 128Pro PCI video card after the NVIDIA card I previously used died.  Does anyone know if a Linux driver exists for this card?  I am able to boot Ubuntu and an error message comes up that gives me the option to run Ubuntu with low resolution graphics.  Although the colors are displayed correctly, the only display option is 800x600 which makes it difficult to view applications such as Evolution e-mail because at that resolution I can only view a few lines at a time.  I am not as much concerned about graphics for gaming.  I would be happy to just set the resolution at a setting which allows better use of the space on the screen.  Any help will be greatly appreciated.

---

### Post by tgalati4 on 2010-03-26
Look through the file:

cat /var/log/Xorg.0.log

It will go through the details of the open driver (ati, rage, radeon, etc) that gets loaded.  If you have low video memory, then it will be noted in the log file.  You may need to specify a custom modeline in your xorg.conf.

Run gtf in a terminal and cut and paste that into xorg.conf:

tgalati4@tpad-Gloria7 ~/Desktop $ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

---

### Post by sdtrott on 2010-03-29
Thanks for your response.  I ran GTF and my results were identical to what you indicated in your response.  I think I am understanding you correctly to say that I should take the results of that command and paste it into xorg.conf, however, when I opened xorg.conf, I did not see any similar existing entries in there, so that prompted me to wonder if I am understanding you correctly. Also, the file's permissions are set at "read-only" so I don't know what I need to do to change that (perhaps it is similar to UNIX?). I am still somewhat new with Linux but I can grasp most of its concepts once they are explained.

I am attaching a document with the contents of the xorg.conf and xorg.0.log files because I am not sure what is going on in the way the graphics driver is being loaded. There are references to NVIDIA which I thought only had to do with the previous video card (XFX) that was present when I initially installed Ubuntu.  Is it possible that there are NVIDIA drivers associated with the previous graphics card that are causing conflicts with the ATI card that is currently installed?

---

