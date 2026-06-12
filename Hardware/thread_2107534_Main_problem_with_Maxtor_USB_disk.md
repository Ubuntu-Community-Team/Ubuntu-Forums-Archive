---
title: "Main problem with Maxtor USB disk"
date: 2013-01-22
forum: Hardware
---

### Post by ereinion on 2013-01-22
Hi Guys!
I have searched in the internet, but i was not able to find a solution to my problem. I have also written in the Italian Ubuntu forum, but I think that you may also help me.
I have a maxtor usb drive,  when I connect it to the pc nothing happens, the drive is not visible neither in the the desktop or in the disk management.
But if I use the command lsusb I see that the drive is connected to the pc. Here are the outputs:

[Screen_01]("http://sphotos-c.ak.fbcdn.net/hphotos-ak-prn1/72837_4773053277655_1737669018_n.jpg")

[Screen_02]("http://sphotos-g.ak.fbcdn.net/hphotos-ak-ash3/74960_4773055317706_904273741_n.jpg")

Have you any idea of how i may solve the problem? I have some datas on that HD that I MUST save, at any cost.
Thank you all!

---

### Post by JOHNNYG713 on 2013-01-22
I take it as an external hard drive, try to install it internally, as a last resort.

---

### Post by sudodus on 2013-01-22
> **JOHNNYG713 said:**
> I take it as an external hard drive, try to install it internally, as a last resort.
+1

But before that you can try to

- connect it to another computer, even if it is Windows ;-)

- mount it manually with the command [FONT="Courier New"][SIZE="3"]mount[/SIZE][/FONT]

- try all the USB ports on your computer (also at the back of it (if a desktop or workstation)).

- try with another USB cable

---

### Post by ereinion on 2013-01-23
thank you both!
I'll try to use another cable. It is an IDE HD so have to go anfd buy one as soon as I have some time.
Thank you for your help, i'lllet you know...

---

### Post by Le0Chavez on 2013-02-25
I have a similar problem when I connect my maxtor one plus 4 but the printout of lusb command is different:

Bus 002 Device 004: ID 0d49:7300 Maxtor 
[COLOR="Red"][B]libusb couldn't open USB device /dev/bus/usb/002/004: Permission denied.
[/B][/COLOR][/B][/B]libusb requires write access to USB device nodes.
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0d49 Maxtor
  idProduct          0x7300 
  bcdDevice            1.21
  iManufacturer           1 
  iProduct                3 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

THE REMARKED TWO ROWS ARE THE PROBLEM, HOW CAN I OVERRIDE THIS ISSUE?

---

### Post by sudodus on 2013-02-26
Welcome to the Ubuntu Forums :-)

It is hard to help, because we know too little about your hardware and software and what you can and cannot do with that Maxtor drive. '***A good description is almost a solution.***'

So please give us more details about your problem. And it might be a good idea that you ***start an own thread ***with a good descriptive title, that can attract people, who know about your problem.

Some linux commands need superuser privileges. What happens if you put sudo in front of the command line so that
```
command line 
``` becomes
```
sudo command line 
```

---

