---
title: "Flickering screen on Lenovo 3000 N100"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by klaasvanschelven on 2007-07-05
I have a Lenovo 3000 N100 FPG laptop, bought it a few days ago. Ubuntu Feisty works pretty much out of the box except for the sound and this:

I keep having a ever so slightly flickering screen. This can be seen best on the orange standard background image, and only when the windows are in certain positions.

I've installed the xserver-xorg-video-intel package.

[FONT="Courier New"][SIZE="-2"]klaas@lenovo:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


[/SIZE][/FONT]Vista seems to have the same problem, but from a little searching newer drivers appear to be available.

thanks a lot,
regards,

Klaas

---

### Post by klaasvanschelven on 2007-07-05
Also I've looked here:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

but I'm not sure what to set the values to since I don't know what my monitor should be able to handle...

These are the relevant sections from /etc/X11/xorg.conf:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

---

### Post by klaasvanschelven on 2007-07-07
Ok, the problem persists, also with the latest drivers in Vista, so I'll do some talking with Lenovo first.

---

### Post by davisond on 2007-11-07
did you get anywhere with this?  I have a similar issue with gutsy on a 3000 N200.

---

### Post by molly_001 on 2007-11-07
It's an interesting problem, I have the 3000 N100 and with Ubuntu 6.06, 7.04 and 7.10 and never had this problem.  I have the 768EU model, this has Intel Calistoga chip graphics.  I understand there were other N100 models offered with an nVidia graphics solution, different from the Intel solution in mine.  So I wonder what you guys have in your N100?

---

### Post by davisond on 2007-11-07
my N200 has nvidia graphics.

---

### Post by molly_001 on 2007-11-08
... and here is a 3000 N200 with Intel graphics, and not nVidia, solution:
[http://www.buy.com/retail/product.asp?sku=205073866&adid=17654&dcaid=17653](http://www.buy.com/retail/product.asp?sku=205073866&adid=17654&dcaid=17653)

This was really dumb of Lenovo, to issue same model number, for both N100 and N200, and in each model you have different graphics adapters ... some N100s have Intel, some N100s have nvidia.  Dumb.

---

### Post by CazperII on 2007-11-18
I have a  Lenovo N200 with geforce go 7300 and I also experienced the screen flicker. It has something to do with the automatic detection of the resolution. I followed the instructions in this thread [http://ubuntuforums.org/showthread.php?t=398821&page=12](http://ubuntuforums.org/showthread.php?t=398821&page=12) and now the flicker is gone. 

What I did:

[LIST=1]
[*]Goto: System>Preferences>Advanced desktop settings (The compiz config settings manager)

[*]Click on General options>display settings

[*]Untick Detect Output

[*]Manually input your screen's resolution (1680x1050+0+0 for my LCD-panel)
[/LIST]

---

### Post by klaasvanschelven on 2008-05-06
Solved... I went to the service center and they put in a new screen for me... :-)

---

