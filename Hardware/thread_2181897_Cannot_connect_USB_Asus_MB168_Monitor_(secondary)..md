---
title: "Cannot connect USB Asus MB168 Monitor (secondary)."
date: 2013-10-19
forum: Hardware
---

### Post by shestero on 2013-10-19
The packets [COLOR=#000000][FONT=Ubuntu Beta]xserver-xorg-video-displaylink and fbdev are installed.
Monitor is just black.
No fb0, fb1 devices in /dev/.  I tried to create them using mknod, but their seems to be  no use and disapears after reboot.
My system is Ubuntu 10.04.
Here is xorg.conf :
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Beta]Section "ServerLayout"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier     "X.org Configured"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Screen      0  "Screen0" 0 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        InputDevice    "Mouse0" "CorePointer"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        InputDevice    "Keyboard0" "CoreKeyboard"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "InputDevice"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier  "Keyboard0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Driver      "kbd"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "InputDevice"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier  "Mouse0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Driver      "mouse"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option      "Protocol" "auto"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option      "Device" "/dev/input/mice"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Option      "ZAxisMapping" "4 5 6 7"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier   "Monitor0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        VendorName   "Monitor Vendor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        ModelName    "Monitor Model"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]# Primary (First/only) display[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Section "Device"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Identifier "Card0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Driver     "emgd"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    VendorName "Intel(R) DEG"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    BoardName  "Embedded Graphics"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    BusID      "0:2:0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Screen      0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    VideoRam   32768[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "PcfVersion"            "1792"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ConfigId"              "1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "SWCursor"              "true"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/name"                   "fit-PC2 "[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/General/PortOrder"      "20000"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/General/DisplayConfig"  "1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/General/DisplayDetect"  "1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/General/xVideo"         "1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/General/XVideoBlend"    "0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/General/DRI"            "1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/Port/2/General/name"           "DVI"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/Port/2/General/EdidAvail"      "2"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/Port/2/General/EdidNotAvail"   "1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/Port/2/General/Rotation"       "0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "ALL/1/Port/2/General/Edid"           "1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Option     "PortDrivers"           "sdvo"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Identifier "Screen0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Device     "Card0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Monitor    "Monitor0"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        DefaultDepth    24[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "DRI"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Group 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]        Mode 0666[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "Extensions"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Option   "Composite" "enable"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]


[COLOR=#000000][FONT=Ubuntu Beta]Section "ServerFlags"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Option "DontZap" "false"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Option "GlxVisuals" "all"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Option "IgnoreABI" "true"[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]#   Option "AutoAddDevices" "False"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]#   Option "AllowEmptyInput" "False"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "Files"                                                   [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   ModulePath  "/usr/lib/xorg/modules"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]#   ModulePath  "/usr/local/lib/xorg/modules"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "Device"                                                  [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]Identifier  "DisplayLinkDevice"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Driver      "displaylink"                [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   Option      "fbdev" "/dev/fb1"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "Monitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Identifier      "DisplayLinkMonitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]

[COLOR=#000000][FONT=Ubuntu Beta]Section "Screen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Identifier      "DisplayLinkScreen"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Device          "DisplayLinkDevice"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]    Monitor         "DisplayLinkMonitor"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   # SubSection "Display"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   #         Depth   24[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   #        Modes   "1280x1024"[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]   # EndSubSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Beta]EndSection[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Beta]
[/FONT][/COLOR]

---

### Post by shestero on 2013-10-21
I istalled Ubuntu 12.04. This system sees my monitor as an USB device (here is the except from dmesg output): 
[  108.964154] usb 1-3: new high-speed USB device number 4 using ehci-pci
[  109.097746] usb 1-3: New USB device found, idVendor=17e9, idProduct=ff03
[  109.097765] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  109.097779] usb 1-3: Product: MB168B
[  109.097791] usb 1-3: Manufacturer: DisplayLink
[  109.097802] usb 1-3: SerialNumber: D7LMTF******

Still no /dev/fb1 device appears!

---

### Post by VipHybs on 2013-11-17
Were you ever able to figure this out? I'm also having the same issue on 12.04 & 13.10.

---

### Post by gshafer on 2013-12-13
Anybody get this to work? It would be great for my headless server.

---

### Post by shestero on 2014-02-22
Still no solution anywhere. :-(

---

### Post by delbert2 on 2014-02-28
the MB168 came with a CD that includes a directory called /isolinux.

were you able to make any use of what was in there?

delbert

---

### Post by azedra on 2015-01-15
Hi [**[COLOR=#000000]delbert2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1908020"),

I bought "USB Asus MB168 Monitor" and as you said, i found directory called "isolinux" in the CD.

this directory contain the following files :

/media/al/Partition1/isolinux/:
total 21K
drwx------ 1 al al  472 oct.  23  2009 .
drwx------ 1 al al 4,0K janv. 15 00:29 ..
-rw------- 1 al al 2,0K avril 17  2007 boot.cat
drwx------ 1 al al  352 oct.  22  2009 data
-rw------- 1 al al  11K nov.  23  2009 isolinux.bin
-rw------- 1 al al  575 oct.  22  2009 isolinux.cfg
drwx------ 1 al al  424 oct.  23  2009 src

/media/al/Partition1/isolinux/data:
total 32M
drwx------ 1 al al 352 oct.  22  2009 .
drwx------ 1 al al 472 oct.  23  2009 ..
-rw------- 1 al al 32M oct.   8  2012 boot.ima
-rw------- 1 al al 170 nov.  23  2009 bootmsg.txt
-rw------- 1 al al 23K oct.   5  2009 memdisk

/media/al/Partition1/isolinux/src:
total 5,2M
drwx------ 1 al al  424 oct.  23  2009 .
drwx------ 1 al al  472 oct.  23  2009 ..
-rw------- 1 al al 549K oct.  22  2009 FDOEMCD.builder.zip
-rw------- 1 al al 2,9M oct.  22  2009 FDOEMCD.source-tools.zip
-rw------- 1 al al 1,9M oct.  22  2009 FDOEMCD.source.zip

so, can you explain me how can i use the content of the "isolinux" directory, to use my "USB Asus MB168 Monitor".

Thanks a lot.

---

