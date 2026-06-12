---
title: "Mobile Pre Usb - Soundcard stopped working"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by sonium on 2006-11-19
Hi, after a fresh installed the external usb-soundcard worked fine. But after I brought my PC to another places I reconnected the device to another port. From this time I didn't work anymore. For dapper there exists a programm that modifies the udev rule set an fixed this issue, but for edgy it doesn't work. Maybe the udev system is to different from debian.

So here is some information from lsusb:

```
Bus 003 Device 007: ID 0763:2804 Midiman 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass          254 Application Specific Interface
  bDeviceSubClass         1 Device Firmware Update
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0763 Midiman
  idProduct          0x2804 
  bcdDevice            1.00
  iManufacturer           1 Unknown
  iProduct                2 Unknown
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x40
      (Missing must-be-set bit!)
      Self Powered
    MaxPower              400mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      0 
      iInterface              3 RAM
Device Status:     0x0000
  (Bus Powered)
```


The output on /var/log/messages on disconnect and reconnect is this:
```
Nov 19 11:36:00 raumstation kernel: [17344922.940000] usb 3-2: USB disconnect, address 7
Nov 19 11:36:07 raumstation kernel: [17344930.560000] usb 3-2: new full speed USB device using uhci_hcd and address 8
Nov 19 11:36:08 raumstation kernel: [17344930.720000] usb 3-2: configuration #1 chosen from 1 choice

```


The device should also be class compatible (accourding the the vendor). Is there maybe a way to force linux to treat this a sound device?

---

### Post by davepaque on 2006-11-21
I also use this sound card. If it is your main sound card then you need to edit /etc/modprobe.d/alsa-base and comment out the line options snd-usb-audio index=-2. This allows the soundcard to use hw=0. Also you may need to create an asoundrc.asoundconf in your home directory. 

gedit asoundrc.asoundconf

add this:

pcm.!default {
type hw
card 1
}

ctl.!default {
type hw
card 1
}

---

### Post by sonium on 2006-11-21
I already tried different thing with the loading order and so on. I seems to be problem of the udev rules. I can load the driver manually with

```
sudo madfuload --device=/proc/bus/usb/004/005 -3 -f /usr/local/share/usb/maudio/ma004103.bin
```

unfortunately I'm not experienced writing udev rules.

---

