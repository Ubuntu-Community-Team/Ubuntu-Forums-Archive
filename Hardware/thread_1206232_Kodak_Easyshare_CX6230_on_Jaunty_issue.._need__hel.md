---
title: "Kodak Easyshare CX6230 on Jaunty issue.. need  help please.."
date: 2009-07-06
forum: Hardware
---

### Post by killer_d76 on 2009-07-06
I have this old camera that has been working fine on F-Spot on Ubuntu Hardy Heron.. but since i upgraded to Ibex and Jaunty my laptop now can't detect/connect my camera!.. need help here.. thanks! ;)

---

### Post by tommcd on 2009-07-07
Try installing **gphoto2** from the Ubuntu repos if you don't already have it installed. It is not installed by default, as it is not present in the Ubuntu 9.04 on my laptop.
Then plug in the camera and open a terminal and run:
```
gphoto2 --auto-detect
```
and see if it detects the camera. If it does then run:
```
gphoto2 -P
```
This will download the camera's photos to the directory your terminal is in. By default, the terminal open to your home directory.
Also. open a terminal and run: **lsusb** to see if the camera is detected as a usb device.

If this doesn't work I'm not sure what else you could try.

---

### Post by killer_d76 on 2009-07-07
thanks for the quick reply tommcd, i installed gphoto and run the codes that you have provided but i got this error!.. hope you can help me fix this issue for me!.. thanks again! ;)

[PHP]arvin@arvin-laptop:~$ gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
Kodak CX6230                   usb:            
Kodak CX6230                   usb:004,002     
arvin@arvin-laptop:~$ gphoto2 -P
                                                                               
*** Error ***              
PTP I/O error

*** Error ***              
An error occurred in the io-library ('Unspecified error'): No error description available
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt -P

Please make sure there is sufficient quoting around the arguments.

arvin@arvin-laptop:~$ 

[/PHP]

---

### Post by tommcd on 2009-07-07
That was unexpected...
Your output from **gphoto2 --auto-detect** indicates that it correctly detects your camera as Kodak CX6230.
But your output from **gphoto2 -P** gives the rather unenlightening "unspecified error" message.

If gphoto2 correctly detects your camera, I don't know why it can't import the photos from the camera. Normally if the camera is detected, the photos will download without a problem.
 A reference from the Arch linux forums suggests that it may be a kernel bug:
[http://bbs.archlinux.org/viewtopic.php?id=62509](http://bbs.archlinux.org/viewtopic.php?id=62509)
This page from the ghoto2 website claims that your camera is supported:
[http://gphoto.org/proj/libgphoto2/support.php](http://gphoto.org/proj/libgphoto2/support.php)
While this may be of academic interest, it does not solve your problem.
Try running the command with the debug option as the output suggests:
```

gphoto2 --auto-detect
gphoto2 -debug -P

```

---

### Post by killer_d76 on 2009-07-07
thanks tommcd here's the result of the code that you have provided, though i added an additional "-" on the "-debug" part of the code,

[PHP]arvin@arvin-laptop:~$ gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
Kodak CX6230                   usb:            
Kodak CX6230                   usb:004,003 [/PHP]



[PHP]
20). Make sure this device is connected to the computer.
0.681071 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.681084 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4100). Make sure this device is connected to the computer.
0.681097 gphoto2-port(0): Could not find USB device (vendor 0x3e8, product 0x2182). Make sure this device is connected to the computer.
0.681110 gphoto2-port(0): Could not find USB device (vendor 0x3e8, product 0x2180). Make sure this device is connected to the computer.
0.681123 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.681136 gphoto2-port(0): Could not find USB device (vendor 0xe21, product 0x751). Make sure this device is connected to the computer.
0.681149 gphoto2-port(0): Could not find USB device (vendor 0xe21, product 0x801). Make sure this device is connected to the computer.
0.681163 gphoto2-port(0): Could not find USB device (vendor 0xe21, product 0x701). Make sure this device is connected to the computer.
0.681176 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4007). Make sure this device is connected to the computer.
0.681189 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x400a). Make sure this device is connected to the computer.
0.681202 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4012). Make sure this device is connected to the computer.
0.681215 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x400b). Make sure this device is connected to the computer.
0.681228 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4013). Make sure this device is connected to the computer.
0.681241 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4123). Make sure this device is connected to the computer.
0.681254 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4157). Make sure this device is connected to the computer.
0.681267 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4130). Make sure this device is connected to the computer.
0.681280 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x413c). Make sure this device is connected to the computer.
0.681305 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4137). Make sure this device is connected to the computer.
0.681319 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x413d). Make sure this device is connected to the computer.
0.681332 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4131). Make sure this device is connected to the computer.
0.681345 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4150). Make sure this device is connected to the computer.
0.681358 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4158). Make sure this device is connected to the computer.
0.681372 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4152). Make sure this device is connected to the computer.
0.681385 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x411f). Make sure this device is connected to the computer.
0.681398 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4153). Make sure this device is connected to the computer.
0.681411 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x413e). Make sure this device is connected to the computer.
0.681424 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4151). Make sure this device is connected to the computer.
0.681438 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4128). Make sure this device is connected to the computer.
0.681451 gphoto2-port(0): Could not find USB device (vendor 0x84d, product 0x3). Make sure this device is connected to the computer.
0.681464 gphoto2-port(0): Could not find USB device (vendor 0xd64, product 0x1021). Make sure this device is connected to the computer.
0.681477 gphoto2-port(0): Could not find USB device (vendor 0x3e8, product 0x2130). Make sure this device is connected to the computer.
0.681491 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x905c). Make sure this device is connected to the computer.
0.681504 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.681517 gphoto2-port(0): Could not find USB device (vendor 0xc45, product 0x8000). Make sure this device is connected to the computer.
0.681530 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x4132). Make sure this device is connected to the computer.
0.681543 gphoto2-port(0): Could not find USB device (vendor 0x41e, product 0x412f). Make sure this device is connected to the computer.
0.681557 gphoto2-port(0): Could not find USB device (vendor 0x413c, product 0x4500). Make sure this device is connected to the computer.
0.681570 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x905c). Make sure this device is connected to the computer.
0.681583 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.681597 gphoto2-port(0): Could not find USB device (vendor 0x5da, product 0x1018). Make sure this device is connected to the computer.
0.681610 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.681623 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.681643 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.681657 gphoto2-port(0): Could not find USB device (vendor 0x1183, product 0x1). Make sure this device is connected to the computer.
0.681671 gphoto2-port(0): Could not find USB device (vendor 0x5da, product 0x1020). Make sure this device is connected to the computer.
0.681684 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.681697 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.702459 gphoto2-port(0): Could not find USB device (vendor 0xaa6, product 0x6021). Make sure this device is connected to the computer.
0.702478 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9050). Make sure this device is connected to the computer.
0.702492 gphoto2-port(0): Could not find USB device (vendor 0x10d6, product 0x2200). Make sure this device is connected to the computer.
0.702505 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.702519 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10f). Make sure this device is connected to the computer.
0.702532 gphoto2-port(0): Could not find USB device (vendor 0x4b8, product 0x403). Make sure this device is connected to the computer.
0.702546 gphoto2-port(0): Could not find USB device (vendor 0x4b8, product 0x402). Make sure this device is connected to the computer.
0.702560 gphoto2-port(0): Could not find USB device (vendor 0x6d3, product 0x21ba). Make sure this device is connected to the computer.
0.702573 gphoto2-port(0): Could not find USB device (vendor 0x4c5, product 0x1140). Make sure this device is connected to the computer.
0.702586 gphoto2-port(0): Could not find USB device (vendor 0xdca, product 0x2). Make sure this device is connected to the computer.
0.702600 gphoto2-port(0): Could not find USB device (vendor 0xdca, product 0x2). Make sure this device is connected to the computer.
0.702613 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x14a). Make sure this device is connected to the computer.
0.702627 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1d2). Make sure this device is connected to the computer.
0.702640 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1c6). Make sure this device is connected to the computer.
0.702653 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x193). Make sure this device is connected to the computer.
0.702666 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1c0). Make sure this device is connected to the computer.
0.702679 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x19b). Make sure this device is connected to the computer.
0.702692 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1c1). Make sure this device is connected to the computer.
0.702706 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1c5). Make sure this device is connected to the computer.
0.702719 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1d4). Make sure this device is connected to the computer.
0.702732 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1db). Make sure this device is connected to the computer.
0.702745 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1c4). Make sure this device is connected to the computer.
0.702758 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1bf). Make sure this device is connected to the computer.
0.702772 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x142). Make sure this device is connected to the computer.
0.702785 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x18f). Make sure this device is connected to the computer.
0.702798 gphoto2-port(0): Could not find USB device (vendor 0x4cb, product 0x1d8). Make sure this device is connected to the computer.
0.702811 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.702825 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.702838 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.702852 gphoto2-port(0): Could not find USB device (vendor 0x919, product 0x100). Make sure this device is connected to the computer.
0.702878 gphoto2-port(0): Could not find USB device (vendor 0x458, product 0x7005). Make sure this device is connected to the computer.
0.702892 gphoto2-port(0): Could not find USB device (vendor 0x797, product 0x801c). Make sure this device is connected to the computer.
0.702905 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.702918 gphoto2-port(0): Could not find USB device (vendor 0x1302, product 0x1016). Make sure this device is connected to the computer.
0.702932 gphoto2-port(0): Could not find USB device (vendor 0x1302, product 0x1017). Make sure this device is connected to the computer.
0.702945 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.702958 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.702972 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6502). Make sure this device is connected to the computer.
0.702985 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6202). Make sure this device is connected to the computer.
0.702998 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7c02). Make sure this device is connected to the computer.
0.703011 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7d02). Make sure this device is connected to the computer.
0.703039 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6302). Make sure this device is connected to the computer.
0.703055 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6602). Make sure this device is connected to the computer.
0.703068 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7402). Make sure this device is connected to the computer.
0.703081 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7802). Make sure this device is connected to the computer.
0.703095 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7202). Make sure this device is connected to the computer.
0.703108 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6e02). Make sure this device is connected to the computer.
0.703121 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7902). Make sure this device is connected to the computer.
0.703134 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6d02). Make sure this device is connected to the computer.
0.703148 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6302). Make sure this device is connected to the computer.
0.703161 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4102). Make sure this device is connected to the computer.
0.703174 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6802). Make sure this device is connected to the computer.
0.703187 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7102). Make sure this device is connected to the computer.
0.703201 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6b02). Make sure this device is connected to the computer.
0.703214 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6402). Make sure this device is connected to the computer.
0.703227 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7602). Make sure this device is connected to the computer.
0.703240 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6702). Make sure this device is connected to the computer.
0.703254 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6c02). Make sure this device is connected to the computer.
0.703267 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6a02). Make sure this device is connected to the computer.
0.703280 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4202). Make sure this device is connected to the computer.
0.710123 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7702). Make sure this device is connected to the computer.
0.710142 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7e02). Make sure this device is connected to the computer.
0.710156 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4302). Make sure this device is connected to the computer.
0.710169 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4102). Make sure this device is connected to the computer.
0.710182 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4402). Make sure this device is connected to the computer.
0.710196 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4502). Make sure this device is connected to the computer.
0.710209 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4102). Make sure this device is connected to the computer.
0.710223 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x6002). Make sure this device is connected to the computer.
0.710236 gphoto2-port(0): Could not find USB device (vendor 0xf003, product 0x6002). Make sure this device is connected to the computer.
0.710249 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8b02). Make sure this device is connected to the computer.
0.710262 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8c02). Make sure this device is connected to the computer.
0.710275 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7502). Make sure this device is connected to the computer.
0.710288 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7b02). Make sure this device is connected to the computer.
0.710302 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7302). Make sure this device is connected to the computer.
0.710315 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x4002). Make sure this device is connected to the computer.
0.710328 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x7a02). Make sure this device is connected to the computer.
0.710341 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8002). Make sure this device is connected to the computer.
0.710354 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8102). Make sure this device is connected to the computer.
0.710367 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8202). Make sure this device is connected to the computer.
0.710380 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x9b02). Make sure this device is connected to the computer.
0.710393 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8402). Make sure this device is connected to the computer.
0.710406 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8502). Make sure this device is connected to the computer.
0.710419 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x9602). Make sure this device is connected to the computer.
0.710432 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x9702). Make sure this device is connected to the computer.
0.710445 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8702). Make sure this device is connected to the computer.
0.710459 gphoto2-port(0): Could not find USB device (vendor 0x3f0, product 0x8802). Make sure this device is connected to the computer.
0.710472 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9153). Make sure this device is connected to the computer.
0.710485 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.710498 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10e). Make sure this device is connected to the computer.
0.710511 gphoto2-port(0): Could not find USB device (vendor 0x19ff, product 0x303). Make sure this device is connected to the computer.
0.710536 gphoto2-port(0): Could not find USB device (vendor 0x19ff, product 0x309). Make sure this device is connected to the computer.
0.710550 gphoto2-port(0): Could not find USB device (vendor 0x19ff, product 0x307). Make sure this device is connected to the computer.
0.710563 gphoto2-port(0): Could not find USB device (vendor 0x45e, product 0xc9). Make sure this device is connected to the computer.
0.710577 gphoto2-port(0): Could not find USB device (vendor 0x8086, product 0x630). Make sure this device is connected to the computer.
0.710590 gphoto2-port(0): Could not find USB device (vendor 0x553, product 0x202). Make sure this device is connected to the computer.
0.710604 gphoto2-port(0): Could not find USB device (vendor 0x93a, product 0x10f). Make sure this device is connected to the computer.
0.710617 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x112a). Make sure this device is connected to the computer.
0.710630 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1126). Make sure this device is connected to the computer.
0.710643 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x2102). Make sure this device is connected to the computer.
0.710656 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x2101). Make sure this device is connected to the computer.
0.710669 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1008). Make sure this device is connected to the computer.
0.710682 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1122). Make sure this device is connected to the computer.
0.710696 gphoto2-port(0): Could not find USB device (vendor 0x1006, product 0x4002). Make sure this device is connected to the computer.
0.710709 gphoto2-port(0): Could not find USB device (vendor 0x1006, product 0x4003). Make sure this device is connected to the computer.
0.710722 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1113). Make sure this device is connected to the computer.
0.710735 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1120). Make sure this device is connected to the computer.
0.710748 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1117). Make sure this device is connected to the computer.
0.710761 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1115). Make sure this device is connected to the computer.
0.710774 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1118). Make sure this device is connected to the computer.
0.710788 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1114). Make sure this device is connected to the computer.
0.710801 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1119). Make sure this device is connected to the computer.
0.710814 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1134). Make sure this device is connected to the computer.
0.710827 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1116). Make sure this device is connected to the computer.
0.710840 gphoto2-port(0): Could not find USB device (vendor 0x4102, product 0x1132). Make sure this device is connected to the computer.
0.710853 gphoto2-port(0): Could not find USB device (vendor 0xb20, product 0xddee). Make sure this device is connected to the computer.
0.710866 gphoto2-port(0): Could not find USB device (vendor 0x784, product 0x100). Make sure this device is connected to the computer.
0.710879 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x905c). Make sure this device is connected to the computer.
0.710893 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x3300). Make sure this device is connected to the computer.
0.710906 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x4100). Make sure this device is connected to the computer.
0.710920 gphoto2-port(0): Could not find USB device (vendor 0x5da, product 0x1006). Make sure this device is connected to the computer.
0.732208 gphoto2-port(0): Could not find USB device (vendor 0xd96, product 0x0). Make sure this device is connected to the computer.
0.732226 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer.
0.732240 gphoto2-port(0): Could not find USB device (vendor 0x4f1, product 0x6105). Make sure this device is connected to the computer.
0.732254 gphoto2-port(0): Could not find USB device (vendor 0x84e, product 0x1). Make sure this device is connected to the computer.
0.732267 gphoto2-port(0): Could not find USB device (vendor 0xb28, product 0x100c). Make sure this device is connected to the computer.
0.732280 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x57e). Make sure this device is connected to the computer.
0.732294 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58a). Make sure this device is connected to the computer.
0.732307 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58c). Make sure this device is connected to the computer.
0.732320 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x58d). Make sure this device is connected to the computer.
0.732334 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x589). Make sure this device is connected to the computer.
0.732347 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5aa). Make sure this device is connected to the computer.
0.732360 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x59a). Make sure this device is connected to the computer.
0.732374 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5a2). Make sure this device is connected to the computer.
0.732387 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5b7). Make sure this device is connected to the computer.
0.732400 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5ba). Make sure this device is connected to the computer.
0.732413 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5a7). Make sure this device is connected to the computer.
0.732427 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5af). Make sure this device is connected to the computer.
0.732440 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5ae). Make sure this device is connected to the computer.
0.732453 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x5a9). Make sure this device is connected to the computer.
0.732466 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x59c). Make sure this device is connected to the computer.
0.732479 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x560). Make sure this device is connected to the computer.
0.732493 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x560). Make sure this device is connected to the computer.
0.732506 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x535). Make sure this device is connected to the computer.
0.732519 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x566). Make sure this device is connected to the computer.
0.732532 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x566). Make sure this device is connected to the computer.
0.732546 gphoto2-port(0): Could not find USB device (vendor 0x40a, product 0x574). Make sure this device is connected to the computer.
0.732553 gphoto2-port-usb(1): Looking for USB device (vendor 0x40a, product 0x573)... found.
0.732562 gphoto2-port-usb(2): inep to look for is 83
0.732569 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 83, outep 04, intep 85, class 06, subclass 01
0.732580 gphoto2-abilities-list.c(2): Found 'Kodak CX6230' (0x40a,0x573)
0.732601 gphoto2-port(2): Freeing port...
0.732611 gphoto2-port(2): Closing port...
0.732769 gphoto2-camera(2): Setting abilities ('Kodak CX6230')...
0.732783 gphoto2-setting(2): Setting key 'model' to value 'Kodak CX6230' (gphoto2)
0.732795 gphoto2-setting(2): Saving 2 setting(s) to file "/home/arvin/.gphoto/settings"
0.732965 gphoto2-port-info-list(2): Looking for path 'usb:' (13 entries available)...
0.732986 gphoto2-port-info-list(2): Getting info of entry 6 (13 available)...
0.732997 gphoto2-camera(2): Setting port info for port 'Universal Serial Bus' at[/PHP]

---

### Post by tommcd on 2009-07-08
Is that all of the output with the debug option? The last line:
> 0.732997 gphoto2-camera(2): Setting port info for port 'Universal Serial Bus' at  
looks like it should have something after the word "at".

Anyway, it looks like gphoto2 is having problems finding your camera, as evidenced by all the 
> 0.681071 gphoto2-port(0): Could not find USB device (vendor 0x2770, product 0x9120). Make sure this device is connected to the computer. 
messages. Is the camera detected as a usb device if you run **lsusb** from the terminal after plugging in the camera?
Have you tried plugging the camera into different usb ports?
 The fact that Ubuntu properly detects your camera, but can not seem to download the photos is a bit of a mystery.
Try running gphoto2 with these options:
```

gphoto2 --auto-detect
gphoto2 --get-all-raw-data

```
reference:[http://www.linuxcompatible.org/thread30236-1.html](http://www.linuxcompatible.org/thread30236-1.html)
If that don't work, then try:
```

gphoto2 --auto-detect
gphoto2 --P --camera="Kodak CX6230"

```
reference:[http://fixunix.com/ubuntu/330484-gphoto2-first-look.html](http://fixunix.com/ubuntu/330484-gphoto2-first-look.html)
Report back if any of this helps. I'm about out of ideas on this one.

---

### Post by squee on 2009-07-08
I'm actually getting similar problems with my mp3 player, Trekstor Vibez. I dont even know why the file system is gphoto2...

Really frustrating me that it's not working.

---

### Post by killer_d76 on 2009-07-09
thanks so much tommcd for the reply, i will try all your suggestion later, i'll keep you posted!.. :)

---

### Post by xinilux on 2009-08-26
Bump

I also have a CX6230 and had the same error messages as the OP. (I am running Intrepid.) Google-ing found this

[http://www.linuxquestions.org/questions/slackware-14/digital-camera-problems-on-slackware-current-486973/]("http://www.linuxquestions.org/questions/slackware-14/digital-camera-problems-on-slackware-current-486973/")

Scroll down about halfway to TSquaredF's post for the general instructions which can be modified for use with the Kodak CX6230. In particular, you may want to run the command

/usr/lib/libgphoto2/print-camera-list udev-rules mode 0660 > camera.rules

instead of what TSquaredF uses. You will need to have the package libgphoto2-2 installed to run this command.
The post is a bit old but I found it helpful in resolving the issue.

---

### Post by killer_d76 on 2009-10-15
thanks xinilux, this can be very helpful to all the other kodak cx6230 owners out there because even on the new ubuntu 9.10 i am still getting the same error and can't seem to get this camera working :(

---

