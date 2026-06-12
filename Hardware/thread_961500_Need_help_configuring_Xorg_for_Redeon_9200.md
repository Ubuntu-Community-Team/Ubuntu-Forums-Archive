---
title: "Need help configuring Xorg for Redeon 9200"
date: 2008-10-28
forum: Hardware
---

### Post by srkelley on 2008-10-28
I used the guide at [https://help.ubuntu.com/community/RadeonDriver#Configuring X.org](https://help.ubuntu.com/community/RadeonDriver#Configuring X.org) to configure my Radeon 9200. Problem is, I think my BusID for the card is wrong, which is why it didn't work when i did it. I changed it from 8 to 0 when i logged back in and had to use the integrated graphics via VESA.

I entered lcspi in the terminal

And received:

shirondale@shirondale-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
[B]01:08.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:08.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)[/B]
01:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
shirondale@shirondale-desktop:~$ 



The guide says that the number "01:08.1" is hexadecimal and that it needs to be converted before placing it in the xorg file by not having two numbers together (the 08). What would my number convert to, and have i made any other errors in my xorg.conf file?


Section "Device"
        Identifier      "Radeon 9200"
        Driver          "ati"
        BusID           "PCI:1:8:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Olevia"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Flat"
        Device          "Radeon 9200"
        Monitor         "Olevia"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1360x768" "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Flat"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
EndSection





haha, I misspelled Radeon in the title

---

### Post by srkelley on 2008-10-28
I've tried all of the combinations and still havn't gotten the driver to work. Is thre anything else I can do?

---

