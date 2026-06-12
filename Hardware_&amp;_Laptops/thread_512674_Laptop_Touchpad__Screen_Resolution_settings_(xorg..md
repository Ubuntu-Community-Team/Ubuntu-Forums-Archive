---
title: "Laptop Touchpad / Screen Resolution settings (xorg.conf)"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by ugm6hr on 2007-07-29
I have seen a lot of threads posted for help getting laptop screen resolution settings and touchpad settings sorted.  I thought it might be helpful to keep a record of fully functional xorg.conf for various laptops in one place (please attach as .txt files to your post with output from *lspci -nn* - feel free to reply to my template below).  

Perhaps links to other solutions to get various components working on the laptop could be included too.

For beginners - this is useful if you own a laptop ***identical*** to one posted here, in order to get the screen working at resolution(s) stated, with touchpad working with functions as described - just apply the attached xorg file.
[B]
How to apply a downloaded xorg config file:[/B]
Download to your /home/*user* directory
Make a backup of your original xorg.conf (in case there is a problem later)
```
sudo cp xorg.conf xorgbackup.conf
```
Open the downloaded xorg.txt file (double click)
Select all, and then Copy
```
gksudo gedit /etc/X11/xorg.conf
```
(PS: use *mousepad* instead of *gedit* for Xubuntu)
Delete everything here, and then Paste.
Save

I will try and keep a Contents Page here. I hope this is useful for people.

**Contents**
Acer Aspire 5051AWXMi [http://ubuntuforums.org/showpost.php?p=3100932&postcount=3](http://ubuntuforums.org/showpost.php?p=3100932&postcount=3)
Averatec 2300 / 2370 [http://ubuntuforums.org/showthread.php?t=308152](http://ubuntuforums.org/showthread.php?t=308152)
Dell Inspiron 1501 [http://ubuntuforums.org/showpost.php?p=3191485&postcount=9](http://ubuntuforums.org/showpost.php?p=3191485&postcount=9)
Dell Inspiron 4000 [http://ubuntuforums.org/showpost.php?p=3134890&postcount=6](http://ubuntuforums.org/showpost.php?p=3134890&postcount=6)
Dell Inspiron 4150 (3D enabled) [http://ubuntuforums.org/showpost.php?p=3134126&postcount=5](http://ubuntuforums.org/showpost.php?p=3134126&postcount=5)
Dell Inspiron 5000e [http://ubuntuforums.org/showpost.php?p=3131272&postcount=4](http://ubuntuforums.org/showpost.php?p=3131272&postcount=4)
Dell Precision M70 [http://ubuntuforums.org/showpost.php?p=3174491&postcount=8](http://ubuntuforums.org/showpost.php?p=3174491&postcount=8)

**Other laptop-specific links that might be helpful**
Acer Aspire 4920 [http://ubuntuforums.org/showthread.php?t=494467](http://ubuntuforums.org/showthread.php?t=494467)
Acer Travelmate 4600 [http://ubuntuforums.org/showpost.php?p=3160128&postcount=7](http://ubuntuforums.org/showpost.php?p=3160128&postcount=7)
Amilo M7400 [http://ubuntuforums.org/showthread.php?t=189540](http://ubuntuforums.org/showthread.php?t=189540)
HP dv9000 / dv9500 [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
HP/Compaq NC4000 [http://ubuntuforums.org/showthread.php?t=52223](http://ubuntuforums.org/showthread.php?t=52223)
Sony Vaio VGN-FE41Z [http://ubuntuforums.org/showthread.php?t=465491](http://ubuntuforums.org/showthread.php?t=465491)

Other useful links:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad) [http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide](http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide) (Full how-tos for Touchpads)
[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL) (look under laptops for hardware support details)
[https://wiki.ubuntu.com/LaptopTestingTeam/](https://wiki.ubuntu.com/LaptopTestingTeam/) (Laptop Testing Team entries)

---

### Post by ugm6hr on 2007-07-29
**Laptop Model**

**Ubuntu version:**
Dapper Edgy Feisty

**lspci -nn**

**Screen Resolution(s):** 
1280x768 1024x768 800x600

**3D Accelerated graphics:**
Direct rendering: Yes No
glxgears fps:

**Touchpad:**
Tap-to-click: On Off
Vertical Scroll: On Off
Horizontal Scroll: On Off

**Ethernet: **
Out-of-the-box Fixed Not yet
[B]
Wifi: [/B]
Out-of-the-box Fixed Not yet

**Card Reader: **
Out-of-the-box Fixed Not yet

**Other useful info:**

---

### Post by ugm6hr on 2007-07-29
**Acer Aspire 5051AWXMi**

**Ubuntu Version:**
Xubuntu7.04 / Feisty

**lspci -nn**
```
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a39]
00:12.0 IDE interface [0101]: ATI Technologies Inc ATI 4379 Serial ATA Controller [1002:4379] (rev 80)
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 83)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
08:01.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
08:01.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
08:01.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01)
08:01.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
08:01.4 FLASH memory [0501]: ENE Technology Inc Unknown device [1524:0551] (rev 01)
08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
08:04.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5005G 802.11abg NIC [168c:001a] (rev 01)
```

**Screen Resolution(s):** 
1280x768 1024x768 800x600

**Touchpad:**
Tap-to-click: On 
Vertical Scroll: On 
Horizontal Scroll: Off

**Ethernet: **
Out-of-the-box
[B]
Wifi: [/B]
Fixed with Wicd

**Card Reader: **
Not yet

**Other useful info:**
Sound / Microphone: [http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515) [http://ubuntuforums.org/showthread.php?t=457011](http://ubuntuforums.org/showthread.php?t=457011)
Wifi: [http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)
Suspend: [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by ugm6hr on 2007-08-04
**Laptop Model**
Dell Inspiron 5000e (with 1400x1050 screen)

**Ubuntu version:**
Xubuntu7.04/ Feisty

**lspci -nn**
```
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:04.0 CardBus bridge [0607]: Texas Instruments PCI1225 [104c:ac1c] (rev 01)
00:04.1 CardBus bridge [0607]: Texas Instruments PCI1225 [104c:ac1c] (rev 01)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1978 Maestro 2E [125d:1978] (rev 10)
00:10.0 Communication controller [0780]: Agere Systems WinModem 56k [11c1:0448] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M3 AGP 2x [1002:4c46] (rev 02)

```

**Screen Resolution(s):** 
1400x1050

**Touchpad:**
Tap-to-click: On 
Vertical Scroll: On 
Horizontal Scroll: Off 

**Other useful info:**
Install initially with Safe Graphics mode (Vesa) - otherwise you get a distorted screen.

---

### Post by Xomphos on 2007-08-04
**Ubuntu version:**
Feisty 7.04

**lspci -nn**

> 00:00.0 Host bridge [0600]: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB (Hub #1) [8086:2482] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
02:01.1 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
07:00.0 Network controller [0280]: Broadcom Corporation BCM43xG 802.11b/g [14e4:4325] (rev 02)


**Screen Resolution(s):** 
1400x1050

**Touchpad:**
Tap-to-click: On Off
Vertical Scroll: On Off
Horizontal Scroll: On Off

**Ethernet: **
Out-of-the-box
[B]
Wifi: [/B]
Fixed - MN-720 Microsoft card-used broadcom drivers

**Card Reader: **
N/A

---

### Post by nc_jed on 2007-08-04
**Laptop Model**
Dell Inspiron 4000

**Ubuntu version:**
Xubuntu Feisty (07.04)

**lspci -nn**
```
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:03.0 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
00:03.1 CardBus bridge [0607]: Texas Instruments PCI1420 [104c:ac51]
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:08.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M3 AGP 2x [1002:4c46] (rev 02)
06:00.0 Network controller [0280]: RaLink Ralink RT2600 802.11 MIMO [1814:0401]

```

**Screen Resolution(s):** 
1024x768 800x600 640x480

**Touchpad:**
Tap-to-click: On
Vertical Scroll: On
Horizontal Scroll: On

**Ethernet: **
Unsure -- using Wifi PCMCIA

**Modem: **
Unsure -- using Wifi PCMCIA

**Wifi: **
LiveCD-
Out of the box

Disk Install-
Fixed. Ralink chip set  PCMCIA card.  Fixed with this thread.  [http://ubuntuforums.org/showthread.php?t=162008](http://ubuntuforums.org/showthread.php?t=162008)

**Card Reader: **
N/A

**Other useful info:**
- ATI Graphics Card defaulted to 800x600.  Too old for the generic ATI/Radeon driver.  Fixed with this thread.  [http://ubuntuforums.org/showthread.php?t=495256](http://ubuntuforums.org/showthread.php?t=495256)

- Suspend/Resume worked out of the box.

- Installed with alternate install disk (text mode).  'Install to Harddisk' icon in LiveCD did not complete successfully.

---

### Post by davycork on 2007-08-09
I am a newbie and had a need to disable the touchpad as it was far too sensitive.

To disable the touchpad in this laptop, I did the following:

su
[type your root password]
cd /etc/X11
cp xorg.conf xorg_backup
nano xorg.conf

I then inserted the Synaptics touchpad section below the "mouse" section. The key here is to have the

Option     "Core Pointer"

directive, as this tells this section to override the "mouse" section.

My version of the file is attached below. Good luck!

---

### Post by porcorosso on 2007-08-11
Laptop Model:
Dell Precision M70

Ubuntu version:
Feisty

lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV41 [Quadro FX Go1400] [10de:00cc] (rev a2)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

```

Screen Resolution(s):
1680x1050 on external LCD (DVI, used when docked) / 1920x1200 on integrated LCD (used when undocked)

3D Accelerated graphics:
Direct rendering: No
glxgears fps:

Touchpad:
Tap-to-click: Off
Vertical Scroll: Off
Horizontal Scroll: Off

Ethernet:
Out-of-the-box

Wifi:
Out-of-the-box

Card Reader:
Haven't Checked / Not Interested

Other useful info:
I have tried 6 different methods of installing the binary driver for the video subsystem -- always on clean Ubuntu installations so that no possible effect from previous attempts interferes with the current effort. All of them work -- until I change the docking status of the computer. At that point I lose one monitor or the other. At that point I try altering the configuration through nvidia-settings or through direct editing of xorg.conf and then lose Xserver. I have, so far, been able to restore Xserver only by reverting to the original driver and the original xorg.conf. The xorg.conf I have posted is the original xorg.conf file altered ONLY by the addition of the option in the Synaptics section which turns off tapping and scrolling on my ALPS touchpad. It's the only way to make the danged thing useable.

---

### Post by Paul133 on 2007-08-14
**Laptop Model:**
Dell Inspiron 1501
[B]
Ubuntu version:[/B]
Ubuntu (Gnome) 7.04 Feisty

**lspci -nn**
```

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SB600 SMBus [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SB600 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SB600 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)

```
[B]
Screen Resolution(s):[/B]
1280x800 (main), 1280x768, 1024x768, 800x600, 640x480
[B]
3D Accelerated graphics:[/B] Yes, with the restricted driver
Direct rendering: Yes (I think)
glxgears fps: 1738.921 FPS (I took the highest of 5 if it matters)
[B]
Touchpad:[/B]
**Tap-to-click:** On
**Vertical Scroll:** On 
**Horizontal Scroll:** Off

**Ethernet:**
Out-of-the-box

**Wifi:**
Fixed (ndiswrapper, see below for the tutorial)

**Card Reader:**
Not tested

**Other useful info:**
I am running XGL/Compiz Fusion with the restricted driver; the tutorial I followed is here:
[http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html)

I got my WiFi working with ndiswrapper; tutorial here:
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

If you have this laptop, just go to that blog; the guy that runs it (redDEAD) has just about everything on this laptop working.

---

