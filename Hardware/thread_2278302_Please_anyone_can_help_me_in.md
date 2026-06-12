---
title: "Please anyone can help me in"
date: 2015-05-15
forum: Hardware
---

### Post by Princeash on 2015-05-15
i am using Linux before more than year and i have a big problem which i couldn’t resolve it i am so sad really i tried  many dist ubuntu kubuntu Lubuntu xbuntu ubuntu gnome i tried debian and arch linux and many many distros ...  "my Laptop is "Toshiba c660-111 Pro satellite"

the problem in the screen you can notice in my video that the screen is crashing you can see 

[https://youtu.be/VKSvWC62srg](https://youtu.be/VKSvWC62srg)

i tryed many intel Grapic drivers and intel-linux-graphics-installer but the same problem my card is "Mobile Intel® GM45 Express Chipset x86/MMX/SSE2"

and this is the output of "lspic"

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
14:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)


Please help please

---

### Post by dino99 on 2015-05-15
the i965-va-driver from the ubuntu archive should do the trick
> This package contains the video decode and encode driver backend for the Intel G45 chipsets and Intel HD Graphics for the Intel Core processor family. The supported platforms include:
 * Cantiga, Intel GMA 4500MHD (GM45)
 * .... 
 there is also some related 'toshiba' packages into the archive that might be installed: install 'synaptic' and search about 'toshiba' with it, and watch the package details
or try their driver  [http://www.toshiba.eu/innovation/download_drivers_bios.jsp?service=EU](http://www.toshiba.eu/innovation/download_drivers_bios.jsp?service=EU)

---

### Post by v3.xx on 2015-05-15
You are on Unity/compiz desktop.  I do not run your chipset, but got some forum hits.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Mobile+Intel%C2%AE+GM45&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Mobile+Intel%C2%AE+GM45&sa=Search&cof=FORID:9)

Even though you have tried several flavors, I would still use another desktop that uses less computer resources as a test.

The Flashback desktop (using metacity) can easily be added to a Unity install.
```
sudo apt-get install gnome-panel
```
Reboot and at the login screen, click on the icon and choose your desktop.

What sort of video drivers do you have to choose from?  And how much ram do you have?

---

### Post by tgalati4 on 2015-05-15
You might have better luck with MATE or a lighter desktop.  [http://ubuntuforums.org/showthread.php?t=2201830&highlight=Mobile+Intel+GM45+Express](http://ubuntuforums.org/showthread.php?t=2201830&highlight=Mobile+Intel+GM45+Express)

---

