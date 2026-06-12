---
title: "xbox controller memory access"
date: 2009-04-18
forum: Hardware
---

### Post by tuxunkhamon on 2009-04-18
I've added a male usb end to my old xbox controller wire so that I can hook it up to my pc (running Ubuntu Intrepid).  The controller works great, but I'm unable to access the memory card attached to it.  If anyone can help with this, I would greatly appreciate it.  Below is a chronicle of my experience thus far.  Thanks in advance.


A snapshot of my device directory before connecting the controller.
[COLOR="Red"]name@host:~$ ls /dev > ls1.txt[/COLOR]

Another snapshot after connecting the controller.
[COLOR="Red"]name@host:~$ ls /dev > ls2.txt
name@host:~$ dmesg[/COLOR]
[COLOR="DarkGreen"]    ...
     usb 2-3: new full speed USB device using ohci_hcd and address 2
     usb 2-3: configuration #1 chosen from 1 choice
     hub 2-3:1.0: USB hub found
     hub 2-3:1.0: 3 ports detected
     usb 2-3.1: new full speed USB device using ohci_hcd and address 3
     usb 2-3.1: configuration #1 chosen from 1 choice
     input: Microsoft X-Box pad v2 (US) as /devices/pci0000:00/0000:00:03.0/usb2/2-3/2-3.1/2-3.1:1.0/input/input7
     usbcore: registered new interface driver xpad
     xpad: X-Box pad driver[/COLOR]
[COLOR="Red"]name@host:~$ lsusb[/COLOR]
[COLOR="DarkGreen"]    Bus 002 Device 003: ID 045e:0289 Microsoft Corp. Xbox Controller S
    Bus 002 Device 002: ID 045e:0288 Microsoft Corp. Xbox Controller S Hub
    ...
[/COLOR]
And then one after connecting the memory unit to the controller.
[COLOR="Red"]name@host:~$ ls /dev > ls3.txt
name@host:~$ dmesg[/COLOR]
[COLOR="DarkGreen"]    ...
     usb 2-3.2: new full speed USB device using ohci_hcd and address 4
     usb 2-3.2: configuration #1 chosen from 1 choice
[COLOR="Red"]name@host:~$ lsusb[/COLOR]
    Bus 002 Device 004: ID 045e:0280 Microsoft Corp. XBox Device
    ...
[/COLOR]
So it seems to me that according to dmesg:
1. The controller and empty expansion slots were properly recognized and assigned addressess.  The controller itself was identified as an input device and the xpad interface driver was registered.
2. After connecting the memory card, a new usb device was identified and assigned an address.

Everything seems ok so far, but what about the /dev snapshots?
[COLOR="Red"]name@host:~$  diff ls1.txt ls2.txt[/COLOR]
[COLOR="DarkGreen"] 682a683,687
 > usbdev2.2_ep00
 > usbdev2.2_ep81
 > usbdev2.3_ep00
 > usbdev2.3_ep02
 > usbdev2.3_ep81
[/COLOR][COLOR="Red"]name@host:~$ diff ls2.txt ls3.txt[/COLOR]
[COLOR="DarkGreen"] 687a688,690
 > usbdev2.4_ep00
 > usbdev2.4_ep02
 > usbdev2.4_ep81
[/COLOR]
I'm not sure exactly what this tells me.  It seems that the new devices have been identified, but I usually get a new sd* entry when I plug in a usb storage device.  The only thing I am sure of is that my memory card has been assigned the usb device address 002:004.  Let's make sure this is correct.
[COLOR="Red"]name@host:~$ lsusb -s 002:004 -v[/COLOR]
[COLOR="DarkGreen"] 
 Bus 002 Device 004: ID 045e:0280 Microsoft Corp. XBox Device
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               1.10
   bDeviceClass            0 (Defined at Interface level)
   bDeviceSubClass         0 
   bDeviceProtocol         0 
   bMaxPacketSize0         8
   idVendor           0x045e Microsoft Corp.
   idProduct          0x0280 XBox Device
   bcdDevice            0.0e
   iManufacturer           0 
   iProduct                0 
   iSerial                 0 
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength           32
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0 
     bmAttributes         0x80
       (Bus Powered)
     MaxPower               60mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           2
       bInterfaceClass         8 Mass Storage
       bInterfaceSubClass     66 
       bInterfaceProtocol     80 
       iInterface              0 
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0040  1x 64 bytes
         bInterval               0
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x02  EP 2 OUT
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0040  1x 64 bytes
         bInterval               0
 cannot read device status, Operation not permitted (1) 
[/COLOR]
Again, I'm not exactly sure what all this means.  It seems that I have properly identified the usb address of the memory card, and I notice from the above output that it has been correctly identified as a "Mass Storage" device.

Ok, so I may not have a /dev/sd* entry for the card, but shouldn't it still be (theoretically) accessible via /dev/bus/usb/002/004?  If this is right, I should be able to use dd to flash the memory:
[COLOR="Red"]name@host:~$ dd if=filename.img of=/dev/bus/usb/002/004[/COLOR]
[COLOR="DarkGreen"] dd: writing to `/dev/bus/usb/002/004': Invalid argument
 1+0 records in
 0+0 records out
 0 bytes (0 B) copied, 0.0264747 s, 0.0 kB/s
[/COLOR]
I'm not sure why this doesn't work.  Is the card not accessible via /dev/bus/usb/002/004?  Am I missing some flag/option when issuing the dd command?  Any help would be greatly appreciated.

---

### Post by tuxunkhamon on 2009-04-19
Ok, so I've made some progress, but I'm still not sure about how to resolve this.

[COLOR="Red"]name@host:~$ sudo mount -t usbfs usbfs /proc/bus/usb
name@host:~$ cat /proc/bus/usb/devices[/COLOR]
[COLOR="DarkGreen"]T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=0280 Rev= 0.0e
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 60mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=42 Prot=50 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
[/COLOR]

I notice that it says "Driver=(none)" above.  Shouldn't that read "Driver=usb-storage"?  

Anybody have any suggestions as to how to fix this?

---

