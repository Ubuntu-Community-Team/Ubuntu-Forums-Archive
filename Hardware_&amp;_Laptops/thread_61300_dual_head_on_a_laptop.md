---
title: "dual head on a laptop"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by axl123456 on 2005-08-31
Hi,

I have been looking around the forum for a solution to having dual head display on my laptop and I found nothing that works for me!

I have a Fujitsu Siemens laptop with an ATI Rage Mobility (Mach 64).

When I was running Windows XP, I could set it up to extend my desktop to my 18' Philips LCD screen (laptop resolution: 1024x768, Philips: 1280x1024) so the hardware is able to do it.

With Ubuntu, I tried playing with xorg.conf without success. All I get is a clone display on the external monitor, and both 1024x768.

Note that I have only one video card on busID 0:20:0.

lspci -X

PCI:0:0:0 Host bridge: Intel Corp. 82440MX Host Bridge
PCI:0:0:1 Multimedia audio controller: Intel Corp. 82440MX AC'97 Audio Controller
PCI:0:0:2 Modem: Intel Corp. 82440MX AC'97 Modem Controller
PCI:0:7:0 Bridge: Intel Corp. 82440MX ISA Bridge
PCI:0:7:1 IDE interface: Intel Corp. 82440MX EIDE Controller
PCI:0:7:2 USB Controller: Intel Corp. 82440MX USB Universal Host Controller
PCI:0:7:3 Bridge: Intel Corp. 82440MX Power Management Controller
PCI:0:17:0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
PCI:0:18:0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
PCI:0:19:0 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller
PCI:0:19:1 CardBus bridge: O2 Micro, Inc. OZ6933 Cardbus Controller
PCI:0:20:0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M

And I cannot create 2 devices in xorg.conf like this:

Section "Device"
Identifier "ati0"
Driver "ati"
BusID "PCI:0:20:0"
Option "UseFBDev" "true"
Screen 0
EndSection

Section "Device"
Identifier "ati1"
Driver "ati"
BusID "PCI:0:20:0"
Option "UseFBDev" "true"
Screen 1
EndSection

Because then I have the following error in /var/log/Xorg.0.log:

(EE) ATI: XF86Config Device sections "ati0" and "ati1" may not be assigned to the same adapter.
(EE) No devices detected.

And I cannot start GNOME!

Do you think there is a solution to my problem?

Thank you for your help.

---

### Post by s_p_a_r_k_y on 2005-08-31
Check out my attached file. I have a dual screen setup.

---

### Post by axl123456 on 2005-09-01
Thank you for your help s_p_a_r_k_y,

It feels good to know that I'm not alone on this planet!;-)

So I've tried your config in several steps:

1. Copied xorg.conf.ati_dual.txt to /etc/X11/xorg.conf and replaced BusID with my own (PCI:0:20:0). Then restarted gdm.
I obtained the following error:
-> "Failed to load module "fglrx" (module does not exist, 0)".

2. I replaced Driver "fglrx" with Driver "ati" and restarted gdm.
-> "ATI: XF86Config Device Sections "ATI Graphics Adapter Connector 0" and "ATI Graphics Adapter Connector 1" may not be assigned to the same adapter".

3. I commented out the BusID "PCI:0:20:0" for the Device "ATI Graphics Adapter Connector 1" like you did for the Device "Standard VGA" and restarted gdm.
-> And I obtained the same error message as in step 2.

So my conclusion is (at least I suppose): that the default ATI driver doesn't allow assigning 2 devices to the same adapter, but that the fglrx driver does (as it does for you).
However, I've already tried to install the fglrx-control package from Synaptic before and it seemed no to be compatible with my old ATI Rage Mobility adapter, as I had actually read it on some other thread (in this thread they say I need a mach 64 driver: [http://www.ubuntuforums.org/showthread.php?t=7200&page=4&pp=10)](http://www.ubuntuforums.org/showthread.php?t=7200&page=4&pp=10)).

And unfortunately, ATI doesn't provide linux driver for this adapter:
"Display drivers and multimedia applications for notebooks with ATI graphics solutions are available for download from your Notebook manufacturer."
([https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300))
Neither does Fujitsu Siemens, my notebook manufacturer (http://www.fujitsu-siemens.com/support/downloads_1.html)!:-?

I've also tried the mach64 driver but without success.

Anyway, I will try again all drivers that have a chance to work: mach64, fglrx, SciTech...

Thank you for your help.

---

### Post by beefsprocket on 2005-09-01
I don't know if it will help, but perhaps downloading and installing the Xorg driver from ATI would allow you to use the fglrx module. I have no idea whether it will support a Mach 64. Regardless of what ATI says about notebook cards, downloading and installing ATI's Xorg driver generally works quite well.

---

### Post by chillpetter on 2005-09-01
I have the exact same problem here... I did copy almost all of the xorg.conf from s_p_a_r_k_y, and I got the external monitor to work (my config is called XF86Config-4). But the screens are still just clones of eachother. How can I tell Ubuntu that I want to use screen1 (and its configuration), instead of screen0 ?

---

### Post by axl123456 on 2005-09-02
I don't know if it's of any interest, but I don't think Ubuntu requires any special configuration for a clone dual display. It was working upon OS installation for me anyway.
But maybe you are a step beyond me, because although my clone display is correct, I cannot increase the screen resolution on the external display (I have 1024x768 for both laptop and external displays whereas externel is supposed to go up to 1280x1024).

Could you get a higher resolution then laptop display allows? Could you get 2 different resolutions on each display?

---

### Post by axl123456 on 2005-09-02
I've just tried installing the ATI xorg driver as suggested by beefsprocket:
[http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run]("http://www2.ati.com/drivers/linux/ati-driver-installer-8.16.20-i386.run")
And the installation log (/usr/share/fglrx/fglrx-install.log) has the following error:
"[Error] Kernel Module : Failed to install compiled kernel module - please consult readme." (don't know where is this readme by the way!).
(log file attached).
I then ran the fglrxconfig that started with:
```
This program will create the ATI "xorg.conf" file
- based on your selections - for the following video cards...
  - ATI FireGL V3100 / V3200 / V5000 / V5100 / V7100
  - ATI FireGL X1 / X2 / X3 / Z1 / T2
  - ATI FireGL 8700 / 8800
  - ATI Mobility FireGL T2 / 9100 / V5000
  - ATI Mobility Radeon 9000 / 9200 / 9600 /9800
  - ATI Mobility Radeon X700
  - ATI Radeon 8500 / 9000 / 9100 / 9200
  - ATI Radeon 9500 / 9550 / 9600 / 9700 / 9800
  - ATI Radeon X300 / X600 / X700 / X800 / X850
  - ATI IGP Radeon 9100 / 9200/n  - ATI IGP Mobility Radeon 9000 / 9100/n
```
And my card is not one of these (ATI Rage Mobility 64).
And indeed, at this end of configuration, it says:
```
Probing PCI bus for a supported graphics device...
unable to find any of the subsequent graphics boards:
  - ATI FireGL V3100 / V3200 / V5000 / V5100 / V7100
  - ATI FireGL X1 / X2 / X3 / Z1 / T2
  - ATI FireGL 8700 / 8800
  - ATI Mobility FireGL T2 / 9100 / V5000
  - ATI Mobility Radeon 9000 / 9200 / 9600 /9800
  - ATI Mobility Radeon X700
  - ATI Radeon 8500 / 9000 / 9100 / 9200
  - ATI Radeon 9500 / 9550 / 9600 / 9700 / 9800
  - ATI Radeon X300 / X600 / X700 / X800 / X850
  - ATI IGP Radeon 9100 / 9200/n  - ATI IGP Mobility Radeon 9000 / 9100/n
After starting X11, auto-detection will take place.
If you want to forcefully bind to a specific PCI bus slot at a later time
then you have to edit the fglrx-BusID entry in your xorg.conf file.
```
As expected, when I rebooted, GNOME could not find a device and I had to use my xorg.conf backup in order to start GNOME.

Indeed if we read the [ATI Proprietary Linux Driver FAQ]("http://www.ati.com/products/catalyst/linux.html") we can clearly read:
> **Q2:**                         [b]Which ATI graphics cards can use this driver? 
                        [/b]                                                                   **A2:** The ATI Proprietary Linux driver currently supports Radeon 8500 and later AGP or PCI Express graphics products, as well as FireGL 8700 and later products. We do not currently plan to include support for any products earlier than this. Drivers for earlier products should already be available from the [DRI                           Project]("http://dri.sf.net/") or [Utah-GLX                         project]("http://utah-glx.sf.net/").
So it seems I will have to go with the mach64 specific drivers from DRI as described on this thread:
[http://www.ubuntuforums.org/showthread.php?t=7200]("http://www.ubuntuforums.org/showthread.php?t=7200")

Anyone got the mach64 driver working for dual head?

---

