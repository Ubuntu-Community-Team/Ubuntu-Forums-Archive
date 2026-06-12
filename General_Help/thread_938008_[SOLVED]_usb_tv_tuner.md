---
title: "[SOLVED] usb tv tuner"
date: 2008-10-04
forum: General Help
---

### Post by krauser530 on 2008-10-04
i recently got a pinnacle pctv hd mini stick tuner and i can't get it to work under ubuntu. I plug it in and nothing happens and me-tv doesn't recognize a tuner is plugged in. any suggestions?

---

### Post by hansdown on 2008-10-04
Hi krauser530.

Sorry I don't know much about these, but a google search has a few hits.

[http://www.google.ca/search?q=pinnacle+pctv+hd+mini+stick+tuner+in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=pinnacle+pctv+hd+mini+stick+tuner+in+ubuntu+8.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by oldos2er on 2008-10-04
> **krauser530 said:**
> i recently got a pinnacle pctv hd mini stick tuner and i can't get it to work under ubuntu. I plug it in and nothing happens and me-tv doesn't recognize a tuner is plugged in. any suggestions?

 Plug it in, type "lsusb" in a terminal to see if it's recognized.

---

### Post by krauser530 on 2008-10-05
the results of lsusb are:

Bus 007 Device 002: ID 2304:023f Pinnacle Systems, Inc. [hex] 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

and the results of lsusb -v are:

Bus 007 Device 002: ID 2304:023f Pinnacle Systems, Inc. [hex] 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2304 Pinnacle Systems, Inc. [hex]
  idProduct          0x023f 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ac  1x 940 bytes
        bInterval               1
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

and me-tv gives the error:

No tuner device

---

### Post by krauser530 on 2008-10-05
i tried using tutorials for other sticks that are
similar (like the nanoStick) but they don't seem
to work and I can't find a mini specific one.

here is one such tutorial:
[http://www.smovs.dk/linux/index.php?note=17&subject=Pinnacle%20DVB-T%20nano%20stick%20(PCTV%2073e](http://www.smovs.dk/linux/index.php?note=17&subject=Pinnacle%20DVB-T%20nano%20stick%20(PCTV%2073e))

that one is for the nano 73e stick and mine is a mini 80e

---

### Post by krauser530 on 2008-10-05
I found this [http://www.spinics.net/lists/linux-dvb/msg28888.html](http://www.spinics.net/lists/linux-dvb/msg28888.html), and it seems like theres no DVB support for the 80e. Anyone know what that means? will i just have to wait until someone adds support for it? or is there something else i can do to use it now?

---

### Post by krauser530 on 2008-10-05
I tried using the tuner through a VirtualBox install of XP; however, the stick was not able to be enabled under the USB settings. Is there a way to force VBox to use the device even though it doesn't know what it is?  Windows can take care of the drivers if it has the opportunity.

---

### Post by tharsan on 2008-10-23
hey im actually in the same boat as you.

i've contacted the linux-dvb guys and it looks like this particular card isn't supported yet but there is an effort to get it supported soon.

keep checking the [linuxtv wiki page for the 80e]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_mini_Stick_(80e)") as well the livejournal of devinjh who appears to be the dvb dude working on dvb support for this card!

im anxiously waiting for official support but it should be soon because devin (the dvb dude working on this issue) received tremendous support from Pinnacle on this one ([http://devinjh.livejournal.com/#devinjh148960](http://devinjh.livejournal.com/#devinjh148960))

- T

---

### Post by Fish_Kungfu on 2009-01-02
I just ordered on of these pinnacle pctv hd mini sticks tonight (2009-JAN-02).  I noticed this thread is marked "SOLVED".  Did you guys figure out how to get this to work?  I don't see a clear solution in this thread.

Thanks for starting the thread though!  :)

Cheers....Fish

---

### Post by krauser530 on 2009-01-04
> **Fish_Kungfu said:**
> I just ordered on of these pinnacle pctv hd mini sticks tonight (2009-JAN-02).  I noticed this thread is marked "SOLVED".  Did you guys figure out how to get this to work?  I don't see a clear solution in this thread.

Thanks for starting the thread though!  :)

Cheers....Fish
[It appears that there never may be support in ubuntu]("http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_mini_Stick_(80e)")

---

