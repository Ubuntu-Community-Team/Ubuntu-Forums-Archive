---
title: "Benq M101 Optical Mouse not working on Ubuntu 8.0.4"
date: 2010-01-17
forum: Hardware
---

### Post by Shelmie on 2010-01-17
Hi,

I'm pretty new to Ubuntu and Linux, and have just installed version 8.0.4 on my Samsung Q30 laptop.  I installed this version as the latest one wouldn't boot up.  

I have a Benq M101 optical mouse and haven't been able to get this to work properly after installing Ubuntu.  After bootup, it actually responds, but there is quite a bit of lag and it's quite unusable because of this.  The touchpad works fine however.  When I unplug and plug it back in, it doesn't even register at all (so I have to reboot).

Not sure where to start, have tried looking for Benq linux drivers and also searching through these forums but can't find anything on this mouse.

Thanks in advance for any help!

:D

---

### Post by Shelmie on 2010-01-21
Hi,

I've also tried another generic optical mouse and am getting the same probs.. if anyone could help that would be great... thanks...!!

---

### Post by cpm04 on 2010-01-24
same here
looks like the mouse input is processed every 500ms or so.

i think this broke about 8.04 (cant remember, long ago), with a kernel update. I thought it would be temporary but i have tried 3 new ubuntus and still the same. Never used linux on this laptop ever since...

Some comments about the issue:
- with the live cd seems to work 
- booting up with the mouse connected shows the problem
- booting up without the mouse, and plugging it in afterwards, it works fine
- booting up with another usb (extenal HD here), and the mouse already plugged, works fine...

---

### Post by gonzo.d on 2010-12-28
Hi there,

got also a Samsung Q30 with Maverick, which also does not start with mouse plugged in (hardreset). But it starts when I also plug in a Terratec Cinergy T XXS. If I use only the Cinergy-Stick the machine hangs on boot but the powerbutton will shutdown the system.
It used to work in former Ubuntu-Versions.

This what lsusb -v answers:
```
Bus 002 Device 002: ID 046d:c05b Logitech, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc05b 
  bcdDevice           54.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower               98mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      67
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
        wMaxPacketSize     0x0006  1x 6 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
```

```
dmesg | grep usb
[    0.085953] usbcore: registered new interface driver usbfs
[    0.085976] usbcore: registered new interface driver hub
[    0.086019] usbcore: registered new device driver usb
[  487.340088] usb 2-2: new low speed USB device using uhci_hcd and address 2
[  487.674009] usbcore: registered new interface driver hiddev
[  487.691538] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input7
[  487.692257] generic-usb 0003:046D:C05B.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-2/input0
[  487.693671] usbcore: registered new interface driver usbhid
[  487.693677] usbhid: USB HID core driver
```

irqpoll worked earlier but now it isn't working any more.

If I use irqpoll the machine will hang on booting. 
[IMG]http://media.cdn.ubuntu-de.org/forum/attachments/2721832/irqpoll.jpg[/IMG]
Can I see that on any log?

Any ideas how to fix that?

Happy New Year and
cheerio g

---

### Post by gonzo.d on 2011-01-09
Hi there,

I considered following recommendations [http://ubuntuforums.org/showthread.php?t=1236267&highlight=slow+%2B+USB+%2B+mouse](http://ubuntuforums.org/showthread.php?t=1236267&highlight=slow+%2B+USB+%2B+mouse) and tried different switches to the kernel parameters.

Finally 
```
noapic acpi=noirq nolapic
```
made my Q30 start with Usb-mouse plugged in and all powermanagement states work fine in Maverick.

cheerio g

---

