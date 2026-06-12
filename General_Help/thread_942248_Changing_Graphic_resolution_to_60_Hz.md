---
title: "Changing Graphic resolution to 60 Hz"
date: 2008-10-09
forum: General Help
---

### Post by nima352000 on 2008-10-09
Hi guys , i need some help here to change my graphic resolution to the range between 60-70 Hz. im running Ubuntu 7.10 gusty dual booting with windows vista ultimate. i did not have any issue till few days a go my display went black and i could not boot to normal mode windows/ubuntu . so i called dell and they told me my graphic card is dead. when they send tech to change the main board and graphic card he told me that since im using linux i should change the resolution to 6-70 hz otherwise it is going to fry my board and card again!!!! anyways i want to keep ubuntu in my system i just need some help of how can i check my resolution and how can i change it!! my card is  Nvidia GEForce GO 7400, 256mb 
dell latitude D820 intel core 2 cpu @1.83GHZ , 4GB ram
please let me know if you need any additional information. tnx in advance


HERE IS INFO FROM MY NVIDIA control panel
NVIDIA System Information report created on: 10/09/2008 00:18:26
System name: NIMA-PC

[Display]
Processor:		Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz (1829 MHz)
Operating System:	Microsoft Windows Vista (Service Pack 1)
DirectX version:	10.0 
GPU processor:		GeForce Go 7400
ForceWare version:	156.69
Total available graphics memory:	1662 MB
Dedicated video memory:	256 MB
System video memory:	0 MB
Shared system memory:	1406 MB
Video BIOS version:	5.72.22.21.fe
IRQ:			16
Bus:			PCI Express x16

[Components]

nvCplUIR.dll		1.4.220.00		NVIDIA Control Panel
nvCpl.cpl		1.4.220.00		NVIDIA Control Panel Applet
nvExpBar.dll		1.4.220.00		NVIDIA Control Panel
nvCplUI.exe		1.4.220.00		NVIDIA Control Panel
nvViTvSR.dll		7.15.11.5669		NVIDIA Video and TV Server
nvViTvS.dll		7.15.11.5669		NVIDIA Video and TV Server
nvDispSR.dll		7.15.11.5669		NVIDIA Display Server
NVMCTRAY.DLL		7.15.11.5669		NVIDIA Media Center Library
nvDispS.dll		7.15.11.5669		NVIDIA Display Server
NVCPL.DLL		7.15.11.5669		NVIDIA Compatible Windows 2000 Display driver, Version 156.69 
nvGameSR.dll		7.15.11.5669		NVIDIA 3D Settings Server
nvGameS.dll		7.15.11.5669		NVIDIA 3D Settings Server

---

### Post by JacobSteelsmith on 2008-10-09
You'll need to edit your xorg.conf file. Check out [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) for instructions on changing and specifying resolution and refresh rates.

---

### Post by cariboo on 2008-10-09
TO set up  the modlines in /etc/X11/xorg.conf press Alt-F2 and enter displayconfig-gtk this should allow you to set resolution  and frequencies.

Jim

---

### Post by jonian_g on 2008-10-09
> **cariboo907 said:**
> TO set up  the modlines in /etc/X11/xorg.conf press Alt-F2 and enter displayconfig-gtk this should allow you to set resolution  and frequencies.

Jim

That's right, but use sudo.

---

### Post by nima352000 on 2008-10-09
THNKS for replay , im gonna go and try it

---

### Post by nima352000 on 2008-10-09
i was tying to login in normal mode . but fonts in welcome screen were huge and when i loged in all the icons in desktop were big and i didn't had any menu in my up task bar . i don't know what to do

---

