---
title: "Tablet xinput persist"
date: 2017-11-08
forum: Hardware
---

### Post by m-knichel on 2017-11-08
I have an Epson interactive projector.  I also run with 3 monitors so when I interact with the projector, the projector uses the total of widths of my screens as the resolution for the pointer.
To correct this, I ran 
xrandr:
```
[FONT=monospace][COLOR=#000000]Screen 0: minimum 8 x 8, current 4800 x 1080, maximum 32767 x 32767 [/COLOR]
HDMI-0 connected 1280x1024+3520+0 (normal left inverted right x axis y axis) 376mm x 301mm 
  1280x1024     60.02*+  75.02   
  1920x1080     59.94   
  1280x720      59.94   
  1152x864      75.00   
  1024x768      75.03    60.00   
  800x600       75.00    60.32   
  720x480       59.94    59.94   
  640x480       75.00    59.94   
DP-0 connected primary 1920x1080+1600+0 (normal left inverted right x axis y axis) 382mm x 215mm 
  1920x1080     75.00*+ 
DP-1 disconnected (normal left inverted right x axis y axis) 
DP-2 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 249mm 
  1600x900      60.00*+ 
  1440x900      59.89                                                                                                                                         
  1280x1024     60.02                                                                                                                                         
  1280x720      60.00                                                                                                                                         
  1024x768      60.00                                                                                                                                         
  800x600       60.32                                                                                                                                         
  640x480       59.94                                                                                                                                         
DP-3 disconnected (normal left inverted right x axis y axis)                                                                                                   
DP-4 disconnected (normal left inverted right x axis y axis) 
[/FONT]
```
xinput:```
[FONT=monospace][COLOR=#000000]&#9121; Virtual core pointer                          id=2    [master pointer  (3)] [/COLOR]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)] 
&#9116;   &#8627; Razer Razer Copperhead Laser Mouse        id=10   [slave  pointer  (2)] 
&#9116;   &#8627; 2.4G Cordless Mouse                       id=12   [slave  pointer  (2)] 
&#9116;   &#8627; Targus Laser Presentation Remote          id=14   [slave  pointer  (2)] 
&#9116;   &#8627; Targus Laser Presentation Remote          id=15   [slave  pointer  (2)] 
&#9116;   &#8627; EPSON EPSON EPSON 696Ui/696UT             id=16   [slave  pointer  (2)] 
&#9116;   &#8627; EPSON EPSON EPSON 696Ui/696UT             id=17   [slave  pointer  (2)] 
&#9116;   &#8627; EPSON EPSON EPSON 696Ui/696UT             id=18   [slave  pointer  (2)] 
&#9116;   &#8627; Logitech MX Master                        id=20   [slave  pointer  (2)] 
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=22   [slave  pointer  (2)] 
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)] 
   &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)] 
   &#8627; Power Button                              id=6    [slave  keyboard (3)] 
   &#8627; Video Bus                                 id=7    [slave  keyboard (3)] 
   &#8627; Power Button                              id=8    [slave  keyboard (3)] 
   &#8627; Sleep Button                              id=9    [slave  keyboard (3)] 
   &#8627; Razer Razer Copperhead Laser Mouse        id=11   [slave  keyboard (3)] 
   &#8627; Targus Laser Presentation Remote          id=13   [slave  keyboard (3)] 
   &#8627; Chicony USB 2.0 Camera                    id=19   [slave  keyboard (3)] 
   &#8627; AT Translated Set 2 keyboard              id=21   [slave  keyboard (3)]

[/FONT]
```

Then I can run a script which consists of :
```

[FONT=monospace][COLOR=#000000]xinput map-to-output 16 HDMI-0 [/COLOR]
xinput map-to-output 17 HDMI-0 
xinput map-to-output 18 HDMI-0
[/FONT]
```  

The  problem is that the ID for the 3 Epson values seems to change occasionally and I need to update my script.
I also have to run my script every time I turn the projector on or restart my computer.  
Is there a way to make this permanent?  some way to check the input IDs of Epson and set the map-to-output?

Thanks in advance.

---

### Post by efflandt on 2017-11-10
I had not worked with awk before, but took this as an exercise to learn something about it. This is what I wrote to test the basics using the output of your xinput for the file source and it works. First awk splits each line from grep into fields based on whitespace by default and each id=# for specific devices is the 7th field. The second awk uses -F '=' to specifically split on the equal sign where the second field is just the id number:```
#!/bin/sh
epson=`grep -i epson ~/xinput-epson-test.txt | awk '{ print $7 }' | awk -F '=' '{ print $2 }'`
for id in $epson
do echo xinput map-to-output $id HDMI-0
done
```So try this and see if it works to automatically get the Epson IDs for xinput. Note that the rest of the line after epson= is surrounded by backticks (grave):```
#!/bin/sh
epson=`xinput | grep -i epson | awk '{ print $7 }' | awk -F '=' '{ print $2 }'`
for id in $epson
do xinput map-to-output $id HDMI-0
done
```

---

### Post by Holger_Gehrke on 2017-11-11
I don't have a device that gives multiple IDs to the same symbolic name like your projector does, but xinput should be able to use the symbolic name in the 'xinput map-to-output' command like so:
```

xinput --map-to-output "[FONT=monospace]EPSON EPSON EPSON 696Ui/696UT" HDMI-0[/FONT]
```[FONT=monospace]

Holger
[/FONT]

---

### Post by m-knichel on 2017-11-13
Thanks for the suggestion.  The awk solution works great.  Now I would like to be able to have this run any time the Epson projector starts up.  I am wondering if I should just write a cron entry to run this script every 5 minutes or so?  Don't know how to detect when the projector powers up?

---

### Post by Holger_Gehrke on 2017-11-13
Check whether powering up or plugging the projector in triggers a udev event by running 'udevadm monitor -p' . If you get an event, you could write a rule to execute this script when this kind of event occurs.

Holger

---

### Post by m-knichel on 2017-11-14
I tried the command this morning when I arrived at school and this is what output I received:
```

[FONT=monospace][COLOR=#000000]KERNEL[87477.920488] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1 (usb)[/COLOR]
ACTION=add
BUSNUM=001
DEVNAME=/dev/bus/usb/001/021
DEVNUM=021
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1
DEVTYPE=usb_device
MAJOR=189
MINOR=20
PRODUCT=4b8/907/0
SEQNUM=5055
SUBSYSTEM=usb
TYPE=9/0/2

KERNEL[87477.921205] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1:1.0 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1:1.0
DEVTYPE=usb_interface
INTERFACE=9/0/1
MODALIAS=usb:v04B8p0907d0000dc09dsc00dp02ic09isc00ip01in00
PRODUCT=4b8/907/0
SEQNUM=5056
SUBSYSTEM=usb
TYPE=9/0/2

UDEV  [87477.926505] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1 (usb)
ACTION=add
BUSNUM=001
DEVNAME=/dev/bus/usb/001/021
DEVNUM=021
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1
DEVTYPE=usb_device
DRIVER=usb
ID_BUS=usb
ID_FOR_SEAT=usb-pci-0000_00_14_0-usb-0_4_4_2_1
ID_MODEL=0907                                                                                                                                                  
ID_MODEL_ENC=0907                                                                                                                                              
ID_MODEL_ID=0907                                                                                                                                               
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1                                                                                                                         
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1                                                                                                                     
ID_REVISION=0000                                                                                                                                               
ID_SERIAL=04b8_0907                                                                                                                                            
ID_USB_INTERFACES=:090001:090002:                                                                                                                              
ID_VENDOR=04b8
ID_VENDOR_ENC=04b8
ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
ID_VENDOR_ID=04b8
MAJOR=189
MINOR=20
PRODUCT=4b8/907/0
SEQNUM=5055
SUBSYSTEM=usb
TAGS=:seat:
TYPE=9/0/2
USEC_INITIALIZED=87477923970

UDEV  [87477.927613] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1:1.0 (usb)
.MM_USBIFNUM=00
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1:1.0
DEVTYPE=usb_interface
DRIVER=hub
FWUPD_GUID=26470009-97a8-4028-867a-bbbac6ee7bf0
FWUPD_MODEL=USB 3.0 VL812 B2 Hub
FWUPD_VENDOR=VIA
ID_USB_CLASS_FROM_DATABASE=Hub
ID_USB_PROTOCOL_FROM_DATABASE=TT per port
ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
INTERFACE=9/0/1
MODALIAS=usb:v04B8p0907d0000dc09dsc00dp02ic09isc00ip01in00
PRODUCT=4b8/907/0
SEQNUM=5056
SUBSYSTEM=usb
TYPE=9/0/2
USEC_INITIALIZED=87477927466

KERNEL[87478.281244] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4 (usb)
ACTION=add
BUSNUM=001
DEVNAME=/dev/bus/usb/001/022
DEVNUM=022
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4
DEVTYPE=usb_device
MAJOR=189
MINOR=21
PRODUCT=4b8/326/1234
SEQNUM=5057
SUBSYSTEM=usb
TYPE=0/0/0

KERNEL[87478.282202] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0
DEVTYPE=usb_interface
INTERFACE=3/0/2
MODALIAS=usb:v04B8p0326d1234dc00dsc00dp00ic03isc00ip02in00
PRODUCT=4b8/326/1234
SEQNUM=5058
SUBSYSTEM=usb
TYPE=0/0/0

KERNEL[87478.282495] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011 (hid)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011
HID_ID=0003:000004B8:00000326
HID_NAME=EPSON EPSON EPSON 696Ui/696UT
HID_PHYS=usb-0000:00:14.0-4.4.2.1.4/input0
HID_UNIQ=
MODALIAS=hid:b0003g0001v000004B8p00000326
SEQNUM=5059
SUBSYSTEM=hid

KERNEL[87478.282710] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30 
(input)
ABS=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30
EV=1b
KEY=30000 0 0 0 0 0 0 0 0
MODALIAS=input:b0003v04B8p0326e0200-e0,1,3,4,k110,111,ra0,1,m4,lsfw
MSC=10
NAME="EPSON EPSON EPSON 696Ui/696UT"
PHYS="usb-0000:00:14.0-4.4.2.1.4/input0"
PRODUCT=3/4b8/326/200
PROP=0
SEQNUM=5060
SUBSYSTEM=input
UNIQ=""

KERNEL[87478.282789] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/
mouse5 (input)
ACTION=add
DEVNAME=/dev/input/mouse5
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/mouse5
MAJOR=13
MINOR=37
SEQNUM=5061
SUBSYSTEM=input

KERNEL[87478.336227] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/
event21 (input)
ACTION=add
DEVNAME=/dev/input/event21
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/event21
MAJOR=13
MINOR=85
SEQNUM=5062
SUBSYSTEM=input

KERNEL[87478.336336] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/
js0 (input)
ACTION=add
DEVNAME=/dev/input/js0
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/js0
MAJOR=13
MINOR=0
SEQNUM=5063
SUBSYSTEM=input

KERNEL[87478.336428] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/usbmisc/hiddev3 (usbmisc)
ACTION=add
DEVNAME=/dev/usb/hiddev3
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/usbmisc/hiddev3
MAJOR=180
MINOR=3
SEQNUM=5064
SUBSYSTEM=usbmisc

KERNEL[87478.336524] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/hidraw/hidraw8
 (hidraw)
ACTION=add
DEVNAME=/dev/hidraw8
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/hidraw/hidraw8
MAJOR=242
MINOR=8
SEQNUM=5065
SUBSYSTEM=hidraw

KERNEL[87478.336615] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1
DEVTYPE=usb_interface
INTERFACE=3/0/2
MODALIAS=usb:v04B8p0326d1234dc00dsc00dp00ic03isc00ip02in01
PRODUCT=4b8/326/1234
SEQNUM=5066
SUBSYSTEM=usb
TYPE=0/0/0

KERNEL[87478.337077] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012 (hid)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012
HID_ID=0003:000004B8:00000326
HID_NAME=EPSON EPSON EPSON 696Ui/696UT
HID_PHYS=usb-0000:00:14.0-4.4.2.1.4/input1
HID_UNIQ=
MODALIAS=hid:b0003g0001v000004B8p00000326
SEQNUM=5067
SUBSYSTEM=hid

KERNEL[87478.337768] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31 
(input)
ABS=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31
EV=1b
KEY=30000 0 0 0 0 0 0 0 0
MODALIAS=input:b0003v04B8p0326e0200-e0,1,3,4,k110,111,ra0,1,m4,lsfw
MSC=10
NAME="EPSON EPSON EPSON 696Ui/696UT"
PHYS="usb-0000:00:14.0-4.4.2.1.4/input1"
PRODUCT=3/4b8/326/200
PROP=0
SEQNUM=5068
SUBSYSTEM=input
UNIQ=""

KERNEL[87478.337842] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/
mouse6 (input)
ACTION=add
DEVNAME=/dev/input/mouse6
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/mouse6
MAJOR=13
MINOR=38
SEQNUM=5069
SUBSYSTEM=input

KERNEL[87478.337876] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/
event22 (input)
ACTION=add
DEVNAME=/dev/input/event22
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/event22
MAJOR=13
MINOR=86
SEQNUM=5070
SUBSYSTEM=input

KERNEL[87478.337910] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/
js1 (input)
ACTION=add
DEVNAME=/dev/input/js1
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/js1
MAJOR=13
MINOR=1
SEQNUM=5071
SUBSYSTEM=input

KERNEL[87478.337941] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/usbmisc/hiddev4 (usbmisc)
ACTION=add
DEVNAME=/dev/usb/hiddev4
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/usbmisc/hiddev4
MAJOR=180
MINOR=4
SEQNUM=5072
SUBSYSTEM=usbmisc

KERNEL[87478.337973] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/hidraw/hidraw9
 (hidraw)
ACTION=add
DEVNAME=/dev/hidraw9
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/hidraw/hidraw9
MAJOR=242
MINOR=9
SEQNUM=5073
SUBSYSTEM=hidraw

KERNEL[87478.338018] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2 (usb)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2
DEVTYPE=usb_interface
INTERFACE=3/0/0
MODALIAS=usb:v04B8p0326d1234dc00dsc00dp00ic03isc00ip00in02
PRODUCT=4b8/326/1234
SEQNUM=5074
SUBSYSTEM=usb
TYPE=0/0/0

KERNEL[87478.338353] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013 (hid)
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013
HID_ID=0003:000004B8:00000326
HID_NAME=EPSON EPSON EPSON 696Ui/696UT
HID_PHYS=usb-0000:00:14.0-4.4.2.1.4/input2
HID_UNIQ=
MODALIAS=hid:b0003g0004v000004B8p00000326
SEQNUM=5075
SUBSYSTEM=hid

KERNEL[87478.338905] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32 
(input)
ABS=a608000 3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32
EV=b
KEY=400 0 0 0 0 0 0 0 0 0 0
MODALIAS=input:b0003v04B8p0326e0200-e0,1,3,k14A,ra0,1,2F,35,36,39,3B,mlsfw
NAME="EPSON EPSON EPSON 696Ui/696UT"
PHYS="usb-0000:00:14.0-4.4.2.1.4/input2"
PRODUCT=3/4b8/326/200
PROP=2
SEQNUM=5076
SUBSYSTEM=input
UNIQ=""

KERNEL[87478.338966] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/
mouse7 (input)
ACTION=add
DEVNAME=/dev/input/mouse7
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/mouse7
MAJOR=13
MINOR=39
SEQNUM=5077
SUBSYSTEM=input

KERNEL[87478.339001] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/
event23 (input)
ACTION=add
DEVNAME=/dev/input/event23
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/event23
MAJOR=13
MINOR=87
SEQNUM=5078
SUBSYSTEM=input

KERNEL[87478.339034] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/usbmisc/hiddev5 (usbmisc)
ACTION=add
DEVNAME=/dev/usb/hiddev5
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/usbmisc/hiddev5
MAJOR=180
MINOR=5
SEQNUM=5079
SUBSYSTEM=usbmisc

KERNEL[87478.339067] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/hidraw/hidraw1
0 (hidraw)
ACTION=add
DEVNAME=/dev/hidraw10
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/hidraw/hidraw10
MAJOR=242
MINOR=10
SEQNUM=5080
SUBSYSTEM=hidraw

UDEV  [87478.346994] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4 (usb)
ACTION=add
BUSNUM=001
DEVNAME=/dev/bus/usb/001/022
DEVNUM=022
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4
DEVTYPE=usb_device
DRIVER=usb
ID_BUS=usb
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_USB_INTERFACES=:030002:030000:
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
ID_VENDOR_ID=04b8
MAJOR=189
MINOR=21
PRODUCT=4b8/326/1234
SEQNUM=5057
SUBSYSTEM=usb
TYPE=0/0/0
USEC_INITIALIZED=87478341864

UDEV  [87478.348799] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0 (usb)
.MM_USBIFNUM=00
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0
DEVTYPE=usb_interface
DRIVER=usbhid
ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
INTERFACE=3/0/2
MODALIAS=usb:v04B8p0326d1234dc00dsc00dp00ic03isc00ip02in00
PRODUCT=4b8/326/1234
SEQNUM=5058
SUBSYSTEM=usb
TYPE=0/0/0
USEC_INITIALIZED=87478348614

UDEV  [87478.349626] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1 (usb)
.MM_USBIFNUM=01
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1
DEVTYPE=usb_interface
DRIVER=usbhid
ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
INTERFACE=3/0/2
MODALIAS=usb:v04B8p0326d1234dc00dsc00dp00ic03isc00ip02in01
PRODUCT=4b8/326/1234
SEQNUM=5066
SUBSYSTEM=usb
TYPE=0/0/0
USEC_INITIALIZED=87478349393

UDEV  [87478.349697] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2 (usb)
.MM_USBIFNUM=02
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2
DEVTYPE=usb_interface
DRIVER=usbhid
ID_VENDOR_FROM_DATABASE=Seiko Epson Corp.
INTERFACE=3/0/0
MODALIAS=usb:v04B8p0326d1234dc00dsc00dp00ic03isc00ip00in02
PRODUCT=4b8/326/1234
SEQNUM=5074
SUBSYSTEM=usb
TYPE=0/0/0
USEC_INITIALIZED=87478349444

UDEV  [87478.351133] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011 (hid)
.MM_USBIFNUM=00
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011
DRIVER=hid-generic
HID_ID=0003:000004B8:00000326
HID_NAME=EPSON EPSON EPSON 696Ui/696UT
HID_PHYS=usb-0000:00:14.0-4.4.2.1.4/input0
HID_UNIQ=
MODALIAS=hid:b0003g0001v000004B8p00000326
SEQNUM=5059
SUBSYSTEM=hid
USEC_INITIALIZED=87478350944

UDEV  [87478.352268] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/usbmisc/hiddev3 (usbmisc)
.MM_USBIFNUM=00
ACTION=add
DEVNAME=/dev/usb/hiddev3
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/usbmisc/hiddev3
MAJOR=180
MINOR=3
SEQNUM=5064
SUBSYSTEM=usbmisc
USEC_INITIALIZED=87478352203

UDEV  [87478.353181] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013 (hid)
.MM_USBIFNUM=02
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013
DRIVER=hid-multitouch
HID_ID=0003:000004B8:00000326
HID_NAME=EPSON EPSON EPSON 696Ui/696UT
HID_PHYS=usb-0000:00:14.0-4.4.2.1.4/input2
HID_UNIQ=
MODALIAS=hid:b0003g0004v000004B8p00000326
SEQNUM=5075
SUBSYSTEM=hid
USEC_INITIALIZED=87478352992

UDEV  [87478.354051] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/usbmisc/hiddev4 (usbmisc)
.MM_USBIFNUM=01
ACTION=add
DEVNAME=/dev/usb/hiddev4
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/usbmisc/hiddev4
MAJOR=180
MINOR=4
SEQNUM=5072
SUBSYSTEM=usbmisc
USEC_INITIALIZED=87478353991

UDEV  [87478.354359] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30 
(input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=00
ABS=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30
EV=1b
ID_BUS=usb
ID_FOR_SEAT=input-pci-0000_00_14_0-usb-0_4_4_2_1_4_1_0
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.0
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_0
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=00
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
KEY=30000 0 0 0 0 0 0 0 0
MODALIAS=input:b0003v04B8p0326e0200-e0,1,3,4,k110,111,ra0,1,m4,lsfw
MSC=10
NAME="EPSON EPSON EPSON 696Ui/696UT"
PHYS="usb-0000:00:14.0-4.4.2.1.4/input0"
PRODUCT=3/4b8/326/200
PROP=0
SEQNUM=5060
SUBSYSTEM=input
TAGS=:seat:
UNIQ=""
USEC_INITIALIZED=87478354179

UDEV  [87478.354455] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/hidraw/hidraw8
 (hidraw)
.MM_USBIFNUM=00
ACTION=add
DEVNAME=/dev/hidraw8
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/hidraw/hidraw8
MAJOR=242
MINOR=8
SEQNUM=5065
SUBSYSTEM=hidraw
USEC_INITIALIZED=87478354314

UDEV  [87478.356471] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/hidraw/hidraw1
0 (hidraw)
.MM_USBIFNUM=02
ACTION=add
DEVNAME=/dev/hidraw10
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/hidraw/hidraw10
MAJOR=242
MINOR=10
SEQNUM=5080
SUBSYSTEM=hidraw
USEC_INITIALIZED=87478355558

UDEV  [87478.358193] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012 (hid)
.MM_USBIFNUM=01
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012
DRIVER=hid-generic
HID_ID=0003:000004B8:00000326
HID_NAME=EPSON EPSON EPSON 696Ui/696UT
HID_PHYS=usb-0000:00:14.0-4.4.2.1.4/input1
HID_UNIQ=
MODALIAS=hid:b0003g0001v000004B8p00000326
SEQNUM=5067
SUBSYSTEM=hid
USEC_INITIALIZED=87478358009

UDEV  [87478.358612] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/usbmisc/hiddev5 (usbmisc)
.MM_USBIFNUM=02
ACTION=add
DEVNAME=/dev/usb/hiddev5
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/usbmisc/hiddev5
MAJOR=180
MINOR=5
SEQNUM=5079
SUBSYSTEM=usbmisc
USEC_INITIALIZED=87478358449

UDEV  [87478.358708] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32 
(input)
.MM_USBIFNUM=02
ABS=a608000 3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32
EV=b
ID_BUS=usb
ID_FOR_SEAT=input-pci-0000_00_14_0-usb-0_4_4_2_1_4_1_2
ID_INPUT=1
ID_INPUT_TOUCHSCREEN=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.2
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_2
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=02
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
KEY=400 0 0 0 0 0 0 0 0 0 0
MODALIAS=input:b0003v04B8p0326e0200-e0,1,3,k14A,ra0,1,2F,35,36,39,3B,mlsfw
NAME="EPSON EPSON EPSON 696Ui/696UT"
PHYS="usb-0000:00:14.0-4.4.2.1.4/input2"
PRODUCT=3/4b8/326/200
PROP=2
SEQNUM=5076
SUBSYSTEM=input
TAGS=:seat:
UNIQ=""
USEC_INITIALIZED=87478358449

UDEV  [87478.359382] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/
mouse5 (input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=00
ACTION=add
DEVLINKS=/dev/input/by-id/usb-EPSON_EPSON_EPSON_696Ui_696UT-mouse /dev/input/by-path/pci-0000:00:14.0-usb-0:4.4.2.1.4:1.0-mouse
DEVNAME=/dev/input/mouse5
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/mouse5
ID_BUS=usb
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.0
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_0
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=00
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
MAJOR=13
MINOR=37
SEQNUM=5061
SUBSYSTEM=input
USEC_INITIALIZED=87478359279

UDEV  [87478.361848] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31 
(input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=01
ABS=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31
EV=1b
ID_BUS=usb
ID_FOR_SEAT=input-pci-0000_00_14_0-usb-0_4_4_2_1_4_1_1
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.1
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_1
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=01
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
KEY=30000 0 0 0 0 0 0 0 0
MODALIAS=input:b0003v04B8p0326e0200-e0,1,3,4,k110,111,ra0,1,m4,lsfw
MSC=10
NAME="EPSON EPSON EPSON 696Ui/696UT"
PHYS="usb-0000:00:14.0-4.4.2.1.4/input1"
PRODUCT=3/4b8/326/200
PROP=0
SEQNUM=5068
SUBSYSTEM=input
TAGS=:seat:
UNIQ=""
USEC_INITIALIZED=87478361652

UDEV  [87478.362549] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/hidraw/hidraw9
 (hidraw)
.MM_USBIFNUM=01
ACTION=add
DEVNAME=/dev/hidraw9
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/hidraw/hidraw9
MAJOR=242
MINOR=9
SEQNUM=5073
SUBSYSTEM=hidraw
USEC_INITIALIZED=87478362282

UDEV  [87478.362907] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/
js0 (input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=00
ACTION=add
DEVLINKS=/dev/input/by-id/usb-EPSON_EPSON_EPSON_696Ui_696UT-mouse /dev/input/by-path/pci-0000:00:14.0-usb-0:4.4.2.1.4:1.0-mouse
DEVNAME=/dev/input/js0
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/js0
ID_BUS=usb
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.0
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_0
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=00
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
MAJOR=13
MINOR=0
SEQNUM=5063
SUBSYSTEM=input
USEC_INITIALIZED=87478362812

UDEV  [87478.366746] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/
mouse6 (input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=01
ACTION=add
DEVLINKS=/dev/input/by-path/pci-0000:00:14.0-usb-0:4.4.2.1.4:1.1-mouse /dev/input/by-id/usb-EPSON_EPSON_EPSON_696Ui_696UT-if01-mouse
DEVNAME=/dev/input/mouse6
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/mouse6
ID_BUS=usb
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.1
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_1
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=01
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
MAJOR=13
MINOR=38
SEQNUM=5069
SUBSYSTEM=input
USEC_INITIALIZED=87478366655

UDEV  [87478.368279] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/
js1 (input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=01
ACTION=add
DEVLINKS=/dev/input/by-path/pci-0000:00:14.0-usb-0:4.4.2.1.4:1.1-mouse /dev/input/by-id/usb-EPSON_EPSON_EPSON_696Ui_696UT-if01-mouse
DEVNAME=/dev/input/js1
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/js1
ID_BUS=usb
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.1
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_1
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=01
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
MAJOR=13
MINOR=1
SEQNUM=5071
SUBSYSTEM=input
USEC_INITIALIZED=87478368171

UDEV  [87478.368915] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/
mouse7 (input)
.MM_USBIFNUM=02
ACTION=add
DEVNAME=/dev/input/mouse7
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/mouse7
ID_BUS=usb
ID_INPUT=1
ID_INPUT_TOUCHSCREEN=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.2
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_2
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=02
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
MAJOR=13
MINOR=39
SEQNUM=5077
SUBSYSTEM=input
USEC_INITIALIZED=87478368809

UDEV  [87478.550579] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/
event21 (input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=00
ACTION=add
DEVLINKS=/dev/input/by-id/usb-EPSON_EPSON_EPSON_696Ui_696UT-event-mouse /dev/input/by-path/pci-0000:00:14.0-usb-0:4.4.2.1.4:1.0-event-mouse
DEVNAME=/dev/input/event21
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.0/0003:04B8:0326.0011/input/input30/event21
ID_BUS=usb
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.0
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_0
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=00
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
LIBINPUT_DEVICE_GROUP=3/4b8/326/200:usb-0000:00:14.0-4.4.2.1
MAJOR=13
MINOR=85
SEQNUM=5062
SUBSYSTEM=input
USEC_INITIALIZED=87478550484

UDEV  [87478.563858] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/
event22 (input)
.INPUT_CLASS=mouse
.MM_USBIFNUM=01
ACTION=add
DEVLINKS=/dev/input/by-path/pci-0000:00:14.0-usb-0:4.4.2.1.4:1.1-event-mouse /dev/input/by-id/usb-EPSON_EPSON_EPSON_696Ui_696UT-if01-event-mouse
DEVNAME=/dev/input/event22
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.1/0003:04B8:0326.0012/input/input31/event22
ID_BUS=usb
ID_INPUT=1
ID_INPUT_MOUSE=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.1
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_1
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=01
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
LIBINPUT_DEVICE_GROUP=3/4b8/326/200:usb-0000:00:14.0-4.4.2.1
MAJOR=13
MINOR=86
SEQNUM=5070
SUBSYSTEM=input
USEC_INITIALIZED=87478563735

UDEV  [87478.571020] add      /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/
event23 (input)
.MM_USBIFNUM=02
ACTION=add
DEVLINKS=/dev/input/by-path/pci-0000:00:14.0-usb-0:4.4.2.1.4:1.2-event /dev/input/by-id/usb-EPSON_EPSON_EPSON_696Ui_696UT-event-if02
DEVNAME=/dev/input/event23
DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.4/1-4.4.2/1-4.4.2.1/1-4.4.2.1.4/1-4.4.2.1.4:1.2/0003:04B8:0326.0013/input/input32/event23
ID_BUS=usb
ID_INPUT=1
ID_INPUT_TOUCHSCREEN=1
ID_MODEL=EPSON_EPSON_696Ui_696UT
ID_MODEL_ENC=EPSON\x20EPSON\x20696Ui\x2f696UT
ID_MODEL_ID=0326
ID_PATH=pci-0000:00:14.0-usb-0:4.4.2.1.4:1.2
ID_PATH_TAG=pci-0000_00_14_0-usb-0_4_4_2_1_4_1_2
ID_REVISION=1234
ID_SERIAL=EPSON_EPSON_EPSON_696Ui_696UT
ID_TYPE=hid
ID_USB_DRIVER=usbhid
ID_USB_INTERFACES=:030002:030000:
ID_USB_INTERFACE_NUM=02
ID_VENDOR=EPSON
ID_VENDOR_ENC=EPSON
ID_VENDOR_ID=04b8
LIBINPUT_DEVICE_GROUP=3/4b8/326/200:usb-0000:00:14.0-4.4.2.1
MAJOR=13
MINOR=87
SEQNUM=5078
SUBSYSTEM=input
USEC_INITIALIZED=87478570905
[/FONT]
```


I tried to create a udev rule : 100-epsonInput.rules

```
[FONT=monospace]
SUBSYSTEMS=="input", DRIVERS=="usbhid", ATTRS{vendor}=="EPSON", ATTRS{model}=="EPSON_EPSON_696Ui_696UT", ACTION=="add", RUN+="/home/knichel/SCRIPTS/fixEpsonTablet.sh"
[/FONT]
```


I'm not sure how to capture this when it happens and initiate the script. 

Thanks in advance for the assistance.

---

