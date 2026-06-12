---
title: "Connect a Nokia Phone trough USB IrDa Problems."
date: 2009-05-29
forum: Hardware
---

### Post by sitmex on 2009-05-29
-just for those, asking, yes! I've read previous posts, back from 2006/2007 but no luck.

Hi, Good Day..

So I have this phone, a Nokia 6131, and the only way to connect it to a computer is via infrared. so I plug an USB IrDa device and this is what I got:

```
May 29 19:36:05 Casa kernel: [116905.385645] pl2303 ttyUSB1: pl2303 converter now disconnected from ttyUSB1
May 29 19:36:05 Casa kernel: [116905.385658] pl2303 7-2:1.0: device disconnected
May 29 19:36:13 Casa kernel: [116913.128017] usb 7-1: new full speed USB device using uhci_hcd and address 7
May 29 19:36:13 Casa kernel: [116913.289482] usb 7-1: configuration #1 chosen from 1 choice
May 29 19:36:13 Casa kernel: [116913.291614] pl2303 7-1:1.0: pl2303 converter detected
May 29 19:36:13 Casa kernel: [116913.303631] usb 7-1: pl2303 converter now attached to ttyUSB0

```

when I did lsusb this is what I got:
```
Bus 007 Device 005: ID 0df7:0620 Mobile Action Technology, Inc. MA-620 Infrared Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0df7 Mobile Action Technology, Inc.
  idProduct          0x0620 MA-620 Infrared Adapter
  bcdDevice            3.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0

```

I've tried to install irda-utils, but no luck, I've got an install error.
```
Setting up irda-utils (0.9.18-8.1ubuntu1) ...
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.
/var/lib/dpkg/info/irda-utils.postinst: line 92: update-modules: command not found
dpkg: error processing irda-utils (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ircp-tray:
 ircp-tray depends on irda-utils; however:
  Package irda-utils is not configured yet.
dpkg: error processing ircp-tray (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 irda-utils
 ircp-tray
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now, How can I make it work? (both irda-utils and the phone to be detected?)

What Am I doing wrong?

Thanks in advance for your help! (if you need more info about the environment/computer, components, etc I have, please do not hesitate, and Ask!) 

```
Linux Casa 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux Ubuntu 9.04 - The Jaunty Jackalope

```

---

### Post by moster on 2009-06-07
Half world away in middle europe I have that same JUNK ma620 IR controller. I do not know who made those but it spread this crap across whole world.

This hardware work in winXP and pain in the *** in ubuntu but it is possible. Quick fix in future is install Winxp in virtualbox and there is going to work always.... Back on linux.

Ok.. I get this infrared USB MA-620 to work in jaunty x86

What you need to do is enable "Pre-released updates (jaunty proposed) in menu system/administration/software sources tab "updates". It will allow you to update compatible irda-utils, just go update your computer and select only this.

Next "sudo gedit /etc/default/irda-utils"
Modify this file to look like this
/.
ENABLE="true"

AUTOMATIC="true"

DISCOVERY="true"

DEVICE="/dev/ttyUSB0"

DONGLE="ma600"

SETSERIAL=""
./

Next edit "sudo gedit /etc/modules"
and just add new line on bottom "irda" (without quotes)

Next.. this is probably not necessary and will give you some error but it wont hurt so you do that too 
sudo /etc/init.d/irda-utils start

sudo apt-get install openobex-apps

Next, restart computer and open terminal and write "irxfer"
It will say "waiting for file or something like that"... now you can send whatewer you want from phone. It will say "unknown event", but do not worry. It will land in your home directory.

---

