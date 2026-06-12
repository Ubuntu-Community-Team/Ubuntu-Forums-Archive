---
title: "Ubuntu 9.04- Sound Issues (Used to work, and now it doesnt)"
date: 2009-08-05
forum: Hardware
---

### Post by nissandrift on 2009-08-05
I'm having issues with the sound on my computer... originally my sounds worked completely, but now I only have sound out of the headphone jack. I used all the OEM software originally, but ended up following this step-by-step guide to run all pulse audio [thats found here.]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html") After installing that I noticed that the sound keys on my laptop still showed that they changed the volume, but didnt have any effect in PulseAudio Volume Control. I fixed that already by changing the keyboard layout. While that bugged me the sound still came out of my speakers and headphone jack, but just recently the speakers randomly stopped working. Has anyone else experienced this? Anyone know how I can reinstall all the OEM sound?

Computer:
Lenovo 3000 N100 0768-4JU
Windows 7, and Ubuntu 9.04

steven@steven-laptop:~$ aplay --list-pcms   
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

steven@steven-laptop:~$ lspci -m
00:00.0 "Host bridge" "Intel Corporation" "Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub" -r03 "Lenovo" "Device 2061"
00:02.0 "VGA compatible controller" "Intel Corporation" "Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller" -r03 "Lenovo" "Device 2062"
00:02.1 "Display controller" "Intel Corporation" "Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller" -r03 "Lenovo" "Device 2062"
00:1b.0 "Audio device" "Intel Corporation" "82801G (ICH7 Family) High Definition Audio Controller" -r02 "Lenovo" "Device 2066"
00:1c.0 "PCI bridge" "Intel Corporation" "82801G (ICH7 Family) PCI Express Port 1" -r02 "" ""
00:1c.1 "PCI bridge" "Intel Corporation" "82801G (ICH7 Family) PCI Express Port 2" -r02 "" ""
00:1d.0 "USB Controller" "Intel Corporation" "82801G (ICH7 Family) USB UHCI Controller #1" -r02 "Lenovo" "Device 206b"
00:1d.1 "USB Controller" "Intel Corporation" "82801G (ICH7 Family) USB UHCI Controller #2" -r02 "Lenovo" "Device 206c"
00:1d.2 "USB Controller" "Intel Corporation" "82801G (ICH7 Family) USB UHCI Controller #3" -r02 "Lenovo" "Device 206d"
00:1d.3 "USB Controller" "Intel Corporation" "82801G (ICH7 Family) USB UHCI Controller #4" -r02 "Lenovo" "Device 206e"
00:1d.7 "USB Controller" "Intel Corporation" "82801G (ICH7 Family) USB2 EHCI Controller" -r02 -p20 "Lenovo" "Device 206f"
00:1e.0 "PCI bridge" "Intel Corporation" "82801 Mobile PCI Bridge" -re2 -p01 "" ""
00:1f.0 "ISA bridge" "Intel Corporation" "82801GBM (ICH7-M) LPC Interface Bridge" -r02 "Lenovo" "Device 2071"
00:1f.2 "IDE interface" "Intel Corporation" "82801GBM/GHM (ICH7 Family) SATA IDE Controller" -r02 -p80 "Lenovo" "Device 2072"
00:1f.3 "SMBus" "Intel Corporation" "82801G (ICH7 Family) SMBus Controller" -r02 "Lenovo" "Device 2073"
03:00.0 "Network controller" "Intel Corporation" "PRO/Wireless 3945ABG [Golan] Network Connection" -r02 "Intel Corporation" "Device 1010"
05:01.0 "Ethernet controller" "Realtek Semiconductor Co., Ltd." "RTL-8139/8139C/8139C+" -r10 "Lenovo" "Device 2074"
05:04.0 "CardBus bridge" "ENE Technology Inc" "CB1410 Cardbus Controller" -r01 "Lenovo" "Device 2075"
05:06.0 "FireWire (IEEE 1394)" "Ricoh Co Ltd" "R5C832 IEEE 1394 Controller" -p10 "Lenovo" "Device 2076"
05:06.1 "SD Host controller" "Ricoh Co Ltd" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter" -r19 "Lenovo" "Device 2077"
05:06.2 "System peripheral" "Ricoh Co Ltd" "R5C592 Memory Stick Bus Host Adapter" -r0a "Lenovo" "Device 2079"
05:06.3 "System peripheral" "Ricoh Co Ltd" "xD-Picture Card Controller" -r05 "Lenovo" "Device 207a"

---

### Post by nissandrift on 2009-08-06
Upgraded to Alsa 1.0.20 hoping that would help, but no luck... any suggestions?

---

### Post by harry2006 on 2009-08-06
seems to be some alsa issue, i guess..
did upgrading alsa helps?

---

### Post by nissandrift on 2009-08-06
It didn't seem to make any difference at all. I also checked my alsamixer in the terminal window, and every things bumped to full volume except the Mic boost. I'm not a Linux expert, and I really have no clue what to try next.

---

