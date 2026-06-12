---
title: "Installing NVIDIA Driver in ASPIRE 4750G"
date: 2011-05-13
forum: Hardware
---

### Post by neo_phyte on 2011-05-13
Hello Ubuntu gurus,

I had bought this laptop (Acer Aspire 4750G) with this NVIDIA GEFORCE GT540M. The issue is I am installing Ubuntu 10.04 into it. But I got some problem installing NVIDIA drivers on this laptop:

The driver is available in Nvidia.com for this specific NVIDIA version.

1. I tried running this command as root:

```
sh /home/dudeskie/NVIDIA-Linux-x86-270.41.06.run
```

But I get this error:

[COLOR=Red][B]ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
[/B][/COLOR]
2. I tried killing my X server by doing this command:

Switch to a screen without xorg using the shortcut ALT + CTRL + F1

But all I can see is a blank screen with a flicker on the upper side of my display/monitor. According to the forum here this will lead me to login screen without using X server. But all I can see is a blank screen.


3. Looking into System -> Preferences -> Monitors, I have this

[B]Unknown
Monitor Unknown

[/B]
So, I really need your advise on this, on how I can properly install my INVIDIA driver. I am newbie to any linux distro. So, please list down all commands that I need to run for this.

Thanks in advance.

neo_phyte

---

### Post by neo_phyte on 2011-05-14
For my updates here, I can now see my tty1 screen. There is a post in the forum on how to fix the ALT + CTRL + F1, so I followed that one.

I was able to install the NVIDIA driver. BUT I have another problem which need your help.

After rebooting, I have this problem:

[COLOR=Red][B]Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernedl module. Please check your system's kernel log for additional error message.
Failed to load module "nvidia" (module-specific error, 0)

No drivers available.
[/B][/COLOR]

How can I solve this problem. Please help...


Thanks,

-neo_phyte

---

### Post by neo_phyte on 2011-05-14
Looks like nobody wants to help me.

Guys, I really need your help.

Thanks in advance.

---

### Post by mykel_blacklist on 2011-05-16
im also new to linux distro.. first look at it , iam impressed by the way it works.. 

but when i tried installing it on my new notebook.. acer aspire 4750g im having problems with my graphics card installation.. i dont know yet whats really the problem? i am so confused by it. tried so many commands on terminal.. based on what i have read from forums.. but non of them is working for me..

hope someone can help by posting a step by steps command lines .. im using linux mint julia. gnome 32bit os..

problem i cant install my graphics card 3d acceleration.. 

thanks to someone that can help

---

### Post by judedawson on 2011-07-09
Hi Guys, 

I recently bought an Acer Aspire 4750G with the Nvidia GeForce GT520m graphics card. I did a clean install of Kubuntu 11.04 32bit. 
My laptop does not exhibit the problems that you have highlighted. Kubuntu detected all drivers (as for as I can tell) and works generally well. There are some issues which need to be addressed (battery discharges in only 4hrs, KWin and Rekonq suddenly crashing and laptop suddenly hanging while running LibreOffice). However, it has not developed any graphics card issues.

Did you guys do a clean install of Ubuntu from an ISO file (with MD5 checksum OK) from the Ubuntu website burned to a CD/DVD?

You could try that.

BTW, mykel_blacklist, you're running Linux Mint, mate. You would get better support if you post your query on the Linux Mint Forums :) 

Cheers.

From,
Jude

---

### Post by vinayaksawant on 2011-07-09
Do worry buddie. 
If you want to install nvidia driver goto following site for complete information.
" https://help.ubuntu.com/community/NvidiaManual"
or simply you may goto system settings>additional drivers to install nvidia drivers

---

### Post by judedawson on 2011-07-10
Hi there vinayaksawant, 

Thanks for the suggestion. I checked and discovered <In Kubuntu it's 'Application - System - Additional Drivers'> that the drivers for 3D acceleration were not installed. I've installed them. I'm not very sure how it will improve my laptop performance but there's no harm done by installing it, I suppose ;)

From,
Jude

---

### Post by judedawson on 2011-07-15
Hi guys, 

I forgot to mention... After installing the NVIDIA accelerated graphics driver, the F8 (KWin desktop overview) and F11 (3D desktop cube) features as well as preview view of mimimised files at control panel did not work anymore. 

I had to uninstall the driver to return to normal. 

So I guess in this example, less is indeed more... ;)

From,
Jude

---

