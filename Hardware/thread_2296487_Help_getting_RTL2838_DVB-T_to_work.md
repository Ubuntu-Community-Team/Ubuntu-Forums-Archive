---
title: "Help getting RTL2838 DVB-T to work"
date: 2015-09-26
forum: Hardware
---

### Post by mrpg99 on 2015-09-26
Dear Sir/Madam,


   	Since a couple of days ago, my RTL2838 DVB-T stick stopped working. (after upgrading tvheadend)

   	It was still visible as a device in tvheadend, but could not get any service channels (scans stated FAIL)

   	Tested my antenna directly in my tv instead, and the antenna still works, and i can view channels.

   	
I guess its possible that my DVB-T stick has developt a fault, but want to make sure before i fork out money for a new one.

   	In my attempts for remedy this, i compiled and installed the media_build linux tv drivers [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git) 


   	This made things even worse, and i can now no longer see my usb stick in tvheadend at all..

   	

Some details about my stick etc :

   	[12:09:54] mrpg@mediapc:[/opt/media_build]: lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


   	sudo lsusb -s 2:2 -v

   	Bus 002 Device 002: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x2838 RTL2838 DVB-T
  bcdDevice            1.00
  iManufacturer           1 Realtek
  iProduct                2 RTL2838UHIDIR
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 USB2.0-Bulk&Iso
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
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Bulk-In, Interface
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 Bulk-In, Interface
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      2
Device Status:     0x0000
  (Bus Powered)

   	HTS Tvheadend 4.1-433~gd0e7876
   	


Out of desperation, i upgraded the kernel to 4.1.2


and sudo modprobe dvb-usb-rtl28xxu also does not complain, but no card appears under tvheadend.


   	i can see this in dmesg :


   	[    4.009458] **dvb_core: module verification failed: signature and/or required key missing - tainting kernel**
[    4.022408] saa7146: register extension 'budget dvb'
[    4.149405] usb 2-3: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[    4.385520] usb 2-3: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[    4.388603] dvb_usb_rtl28xxu 2-3:1.0: **unknown tuner NONE**
[    4.399729] usbcore: registered new interface driver dvb_usb_rtl28xxu
[    4.529843] budget dvb 0000:07:04.0: DVB: registering adapter 0 frontend 0 (STV090x Multistandard)...
[   11.416162] budget dvb 0000:07:04.0: DVB: adapter 0 frontend 0 frequency 0 out of range (950000..2150000)

   	
i.e it registers my DVB-S2 , but still not my DVB-T card

   	
any help with this is very appriciated!

Br
mrpg

---

### Post by mrpg99 on 2015-09-27
FYI.
   	I got the card to work in this pc in the end (i.e it registerred as a  device in /dev/dvb/ , and i could see it in tvheadend, but it still  fails to get a signal.
   	tested it on another pc, and same problem here, the card is found, but cannot get any signals.
   	also get messages in dmesg that the usb card was successfully  removed from the system from time to time, even though its still very  much inserted into the usb port.
   	So the dongle is broken [IMG]https://tvheadend.org/plugin_assets/redmine_wiki_extensions/images/sad.png[/IMG]
   	Buying a new one [IMG]https://tvheadend.org/plugin_assets/redmine_wiki_extensions/images/smile.png[/IMG]
   	thanks for all the help & suggestions!
   	Br
mrpg

---

