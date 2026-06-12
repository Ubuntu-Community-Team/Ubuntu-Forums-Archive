---
title: "Trying to connect UPS. Can someone figure out what &quot;USB Name&quot; means?"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by Mogul345 on 2007-11-20
Does anyone out here have a Powercom UPS that came with only a USB connection? I guess I don't really have a Powercom UPS per se,  it really is a power sentry model 100897. When I plug it in to my ubuntu box, and i run lsusb I get the following: 

```
 lsusb -v -s 001:003

Bus 001 Device 003: ID 0d9f:0001 Powercom Co., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0d9f Powercom Co., Ltd
  idProduct          0x0001 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x40
      (Missing must-be-set bit!)
      Self Powered
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     175
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval             250
cannot read device status, Operation not permitted (1)
```

Thus, I think it is a Powercom UPS due to the VendorID. Now, the UPS actually came with a program called "UPSMON for Linux". From googling, I've found that this program is not related to the NUT UPS tools, and is also released by Powercom. Unfortunately, this "UPSMON for Linux" only works with serial connections it appears, as the readme says to use ttys0 or ttys1 to point to where the UPS is connected to, which apparently are how serial ports are represented in the /dev directory.

So I contacted Power Sentry, they don't support Linux (obviously). I then contacted Powercom directly, and they gave me a link to their downloads page which had a version of UPSMON that was for USB Powercom UPS's. I've downloaded it, but when reading the readme I'm stumped by what they mean by "USB Name" Here's the readme:

```
1. Please login as "root"

 

    2. insert the disk

            ex: > mcopy A:upsmon_usbv091.tar /usr

            (copy to user's preferred directory¡^

 

    3. exract the UPSMON files

            ex: > tar -xvf upsmon_usbv091.tar

 

    4. enter upsmon directory

            ex: > cd upsmon

 

    5. copy  "down" files to root directory (shut down command)

            ex: > cp down  /

 

    6. execute UPSMON software

            

            ==> ./upsmon_usb1   Parameter_A   Parameter_B   Parameter_C

            

      Default parameters

             Parameter_A : AC_Fail_Countdown time

                      Parameter_B : UPS TurnOFF Delay time

                      Parameter_C : USB Name

            

EX: When the power goes off, UPSMON will count down for 100 seconds.  If the power is not back on within 100 seconds, UPS will count down another 120 seconds and then shut down UPS.   While first 100 second count down ends, UPSMON program will execute the OS shutdown command.    If the power comes back within 100 seconds, the shutdown command will be cancelled.
```

The help from Powercom also came with a big, fat disclaimer stating that the generic Powercom version of UPSMON might not work with my Power Sentry UPS. But I feel it's worth a shot. Has anyone else in this wide world encountered one of these UPS's?

-Don

---

### Post by Mogul345 on 2007-12-08
bump

---

