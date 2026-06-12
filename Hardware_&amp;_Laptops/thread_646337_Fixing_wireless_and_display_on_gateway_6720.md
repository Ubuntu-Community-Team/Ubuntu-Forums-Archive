---
title: "Fixing wireless and display on gateway 6720"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by Chipmaster on 2007-12-21
Usually when I have an issue with specific model of computers, I have
been able to find specific forum posts about the exact hardware I am
using with a simple google search.  Since I could not find any such
topics about my specific hardware this time, I decided to create the
topic.

I need to fix the display drivers and wireless on a gateway ml6720.
The gutsy install cd boots up fine and the installer works, but the
display is noticeably wrong (in a weird way where the gnome panels
only stretch for around 3/4 of the width and height of the screen, but
the background and mouse are allowed to go to the edges).  The
wireless is also no recognized.

An output of lspci:

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

For the wifi, I plan on looking into native linux support before turning to ndiswrapper.  As for the display, I'll have to look into this some more because I'm already running the 'intel' driver.

Any help/advice or suggestions would be greatly appreciated.

I attached an image of the messed up display.

Update:

On the wireless front I was unable to find a native linux solution, but ndiswrapper does mention this laptop by name as one that it can work with.  The driver you need to work with ndiswrapper is here:
[ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)
and I'm following the guide to installing it here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

Update:

Ok, wireless is up and running.  Here's the procedure:

Get ndiswrapper:
```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```
Download the driver from [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)
Extract the driver
Install the Windows 98 driver with ndiswrapper
```

sudo ndiswrapper -i ~/RTL8187B/Win98/net8187b.inf

```
Load ndiswrapper
```

sudo modprobe ndiswrapper

```
Your card should be detected at this point.  If it's not you can try
going to Ndiswrappers website.  I got mine working using these pages:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

Make it load on reboot:
```

sudo ndiswrapper -m

```

That did it for me.

---

### Post by Chipmaster on 2007-12-21
Alright, I'm having trouble here on this display issue.  I tried reconfiguring xserver, compiling an intel driver that supposedly has support for my card (GM965/GL960).  Nothing has had any effect.  To clarify:  The monitor can handle 1280x800 and the background and x config files back this up.  But the panels and desktop size are restricted to 1024x768 as shown in the screenshot attached.  I noticed that screen resolution and screen and graphics both show that it's 1024x768.  When I try to change them to 1280x800 and restart x, they just revert to 1024x768.

Help on this would be appreciated.

---

### Post by Daspah on 2007-12-21
I have the same display problem and also sound problem.

Notebook -- (widescreen) Gateway P-6825

Please help us =/

---

### Post by Chipmaster on 2007-12-21
Interestingly I tried moving around the panels and I can get the bottom one to go the full length.  This makes me think that maybe this is a bug in gnome?  I'm going to try out KDE and TWM to see if I can get anything to work.

Update:

Ok, fluxbox seems to work and also I I stretch unmaximized windows past the bounds of the desktop and then maximize them, they maximize to the proper length and height.  I think I'll go visit the gnome guys and see if they've seen this before.

Update:

Ok somehow I missed  [this](http://ubuntuforums.org/showthread.php?p=3767658) thread where they solve the problem.  I'm going to try it out on the laptop.  Assuming this works, this should be all that's required to get it fully working.

---

### Post by mjziegle on 2007-12-26
See this thread

[http://ubuntuforums.org/showthread.php?t=566947]("http://ubuntuforums.org/showthread.php?t=566947")

---

### Post by Diavo on 2008-01-03
Thank you!!  The fix for the wireless worked for my Gateway 6720! =)

I installed the Win98 drivers and it installed but I got no response from my wireless (even though it confirmed being operational).  So after a reboot I uninstalled them, then the WinXP drivers.  Installed and sort of worked, so I uninstalled those and reinstalled the Win98 drivers and they work fine.
In fact, I think the wireless works better-stronger-faster under Ubuntu than under Vista. =)

--Diavo

---

