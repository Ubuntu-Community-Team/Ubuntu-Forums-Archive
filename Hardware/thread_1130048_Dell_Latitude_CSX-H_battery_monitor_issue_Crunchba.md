---
title: "Dell Latitude CSX-H battery monitor issue Crunchbang Linux"
date: 2009-04-19
forum: Hardware
---

### Post by Purplecatty on 2009-04-19
I just installed Crunchbang Linux 8.10 (derive from Ubuntu) and It is showing battery monitor on red level "empty" while battery is fully charged. 

Dell latitude CSx-H Laptop
500mhz Coppermine processor
13" lcd monitor
1 USB
1 D-sub VGA jack
1 Docking jack
SCSI Flashdrive adapter w/ 8GB SDHC
Zydas USB Wireless adapter (works out of the box)
6 cells Li-Ion batteries


 I clicked to open "laptop battery 0.0% 

Here's the info

Product: LIP861VVDLP
Status: Discharging
Percentage charge: 0.0%
Vendor: Sony Corp.
Technology: Lithium ion
Serial number: 30190
Model: LIP861VVDLP
Design charge: 36.0 Wh
Charge rate: 23.7 W

Percent Charge: is 0.0%

I installed Xubuntu 8.10 and Battery monitor worked fine but I uninstalled it cuz it was laggy and slow going around.  Crunchbang seem much better and faster getting around.

What happened is that I tried to install Crunchbang to SCSI Flashdrive (SD to 44pins IDE adapter with 8GB turbo 150X SDHC plugged) via laptop's external drive and it's getting Grub installation error every time.  So I took out the SCSI flashdrive and plugged it to IDE to USB adapter (3-in-one drive adapter).  I successfully installed Crunchbang with no issue and transfer SCSI flashdrive back to laptop (I just shut down the desktop pc after installing Crunchbang without reboot when it requested).  I didn't have to reconfigure the X11.org.  

What do you suggest to fix the problem..

Thanks
Catty

---

### Post by Purplecatty on 2009-04-19
Never mind....:confused:

It somehow fix itself..  I think I ran update and later in the morning, I shut down the laptop then powered up in the afternoon.  It fixed itself and now I can see battery monitor showing battery discharge rate.

If anyone recently installed Crunchbang Linux on their laptop, be sure to update by using "Super + U" key combo (without the quotes).  This may resolve issue with the battery monitor and other things.

Catty

---

