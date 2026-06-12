---
title: "Dana Alphasmart Sync"
date: 2009-09-08
forum: Hardware
---

### Post by didiercool on 2009-09-08
I have a Dana Alphasmart PalmOS and I'm a little lost trying to get it to hotsync.  I'm using jPilot. (is there a better program for this operation?)

When I run > tail -f /var/log/messages and then hotSync from my dana I get:

> Sep  8 15:16:01 Small kernel: [  562.288789] usb 2-2: configuration #1 chosen from 1 choice


Every time I attempt to hotSync, I get the following error:

> Syncing on device /dev/ttyusb1
Press the HotSync button now
****************************************
pi_bind error: /dev/ttyusb1 No such file or directory
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

I've employed all of the following sources in my effort:
[http://ubuntuforums.org/archive/index.php/t-351029.html](http://ubuntuforums.org/archive/index.php/t-351029.html)
[http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html#GNOME-PILOT](http://www.faqs.org/docs/Linux-HOWTO/PalmOS-HOWTO.html#GNOME-PILOT)
[http://ubuntuforums.org/showthread.php?t=334942&highlight=alphasmart](http://ubuntuforums.org/showthread.php?t=334942&highlight=alphasmart)
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

But none of the above solutions have worked for me.

lsusb -v produces the follow info on the dana:

> Bus 002 Device 010: ID 081e:df00 AlphaSmart, Inc. Handheld
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x081e AlphaSmart, Inc.
  idProduct          0xdf00 Handheld
  bcdDevice            1.00
  iManufacturer           1 AlphaSmart, Inc.
  iProduct                2 Palm Handheld
  iSerial                 5 PalmSN12345678
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

:confused: Does anyone have any suggestions?  Any help would be much appreciated!!

Thanks for reading this far. :KS

---

### Post by semjaza on 2011-07-22
I had to follow the directions here [http://www.pilot-link.org/README.usb]("http://www.pilot-link.org/README.usb") hope it helps.

---

### Post by didiercool on 2011-07-22
FINALLY!!  I'll have to dig out my Dana and see if this works!!  Thank you!!  I had lost all hope.

---

### Post by Dana Alpha-male on 2011-07-24
Edited to add: I'm using the pilot-link package on the command line. Haven't tried Jpilot yet!

The above link didn't seem to have any specific AlphaSmart data in it.

What I did was search the pilot-link mailing list, where I came upon this message regarding the Centro:

[http://lists.pilot-link.org/pipermail/pilot-link-general/2008-July/003423.html](http://lists.pilot-link.org/pipermail/pilot-link-general/2008-July/003423.html)

anyway, they say to use:

pilot-xfer -l -p usb:

so I disconnected my Zire 72 (it was charging from USB) and hit
(function)+(send sync) on the Alpha. The "-l" command is pretty harmless, 
it should just list all the databases installed on the Dana. 

The " -p usb: " part seems completely undocumented. It appears that the
pilot-link man page has not been updated since 2007.

anyway, long-short is that it worked.  

type " pilot-xfer -l -p usb: "  (but don't press return)
hit the sync key on the alpha, 
wait 2 seconds
and then press (return)

This worked as a non-root user, and I am successfully syncing with my 
Zire72 already, so I know that `modprobe visor` is successfully loaded
and syncing with that device already.

I'd also want to remind you that the Dana AlphaSmart can act like a USB 
keyboard, and sometimes seems to be stuck in that mode. if that's the 
case you can try a soft reboot.

Normally I just connect a palm device and look in dmesg or tailf 
/var/log/messages to find the port ( like /dev/ttyUSB1 ) but that didn't 
work w/ the Alpha.

once you get the above command working, read the pilot-xfer man page to 
learn how to install apps or sync the device.

---

### Post by Dana Alpha-male on 2011-07-24
Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=334942](http://ubuntuforums.org/showthread.php?t=334942)

jpilot uses pilot-link for it's backend so I suppose in jpilot it's File :: references :: settings 

and change the serial port field to "usb:" (drop down menu, cool!)

I want to back up my data first before I try this as I don't want to corrupt my zire72 data.

---

### Post by Dana Alpha-male on 2011-07-24
The other thread (it's locked I presume), noted above has the link:

([http://jasonday.home.att.net]("http://jasonday.home.att.net/"))

which is dead, but wayback lead me to here:

[http://www.jlogday.com/code/jpilot-backup/](http://www.jlogday.com/code/jpilot-backup/)

just in case you want to try that plugin.

---

