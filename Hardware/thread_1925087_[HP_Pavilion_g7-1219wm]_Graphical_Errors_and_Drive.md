---
title: "[HP Pavilion g7-1219wm] Graphical Errors and Driver Issue"
date: 2012-02-13
forum: Hardware
---

### Post by Error 418 on 2012-02-13
First attempt with Ubuntu on this laptop was with 11.10.  Was a no-go, as the live CD resulted in a blank screen.  After doing some looking about, I saw that I would have to try the 12.04 Alpha 2 release. 

With that said, here are my specs. 

> **"Video Card"] 
brian@g7:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
[/QUOTE]

[QUOTE="Other ATI PCI's] 
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
[/QUOTE]

Right. That out of the way. Once again, I'm running Ubuntu 12.04 Alpha 2 with Gnome 3.2 (Had a bit of trouble getting anything but the basic set-up to work.) 

Here is my issue.  On log-in, log-out and right clicking menus, I get various graphical issues. Scrambled screen and such.  I know this has been reported before, but couldn't remember what you call it ... Brain fart on my end. The attached screenshot is the result of "logging-in". Lasts only about 30 seconds.

Second issue.  Using ATI card.  Under "Additional Drivers"  I have an ATI card listed with a secondary option above it. Apparently an update for the same card. After installation and reboot, things revert back as if no software had been installed.   

As for my level of experience.  I know enough to work my way through the terminal and thoroughly muck things up if I try "really, really hard."   said:**
>  
brian@g7:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)


---

### Post by Error 418 on 2012-02-15
Bump.

Found some more information.  Not directly related, I don't think, but something to keep in mind.

[http://ubuntuforums.org/showthread.php?t=1894466](http://ubuntuforums.org/showthread.php?t=1894466)  Thread in paticular was solved (Talking about instillation and booting.) and deals with the HP Pavilion g7-1279dx model. 


Additionally.  I preformed a reinstall and didn't activate the AMD drivers this time, nor did I attempt to work with Gnome 3.  Haven't been having the graphical problems.  I will, however, leave this open until I find the reason for the problem.

---

### Post by jonnyboysmithy on 2012-02-15
I dont know I this applies to you but I also used to get scambled screen like that.
If you have the proprietary driver installed then maybe this helps..
EDIT: I'm using HD 6740m on HP DV6 6023TX

> After some experimentation it seems the critical step for me was to  switch to eco graphics before restarting after I installed the driver.
After installing the driver you need to configure it with aticonfig:
```
sudo aticonfig --initial
```And after that tell it to use the power save graphics:
```
sudo aticonfig --px-igpu
```Then restart. For me that prevents it from getting a scrambled splash screen.

---

### Post by Error 418 on 2012-02-16
> **jonnyboysmithy said:**
> I dont know I this applies to you but I also used to get scambled screen like that.
If you have the proprietary driver installed then maybe this helps..
EDIT: I'm using HD 6740m on HP DV6 6023TX


Thats interesting.  I'll give that a try. [EDIT] Your solution seemed to work.  Thank you.


Some new issues have cropped up, thought I believe this is largely to user error on my  part and careless updating.
Ubuntu was running fine without updates, after the re-install.  After updates, I began getting graphical errors once more, and this time without activating proprietary devices. 

I've also received two errors that worry me.  The first one, that I managed to make a log of ...

> The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

unity, compiz, compiz-core, compiz-gnome, compiz-plugins-default, compiz-plugins-main-default, libcompizconfig0, libdecoration0, libgl1-mesa-glx, libglapi-mesa, libindicator3-7, libnux-2.0-0, libnux-2.0-common, unity-commonThe second one followed immediately the previous error ... 

> System Problem Detected

This problem report is damaged and cannot be processed.

TypeError(Error('Incorrect padding',),)Once again, I believe this is user error and careless updating on my part. 

Will attempt starting from scratch again. It's a darn good thing I enjoy this kind of thing, otherwise I'd be overly frustrated.  Curious to see what Canonical has in store for the 12.04 Beta 1 release in a couple weeks.

---

