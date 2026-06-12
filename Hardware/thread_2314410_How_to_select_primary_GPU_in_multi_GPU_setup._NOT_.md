---
title: "How to select primary GPU in multi GPU setup. NOT HYBRID."
date: 2016-02-20
forum: Hardware
---

### Post by jeffery3 on 2016-02-20
I'm ashamed that I even have to post this problem because this isn't the first time i've handled it. About 7 months ago, I had a similarly unique GPU setup with another computer. For the life of me, I cannot locate the thread that solved my problem. Typically the query is littered with discussions about hybrid graphics.

Well, I am not using any sort or hybrid graphics.

My system has 2x NVIDIA GPU's. Currently it is using the GeForce GT 720 (EW....I know...)
I would much rather use the GeForce GTX 750. 

In the past with that other "similar" issue, all I had to do was edit the xorg.conf file and change the PCI bus code and PRESTO! It worked.....

However..... in this system, there is no xorg.conf file for me to edit... So, any guidance on how to get this thing rolling in the direction I want would be much appreciated. I must mention however, i CANNOT remove the GT 720. I know that sounds odd, but this system wont show me the POST while booting utilizing the GTX 750. I've tried removing the GT 720, hoping it would boot using the GTX 750 but it just doesn't happen.

Also, I know this will work because I successfully ran this setup in windows 8, 8.1 & 10. Luckily for me, the Nvidia control panel for Windows is much more robust and allows you to select which GPU. The Nvidia control panel for ubuntu/linux however not so much.... :-(
[B]
[SIZE=3]lspci:[/SIZE]
[/B]
**0b:00.0 VGA compatible controller: NVIDIA Corporation GK208 [GeForce GT 720] (rev a1)**
0b:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
[B]13:00.0 VGA compatible controller: NVIDIA Corporation GM107 [GeForce GTX 750] (rev a2)

[SIZE=3]
nvidia-xconfig --query-gpu-info

Number of GPUs: 1

[/SIZE][/B][SIZE=2]GPU #0:
  Name      : GeForce GT 720
  UUID      : GPU-ba078c87-cf12-10cc-d0cc-9e9eb19f72d2
  PCI BusID : PCI:11:0:0

  Number of Display Devices: 1

  Display Device 0 (TV-1):
      EDID Name             : Samsung U28E590
      Minimum HorizSync     : 30.000 kHz
      Maximum HorizSync     : 90.000 kHz
      Minimum VertRefresh   : 24 Hz
      Maximum VertRefresh   : 75 Hz
      Maximum PixelClock    : 300.000 MHz
      Maximum Width         : 3840 pixels
      Maximum Height        : 2160 pixels
      Preferred Width       : 3840 pixels
      Preferred Height      : 2160 pixels
      Preferred VertRefresh : 30 Hz
      Physical Width        : 610 mm
      Physical Height       : 350 mm[/SIZE][B][SIZE=3]


[/SIZE]

[/B]

---

### Post by jeffery3 on 2016-02-21
Ok. I figured it out. The answer is here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

For my situation, I needed to run this command:[B]sudo nvidia-xconfig -multigpu=on
[/B]
Rebooted & now the GTX 750 shows up in the Nvidia control panel. :-)Hope this helps anyone else who may have this conundrum.

---

