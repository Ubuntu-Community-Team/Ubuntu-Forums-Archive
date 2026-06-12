---
title: "Desktop effects all messed up"
date: 2009-04-14
forum: Hardware
---

### Post by buzypi on 2009-04-14
Hi,

I use Ubuntu Intrepid on my HP Laptop.

I recently connected my laptop to a projector and when I disconnected it from the projector, a few things were broken:
* Alt+Tab is not working anymore.
* I have Cairo-dock installed and it shows a black patch behind the dock when the icons expand.
* The animations in the taskbar when an application is opened are not smooth anymore. It shows a black expanding rectangle instead of an expanding image.
* The number of workspaces has reduced from 4 to 2. The names are changed to Desk 1 and Desk 2. Further, if I try to increase them back they come up as a row, instead of as a grid.
* Most animations from Compiz are broken.

I am seeing this issue in Intrepid to which I upgraded recently. I have seen such an issue before with Hardy, but it used to be only for the current session and a restart of the system would bring back everything.

Also in Intrepid, my external monitor is not automatically recognized. I have to connect it, go to Preferences -> Screen Resolution, Detect the display, Mirror and Apply.

Here are some details that might be useful:
# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Any help in restoring my display is greatly appreciated.

Regards,
Gautham

(Cross posted in Desktop Environments)

---

### Post by Afisamuleal on 2009-04-14
It seems Compiz-Fusion isn't running. I have problems like this too. I didn't come up with a great fix, but:

Find the command to load the Compiz tray icon (edit menus, find it, properties/edit), and add it to:
Menu --> Preferences --> Session

When your computer starts, right click and reload compiz-fusion.

Compiz fusion has taken control of alt+tab and the like with pretty effects :)


As for the monitor, I'm not sure, I'd have to read up on it, Sorry.

---

### Post by buzypi on 2009-04-14
Hello Afisamuleal,

Can you give me the exact command to add to sessions?

I tried compiz --replace - doesn't seem to work. :(

503:~$ compiz --replace &
Checking for Xgl: [3] 7659
504:~$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
Gtk-Message: Failed to load module "libgnomenu": libgnomenu.so: cannot open shared object file: No such file or directory





504:~$ ps aux | grep compiz
gautham   7715  0.0  0.0   3236   788 pts/1    S+   13:56   0:00 grep compiz
[2]-  Done                    compiz --replace
505:~$ ps aux | grep metacity
gautham   7659  2.0  0.8  18088  9092 pts/1    S    13:56   0:00 /usr/bin/metacity --replace --replace
506:~$ 


Thanks,
Gautham

---

### Post by Afisamuleal on 2009-04-14
Hey, ok, from Ocxic at
[http://ubuntuforums.org/showthread.php?p=6064829]("http://ubuntuforums.org/showthread.php?p=6064829")

try

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by buzypi on 2009-04-15
Awesome! That fixed it for me. Thanks a ton!

---

