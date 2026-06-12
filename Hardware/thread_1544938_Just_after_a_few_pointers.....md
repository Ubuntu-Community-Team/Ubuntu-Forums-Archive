---
title: "Just after a few pointers...."
date: 2010-08-03
forum: Hardware
---

### Post by 5BallJuggler on 2010-08-03
I'm trying to set up an "eGalaxTouch32" touchscreen.

I'm running Lucid 32bit on a Acer Aspire One

uname -r gives
```
2.6.32-24-generic
```

X -version gives
```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux phil-laptop 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=8d600575-15e5-438a-800a-232e34468d28 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

xinput list gives
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. Touch                       	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```

USB-devices gives
```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-24-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=62c0 Rev=01.00
S:  Manufacturer=Sonix Technology Co., Ltd.
S:  Product=USB 2.0 Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0a12 ProdID=0001 Rev=48.39
S:  Product=BT2.0
C:  #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-24-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

[B]T:  Bus=05 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0eef ProdID=0001 Rev=01.00
S:  Manufacturer=eGalax Inc.
S:  Product=Touch
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=44mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid[/B]

```

When I run "xinput test 13" i get this output, note it has 2 parameters. a[0]&a[1]
```
motion a[0]=2983 a[1]=3480 
motion a[0]=2988 a[1]=3478 
motion a[0]=2992 a[1]=3477 
motion a[0]=2997 a[1]=3476 
motion a[0]=3002 a[1]=3475 
motion a[0]=3007 a[1]=3474 
motion a[0]=3011 a[1]=3473 
motion a[0]=3018 a[1]=3470 
motion a[0]=3030 a[1]=3465 
motion a[0]=3044 a[1]=3458 
motion a[0]=3062 a[1]=3451 
motion a[0]=3087 a[1]=3444 
motion a[0]=3116 a[1]=3437 
motion a[0]=3151 a[1]=3431 
motion a[0]=3184 a[1]=3429 
motion a[0]=3211 a[1]=3429 
motion a[0]=3230 a[1]=3429 
motion a[0]=3239 a[1]=3427 
motion a[0]=3241 a[1]=3425 
motion a[0]=3242 a[1]=3425 
motion a[0]=3243 a[1]=3425 
motion a[0]=3242 a[1]=3425 
motion a[0]=3240 a[1]=3425 
```

When I run "xinput test 1" i get this output, note it has 4 parameters. a[0],a[1],a[2] & a[3]
```
motion a[0]=42 a[1]=42 a[2]=464 a[3]=1219 
motion a[0]=42 a[1]=42 a[2]=455 a[3]=1232 
motion a[0]=42 a[1]=42 a[2]=446 a[3]=1241 
motion a[0]=42 a[1]=42 a[2]=438 a[3]=1255 
motion a[0]=42 a[1]=42 a[2]=429 a[3]=1265 
motion a[0]=42 a[1]=42 a[2]=421 a[3]=1275 
motion a[0]=42 a[1]=42 a[2]=414 a[3]=1285 
button press   1 
motion a[0]=42 a[1]=42 a[2]=481 a[3]=974 
motion a[0]=42 a[1]=42 a[2]=486 a[3]=980 
motion a[0]=42 a[1]=42 a[2]=495 a[3]=990 
motion a[0]=42 a[1]=42 a[2]=510 a[3]=1004 
button press   1 

```

it looks like a[2] & a[3] are giving me the x, y position of the pointer, do I need to change this to a[0] & a[1]

if so how???

any help greatly appreciated.

please note, I have tried to set up using eGalaxTouch32 drivers, but I'm not advanced enough to do myself, I have borked the system twice by trying.

Phil

---

### Post by 5BallJuggler on 2010-08-03
just as an aside, if I use the --long parameter it says that a[3] & a[4] are z and rot respectively
.....that can't be right
.....can it?

xinput list --long 10
```

eGalax Inc. Touch                       	id=10	[slave  pointer  (2)]
	Reporting 5 classes:
		Class originated from: 10
		Buttons supported: 5
		Button labels: Button Left Button Unknown Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 10
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 42.000000 - 1981.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 42.000000
		Class originated from: 10
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 42.000000 - 1981.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 42.000000
		Class originated from: 10
		Detail for Valuator 2:
		  Label: Abs Z
		  Range: 0.000000 - 2047.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 178.000000
		Class originated from: 10
		Detail for Valuator 3:
		  Label: Abs Rotary X
		  Range: 0.000000 - 2047.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 1702.000000


```

---

### Post by 5BallJuggler on 2010-08-04
Bump.....Sorry

---

### Post by 5BallJuggler on 2010-08-05
Shameless Bump!

---

