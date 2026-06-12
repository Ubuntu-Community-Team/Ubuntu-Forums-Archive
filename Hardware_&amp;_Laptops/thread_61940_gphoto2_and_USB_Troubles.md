---
title: "gphoto2 and USB Troubles"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by Parkotron on 2005-09-02
Hello,

I am trying to connect to my Sony DSC-P52 digital camera from my Kubuntu Hoary machine. I tried a few of the flashier GUIs, but none of them were able to find the camera. I therefore decided to try using the gphoto2 CLI on which most of them are based. But, no luck there either.

Basically I'm looking for any help, advice, experience anyone has to offer. I don't know what my problem is or where to go from here. Below is a log of any data I thought might be useful.

Before anyone asks:
 - Yes, the camera is turned on and in he proper mode.
 - Yes, the USB port works. My joystick works fine in the same port.
 - Yes, the camera is on the list of supported models.

Thanks for whatever help you can offer,

Parker

```
[SIZE=2][COLOR=Blue][19:41:46][/COLOR] [COLOR=Green]~ $[/COLOR] cat /proc/bus/usb/devices

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.10-5-amd64-k8 ehci_hcd
S:  Product=PCI device 10de:005b (nVidia Corporation)
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=10
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.10-5-amd64-k8 ohci_hcd
S:  Product=PCI device 10de:005a (nVidia Corporation)
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#=  8 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=054c ProdID=0010 Rev= 4.50
S:  Manufacturer=Sony
S:  Product=Sony DSC
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=ff Prot=01 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=255ms
[COLOR=Blue][19:42:17][/COLOR] [COLOR=Green]~ $[/COLOR] lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 008: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera
Bus 001 Device 001: ID 0000:0000
[COLOR=Blue][19:42:33][/COLOR] [COLOR=Green]~ $[/COLOR] gphoto2 --auto-detect
Model                          Port
----------------------------------------------------------
[COLOR=Blue][19:42:53][/COLOR] [COLOR=Green]~ $[/COLOR] gphoto2 --camera "Sony DSC-P52 (PTP mode)" --port usb: -L

*** Error ***
An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x54c, product 0x4e). Make sure this device is connected to the computer.
*** Error (-2: 'Bad parameters') ***

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --camera "Sony DSC-P52 (PTP mode)" --port "usb:" -L

Please make sure there is sufficient quoting around the arguments.[/SIZE]
```

---

### Post by Parkotron on 2005-09-13
I hate to be a jerk and bump my own thread, but

BUMP.

Someone out there must know something even kind of slighty related to this. I find it hard to believe that I should be completely stuck on a task as simple is grabbing photos form a digital camera.

---

### Post by jvictor on 2005-10-31
I'd similar issues. try using gtkam .. it worked for me. I'm not sure , y dotn u jst give ur camera as a USB PTP class camera... ? Just gussing.. worth a try though

---

### Post by David Haas on 2005-10-31
Parkotron--Most folks, including myself, use gThumb Image Viewer in "Applications." One connects the camera via USB, turns on the camera, and then opens gThumb. When this is first done, one needs to select his camera from the listing. Thereafter, gThumb recognizes the camera. Once recognized, select "File" in gThumb and then "Import Photos" to get the thumbnails. Then, select "Import" in the dialoque box to download all the thumbnails (the actual photos) into your Home directory. I hope this helps. 
David

---

