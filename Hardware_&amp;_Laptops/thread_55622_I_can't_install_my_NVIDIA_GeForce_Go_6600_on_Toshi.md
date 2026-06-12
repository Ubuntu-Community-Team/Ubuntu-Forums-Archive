---
title: "I can't install my NVIDIA GeForce Go 6600 on Toshiba Tecra S2"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by x1c0 on 2005-08-09
hi!

I can't instal my videocard, i do this (ubuntuguide):

1.
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

 
2. Insert the following lines into the new file 
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;a.. Save the edited file (sample)

3. restart GNOME without rebooting computer

now when i've restarted, i can't see anything... all black!! ](*,)

here goes lspci:

0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FBM (ICH6M) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0148 (rev a2)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4362 (rev 15)
0000:06:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:04.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:04.1 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:04.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:04.4 0805: Texas Instruments: Unknown device 8034 

HELP! what can i do?

to see anything again i enter in recovery mode and do: sudo nvidia-glx-config disable, but what i do now?? :?

---

### Post by x1c0 on 2005-08-10
please.. :( any one can help me???

---

### Post by x1c0 on 2005-08-16
Is my question stupid? 

Or nobody know the anser?

thanks for all the help people :neutral:

---

### Post by heltreko on 2005-08-16
Not a stupid question. Only difficult to answer.

Try CTR+ALT+BACKSPACE to kill the failed X (the black screen). If you end up at a login prompt login and then. 

[I]cp /etc/X11/xorg.conf /etc/X11/xorg.conf_failed
cp /etc/X11/xorg.conf_backup  /etc/X11/xorg.conf[/I]

This returns you to your old X-config file. After this try.

*startx*

And you should hopefully be back at an working X environment but using your old drivers.

Then look in /var/log/Xorg.log.old to see what went wrong.

From reading your lspci

*0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0148 (rev a2)*

It seems like the video card isn't properly recognised.

---

### Post by tseliot on 2005-08-16
[QUOTE=x1c0]please.. :( any one can help me???[/QUOTE]

I've just made an easy HOWTO, here's the link:

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368)

---

