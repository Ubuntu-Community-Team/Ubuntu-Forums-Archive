---
title: "Laptop Resolution Problem, Am I missing something?"
date: 2007-06-06
forum: Hardware &amp; Laptops
---

### Post by chris.hand on 2007-06-06
Hello Everyone,

I have recently installed Ubuntu on my Compaq Presario V5000 notebook computer. Everything is working beautifully, apart from my resolution is not the LCD's native resolution's of 1280x1024. Currently I can only select a maximum resolution of 1024 x 768 under System | Screen Resolution.

Here is the output of "lspci" from a terminal window:

chris@chris-laptop:~$ lspci00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)


Also, here is my current "xorg.conf" file (Just the important bits):


Section "Device"
      Identifier      "Generic Video Card"
      Driver            "i810"
      BusID            "PCI:0:2:0"
EndSection

Section "Monitor"
      Identifier      "Generic Monitor"
      Option            "DPMS"
      HorizSync      28-51
      VertRefresh      43-60
EndSection

Section "Screen"
      Identifier      "Default Screen"
      Device            "Generic Video Card"
      Monitor            "Generic Monitor"
      DefaultDepth      24
      SubSection "Display"
            Depth            1
            Modes            "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
      EndSubSection
      SubSection "Display"
            Depth            4
            Modes            "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
      EndSubSection
      SubSection "Display"
            Depth            8
            Modes            "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
      EndSubSection
      SubSection "Display"
            Depth            15
            Modes            "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
      EndSubSection
      SubSection "Display"
            Depth            16
            Modes            "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
      EndSubSection
      SubSection "Display"
            Depth            24
            Modes            "1280x800" "1280x1024" "1024x768" "800x600" "640x480"
      EndSubSection
EndSection

I have had a look around UbuntuForums.org, but cant seem to find the right answer yet. Also, its worth noting I am fairly new to Ubuntu/Linux so nice easy to follow instructions would be appreciated.

Thanks in advance, and also please let me know if you need any more information.

---

### Post by NeoLithium on 2007-06-06
Perhaps this will help you get you set up: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by chris.hand on 2007-06-07
Thanks Very Much! 

That did the trick and took me about 2 secs. :)

---

### Post by NeoLithium on 2007-06-07
You're very welcome :)

---

