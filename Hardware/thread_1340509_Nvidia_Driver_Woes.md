---
title: "Nvidia Driver Woes"
date: 2009-11-28
forum: Hardware
---

### Post by CleverCognomen on 2009-11-28
Long story short, with my Nvidia card in the system I only get a blank screen when booting, and with the card removed, I can't seem to install the Nvidia drivers. A more detailed explanation:


**1:** Card installed, pumping HDMI to 22" monitor, boot into Ubuntu.
Outcome: Goes to black screen, no signal sent to monitor.

**2:** Nvidia card removed, onboard Intel chip pumping VGA to 15" monitor.
Outcome: Ubuntu works fine, but I can't install the Nvidia drivers (System --> Admin --> Hardware Drivers?) as no Nvidia hardware is detected.

**2a:** Download drivers from Nvidia site and attempt to run them. Discover I must exit X server to do so.

**2b:** Exit X server, again run Nvidia drivers. Installation reports that no Nvidia hardware is detected, the "kernel source files" don't match up or are missing, and that the installation has failed.

At this point I just gave up in frustration and booted back into Windows 7. I'm not a new user to Linux/Ubuntu. I ran Linux Mint 6  with Fluxbox for about 6 months (with the same hardware) as my sole operating system until I got my hands on Windows 7 RTM, and I've repeatedly poked around in Backtrack 3 (Slackware sucks :p). Trying to get Karmic Koala working has been my most frustrating Linux experience since I first dabbled with Gusty Gibbon.

How can I force Ubuntu to make the Nvidia drivers work even without having the card installed? Any help would be appreciated.

**My system specs:**
Dell Inspiron Slim Tower 540s
Intel Core 2 Quad Q9400S (65W) 2.66GHz Quad Core
8GB RAM
Sparkle Nvidia GeForce 9800GT low-profile card w/HDMI
640GB hard drive
DVD burner, card reader
Seasonic 300W TFX PSU
Scythe Shuriken low-profile CPU cooler

Windows 7 Ultimate x64 RTM 
Ubuntu Karmic Koala x64

Gateway 22" HD monitor
KDS 15" monitor (only used for annoying debugging situations like this)

---

### Post by pbrane on 2009-11-28
The problem with trying to install the nvidia driver without the hardware is that the nVidia installer needs to figure out which nVidia chipset you have. so I don't think there is a way to install without the actual hardware.

I'm not sure if you have a clean install of ubuntu or not. So you might try running this command in a terminal to clean up your X config.
**sudo dpkg-reconfigure -phigh xserver-xorg**
This should allow you to use your nVidia card and get the drivers installed. 

Have you tried CTRL+ALT+F1 to get to a console when you boot to a blank screen with the nVidia card installed. If you can get to a terminal after installing the card then you can run that command there as well.

Here is a good resource for installing the drivers properly. You may need to adjust this for your installation though.

[http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")

Note that the latest driver is 190.42. I'm using it now.

---

### Post by almufadado on 2009-11-28
Make sure the add-on card is firmly inserted and secured.

Make sure the monitor cable is connected to the right  card.

Check your bios to see if you can disable the on-board graphics, if yes make sure it is disabled.

Check bios for any possible setting related to the on-board graphics, disable all realated to  it.  (ex: vga -> pci/agp set it to agp (or pcie if that's the case))

---

