---
title: "[SOLVED] USB Parallel Printer Cable Setup"
date: 2008-08-19
forum: Hardware
---

### Post by Rayaz on 2008-08-19
Hi all, have been trying to install an HP Laserjet 4000 printer using an USB to Parallel Cable with  no success. lsusb outputs  Cypress Technologies usb connector. My system is a Compaq Presario Laptop, 1.7 GHz Celeron M, 1.5 Gb RAM, 80 GB HDD. I am running Hardy 8.04, latest kernel. TIA

---

### Post by Rayaz on 2008-08-21
Anyone?

---

### Post by Rayaz on 2008-08-23
Anyone? Please!

---

### Post by Rayaz on 2008-08-23
Hey guys, 75 views and still nothing? Should I post somewhere else?

---

### Post by Rayaz on 2008-08-25
Give it up as a bad job?

---

### Post by Rayaz on 2008-09-01
If this issue doesn't get sorted out, I guess it'll be back to dear old windows:(

---

### Post by Rayaz on 2008-09-05
dmesg output:


[ 2836.692309] usblp0: removed
[ 2836.692321] /build/buildd/linux-2.6.24/drivers/usb/core/message.c: selecting invalid altsetting 0
[ 2845.862758] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 2846.019632] usb 1-1: config 1 has an invalid descriptor of length 26, skipping remainder of the config
[ 2846.019667] usb 1-1: config 1 interface 0 has no altsetting 0
[ 2846.042923] usb 1-1: configuration #1 chosen from 1 choice
[ 2846.075960] usblp0: USB Bidirectional printer dev 7 if 0 alt 2 proto 2 vid 0x04B4 pid 0x4100


cat /proc/bus/usb/devices output:


T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=04b4 ProdID=4100 Rev= 0.02
S:  Product=USB PRINT   
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 2 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms


lsusb -v output:
Bus 001 Device 007: ID 04b4:4100 Cypress Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x04b4 Cypress Semiconductor Corp.
  idProduct          0x4100 
  bcdDevice            0.02
  iManufacturer           1 
  iProduct                2 USB PRINT   
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           50
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 25 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
        ** UNRECOGNIZED:  04 03 09 04
        ** UNRECOGNIZED:  24 49 64 3a 20 75 73 11 00 00 00 00 92 05 08 01 00 00 00 00 00 00 00 21 00 00 00 09 04 00 02 02 07 01 02 00
cannot read device status, Broken pipe (32)

---

### Post by Rayaz on 2008-09-13
Ok guys, managed to get it up and running using a cross-over lan cable with a static IP address. Yeaah!

---

### Post by Rhubarb on 2008-09-13
> **Rayaz said:**
> Ok guys, managed to get it up and running using a cross-over lan cable with a static IP address. Yeaah!

Good to hear Rayaz, my only other suggestion would be to get a PCI to parallel card / get a usb printer (they're cheap anyway).
But I confess, I don't know much about usb -> parallel converters, I only know some usb -> serial stuff.
Glad to hear you got it going anyway :)

---

### Post by UsedBits on 2009-11-17
I, too, am using a USB->Parallel adaptor with which to connect a parallel printer, an HP LaserJet 4L.  All seems to go fine except for one thing - the system can never actually find a printer device.  Just like the original poster of this thread,  lsusb outputs Cypress Technologies usb connector for the port to which the adaptor is connected.
 
Each time a setup program tries to find the printer, nothing can be found.
 
I'm beginning to think it isn't possible, i.e. that Ubuntu 9.10 isn't capable of seeing a parallel printer 'hidden' behind a USB->Parallel adaptor.
 
All help, suggestions, or ideas are welcome.

---

### Post by thodges999 on 2009-12-02
I too have been wrestling with this problem and have found a solution elsewhere on the web which worked for me. [[COLOR="Red"]See here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/461020") 

I'm using a Prolific PL2305 USB-Parallel Port connector and a LaserJet 4 printer.

If you do System, Admin, Printing and then install a new printer of your model using one of the serial ports. On completion don't print a test page but go to the properties of the newly installed printer and change the device url to parallel:/dev/usb/lp0. Your printer will hopefully now work!
Trevor

---

### Post by thodges999 on 2009-12-02
I forgot to mention I'm using Karmic Koala 9.10

---

### Post by __tom__ on 2009-12-17
Terrific! This also worked with my cheapie no name USB to Parallel connector with a Laserjet 4L! I was getting nowhere and it was so good to see it suddenly start printing! Thank you!:KS

---

### Post by UsedBits on 2010-01-05
> **__tom__ said:**
> Terrific! This also worked with my cheapie no name USB to Parallel connector with a Laserjet 4L! I was getting nowhere and it was so good to see it suddenly start printing! Thank you!:KS

What?  What worked to get your no name connector to connect the parallel printer through a USB port?

I tried the uri:parallel:/dev/usb/lp0, but it didn't work.  Would someone walk through all of the steps to make this technique work, i.e. steps to configure a printer with this trick?

---

### Post by thodges999 on 2010-01-06
> **UsedBits said:**
> What?  What worked to get your no name connector to connect the parallel printer through a USB port?

I tried the uri:parallel:/dev/usb/lp0, but it didn't work.  Would someone walk through all of the steps to make this technique work, i.e. steps to configure a printer with this trick?

What worked for me was as follows;
1. Select System, Admin, Printing from the menu
2. Press New and when the dialogue box comes up for New Printer press forward and then select your printer (HP LJ4 in my case). I know this will not be for a USB connection but we'll fix that later.
3. Once you have selected your printer driver press Apply and when asked if you want to print a test page select No.
4. Now you have your printer driver installed you should see it in the Printer Configuration window. Right click on it and select properties.
5. Change the Device URL to parallel:/dev/usb/lp0 and press Apply.

Thats it and it worked for me and others. If this fails please post the results of running lsusb in Terminal.

---

### Post by UsedBits on 2010-01-06
I believe there is no /dev/usb/lp0 on my box.  In fact, I think there is no /dev/usb at all.  It is what I think is the root of many of the problems, i.e. that 9.10 has no usb/lp0 definition.
 
I'd like to try your technique (changing the device URI to parallel:) with whatever 9.10 has decided it will call my usb parallel port.  Will let y'all know this evening.

---

### Post by thodges999 on 2010-01-06
I believe you are correct that there is no /dev/usb/lp0 which is why you have to put it in yourself after installing the printer on one of the outputs that are available (in my case serial port #1)

I can't claim to understand how it works technically but it worked for me, hopefully it does for you as well.

---

### Post by UsedBits on 2010-01-06
> **thodges999 said:**
> I believe you are correct that there is no /dev/usb/lp0 which is why you have to put it in yourself after installing the printer on one of the outputs that are available (in my case serial port #1)

 
Please forgive my inablilty to ferrot out the details of your reply.
 
We both agree there is no /dev/usb/lp0. But when you say "put it in yourself", are you referring simply to entering it into the printer URI field? Or are you suggesting that we have to somehow create /dev/usb/lp0 on the filesystem?
 
Also, when you refer to "serial port #1", my confusion is because the suggested :URI contains 'parallel', and we're talking about USB in the first place. Where did the serial port come into play?
 
Although I've encountered unix since the mid-80s and Linux when it first appeared in the early 90s, I'm far from comfortable with working at this level of detail. In fact, my quest right now is to see if I can live at home in a MS Windows-less environment, but I've already compromised by running Quicken with wine and suspect that a virtual Windows box will need to be created.

---

### Post by thodges999 on 2010-01-06
> **UsedBits said:**
> Please forgive my inablilty to ferrot out the details of your reply.
 
We both agree there is no /dev/usb/lp0. But when you say "put it in yourself", are you referring simply to entering it into the printer URI field? Or are you suggesting that we have to somehow create /dev/usb/lp0 on the filesystem?
 
Also, when you refer to "serial port #1", my confusion is because the suggested :URI contains 'parallel', and we're talking about USB in the first place. Where did the serial port come into play?
 
Although I've encountered unix since the mid-80s and Linux when it first appeared in the early 90s, I'm far from comfortable with working at this level of detail. In fact, my quest right now is to see if I can live at home in a MS Windows-less environment, but I've already compromised by running Quicken with wine and suspect that a virtual Windows box will need to be created.

If you follow my suggestion (four posts above) as follows;

'What worked for me was as follows;
1. Select System, Admin, Printing from the menu
2. Press New and when the dialogue box comes up for New Printer press forward and then select your printer (HP LJ4 in my case). I know this will not be for a USB connection but we'll fix that later.
3. Once you have selected your printer driver press Apply and when asked if you want to print a test page select No.
4. Now you have your printer driver installed you should see it in the Printer Configuration window. Right click on it and select properties.
5. Change the Device URL to parallel:/dev/usb/lp0 and press Apply.'

when you get to step 2 the dialogue box has a list of devices on the left hand side. What would be perfect would be to have your usb to parallel adapter listed here but it isn't. Instead select any other device (in my case serial port #1 but it doesn't matter) and continue to follow the instructions.

Then at step 5, yes you simply type in the device url as stated and thats it.

I now use Ubuntu for the majority of the time with a Windows virtual box to run some proprietary Windows programs that I can't find Linux replacements for. Ubuntu can require more technical input for some items like this USB/parallel adapter or in my case using a Brother scanner.

However I've found the Ubuntu community very helpful and knowledgeable and have solved all my problems to date, which haven't been that many. I also have to say I've had some pretty odd 'challenges' from Windows over the years so its far from perfect as you probably already know.

Good luck

---

### Post by UsedBits on 2010-01-06
ok - followed your instructions almost exactly.  When creating the new printer, I chose 'parallel' instead of 'serial'.  Then, when modifying the URI, all I had to do was add /usb to end up with "parallel:/dev/usb/lp0".  I also made this the default printer.

Next I then attempted to print a test page.  I get the same results as with all my other attempts: the print job hits the queue, but a short while later an error message appears saying the printer might not be connected.

I truly believe this is caused by there being no physical /dev/usb/lp0 device.  If only I could figure out what defined device to use (as found on my system), I think we could move one step closer to solving this.

Oh, one more thing. When my system boots, part of the POST message briefly flashes that it has found 2 USB devices - a keyboard and a mouse.  But no printer.  I don't know if those who can successfully print see when their machine boots and displays its POST messages.

---

### Post by thodges999 on 2010-01-07
If you are seeing a parallel device when setting up your printer I assume you have a parallel port? Is that so as this may cause a different problem.

I don't which is why I am using a USB/parallel adapter so I can't check if it works the same as my suggestion.

What other devices do you have listed in step 2 dialogue box?

I have noticed in my list I have 'Other' and if I use that I can then enter the URL direct and this also gives me a working printer.

Can you post the output of lsusb and dmesg | grep -i usb

Regards

---

### Post by thodges999 on 2010-01-07
I think I was wrong that usblp0 didn't exist on my machine before I installed my printer.

I tried uninstalling the printer and rebooting. Checking with dmesg | grep -i usb I still have it!

---

### Post by UsedBits on 2010-01-08
I'm close to giving up.  The problem seems to be that my system doesn't 'see' that I have a printer behind a USB port.  Lots of stuff about that when they were building 9.10 but it was considered not a showstopper.  Many folks can't print as a result.

---

### Post by thodges999 on 2010-01-08
I like several other people have managed to solve this problem although it is very frustrating.

I'm happy to help (if I can) but I need the answers to my questions in my post 21 (3 above)

---

### Post by UsedBits on 2010-01-08
> **thodges999 said:**
> If you are seeing a parallel device when setting up your printer I assume you have a parallel port? Is that so as this may cause a different problem.

I don't which is why I am using a USB/parallel adapter so I can't check if it works the same as my suggestion.

What other devices do you have listed in step 2 dialogue box?

I have noticed in my list I have 'Other' and if I use that I can then enter the URL direct and this also gives me a working printer.

Can you post the output of lsusb and dmesg | grep -i usb

Regards

When adding a new printer via hp-toolbox, three printer types are shown: Parallel, serial, and other.  Strange thing is that I don't have a parallel port on the system.  (Could it be that it is seeing the Laserjet behind the USB converter?)

lsusb:
Bus 003 Device 002: ID 04b4:4100 Cypress Semiconductor Corp.

Here is what I think are what I think the important parts of dmesg:

[    2.064955] usbcore: registered new interface driver hiddev
[    2.070402] input: Composite USB PS2 Converter USB to PS2 Adaptor  V3.10 as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.0/input/input4
[    2.070461] generic-usb 0003:0B39:0001.0001: input,hidraw0: USB HID v1.10 Keyboard [Composite USB PS2 Converter USB to PS2 Adaptor  V3.10] on usb-0000:00:04.0-3/input0
[    2.079441] input: Composite USB PS2 Converter USB to PS2 Adaptor  V3.10 as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.1/input/input5
[    2.079488] generic-usb 0003:0B39:0001.0002: input,hidraw1: USB HID v1.10 Mouse [Composite USB PS2 Converter USB to PS2 Adaptor  V3.10] on usb-0000:00:04.0-3/input1
[    2.079499] usbcore: registered new interface driver usbhid
[    2.079502] usbhid: v2.6:USB HID core driver
[    2.141367] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:d4:bd:72
[    2.141371] forcedeth 0000:00:0a.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    2.313806] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    2.527285] usb 3-2: config 1 has an invalid descriptor of length 26, skipping remainder of the config
[    2.527290] usb 3-2: config 1 interface 0 has no altsetting 0
[    2.551362] usb 3-2: configuration #1 chosen from 1 choice
[    2.554290] usb 3-2: can't set config #1, error -32

[   11.459565] type=1505 audit(1262929400.779:19): operation="profile_replace" pid=1006 name=/usr/lib/cups/backend/cups-pdf
[   11.463299] type=1505 audit(1262929400.779:20): operation="profile_replace" pid=1006 name=/usr/sbin/cupsd

---

### Post by thodges999 on 2010-01-08
I see you are using hp-toolbox to install your printer so I cannot replicate your steps.

If you try to install the printer using the Ubuntu built in system as my earlier suggestions this will allow us to compare notes. If you do this what other devices do you have listed in step 2 dialogue box?

Could you give the full listing from lsusb so I can compare it with the output from dmesg | grep -i usb.

Is your listing from dmesg the full output from running 'dmesg | grep -i usb'?

Unfortunately I'm off line for a couple of weeks from tomorrow so apologies if any response is delayed.

---

### Post by UsedBits on 2010-01-08
Many thanks for your help.  I'm at work now, my Linux box is at home.  The output provided is what I believed to be the pertanent parts, i.e. there is a USB mouse in addition to the USB printer.
 
Something interrupts the system from identifying the printer.  This is shown with other commands, like lsusb -vvv, for example.  I've posted this output in other places/forums/bugs, so a google search of "UsedBits usb" might find them if you'd like to see them in short order.
 
Once the system sees the printer, I'm certain that it will be configurable to print.
 
If you aren't using hp-toolbox, what, then, are you using?

---

### Post by thodges999 on 2010-01-08
Hi
I've just seen your fuller postings on Ubuntu Bugs and the output from lsusb -vvv shows 'cannot read device status, Broken pipe (32)' at the end of your Cypress Semiconductor section.

I guess this is what is causing your problem and currently I have no idea why although it may be to do with one of those random glitches that software sometimes plays on us or maybe the hardware is faulty.

A reinstall may be one solution but I don't suppose this is preferred, the other would be to run Ubuntu from a liveCD and see if this then works, at least you will know then that it is software related and soluble.

---

### Post by thodges999 on 2010-01-08
> **UsedBits said:**
> Many thanks for your help.  I'm at work now, my Linux box is at home.  The output provided is what I believed to be the pertanent parts, i.e. there is a USB mouse in addition to the USB printer.
 
Something interrupts the system from identifying the printer.  This is shown with other commands, like lsusb -vvv, for example.  I've posted this output in other places/forums/bugs, so a google search of "UsedBits usb" might find them if you'd like to see them in short order.
 
Once the system sees the printer, I'm certain that it will be configurable to print.
 
If you aren't using hp-toolbox, what, then, are you using?

Our responses crossed and I have found your other postings.

To install a printer I use System, Administration, Printing from the menu bar at the top of the screen as my original post. I use this for both HP and non HP printers.

---

### Post by scarpent on 2010-01-12
Finally! I expected this to be fairly simple but had to struggle a bit before finally finding this thread.

Device URI: parallel:/dev/usb/lp0

Did the trick for me.  In the meantime I installed a bunch of stuff suggested by hp-check, and also the hp-toolbox via hplip-gui.  Hard to say if any of that was necessary -- I suspect now that parallel:/dev/usb/lp0 would have had me running right away.

For reference, I'm running 64-bit 9.10 Karmic with an HP LaserJet 6L.  I bought a 6' Sabrent "USB to DB25 Female Parallel Printer Cable".

Further reference, lsusb doesn't seem to show anything for this connection, but it's all good now.

Thanks, thodges999!  The joy of getting it to work almost made up for the pain of banging my head against the wall for an hour or two.

---

### Post by yuanchao on 2010-02-06
I'm having the same problem with Cypress USB Parallel Printer Cable (04b4:4100). Since Ubuntu 9.04, it can't be recognized therefore usblp is not automatically loaded. On 9.10, it's even not listed with 'lsusb -v'. The kernel message shows as the following:

```

[ 7693.032561] usb 4-2: new full speed USB device using ohci_hcd and address 5
[ 7693.236026] usb 4-2: config 1 has an invalid descriptor of length 26, skipping remainder of the config
[ 7693.236039] usb 4-2: config 1 interface 0 has no altsetting 0
[ 7693.260214] usb 4-2: configuration #1 chosen from 1 choice
[ 7693.265380] usb 4-2: can't set config #1, error -32

```

With manually loads 'usblp' and create a device node via 'sudo /bin/mknod /dev/usblp0 c 180 0', now I can finally print through it. (surely, use 'parallel:/dev/usblp0' in CUPS)

So my question is how should I report this bug such that it can be fixed in the new release? I've tried on Fedora 7 and 11 before and both have no problem recognize this device. (usblp automatically loaded and /dev/usb/lp0 created)

---

### Post by moth17 on 2010-03-06
> **thodges999 said:**
> What worked for me was as follows;
1. Select System, Admin, Printing from the menu
2. Press New and when the dialogue box comes up for New Printer press forward and then select your printer (HP LJ4 in my case). I know this will not be for a USB connection but we'll fix that later.
3. Once you have selected your printer driver press Apply and when asked if you want to print a test page select No.
4. Now you have your printer driver installed you should see it in the Printer Configuration window. Right click on it and select properties.
5. Change the Device URL to parallel:/dev/usb/lp0 and press Apply.

Thats it and it worked for me and others. If this fails please post the results of running lsusb in Terminal.


I can't get this to fly either. I'm relatively new to Ubuntu, but I was able to follow this. It's not working for me either. Why is this thread marked Solved? Do I just have a rectal-cranial inversion?](*,)

---

### Post by moth17 on 2010-03-06
Is this useful, or did I just make a mess here??


Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest HP-Deskjet-960c>,
 'cups_instance': None,
 'cups_queue': 'HP-Deskjet-960c',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/usb/lp0',
                       'printer-info': u'HP Deskjet 960c',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP Deskjet 960c hpijs, 3.9.8',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8425500,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP-Deskjet-960c'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.1',
                                 'device-uri': u'parallel:/dev/usb/lp0',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'iso_a6_105x148mm',
                                                     u'jis_b5_182x257mm',
                                                     u'adobe_CDDVD80_83.6083x83.6083mm',
                                                     u'adobe_CDDVD120_5x5in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_legal_8.5x14in',
                                                     u'jpn_oufuku_148x200mm',
                                                     u'roc_16k_7.75x10.75in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'custom_min_1x4in',
                                                     u'custom_max_13x19in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'HP Deskjet 960c',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'',
                                 'printer-make-and-model': u'HP Deskjet 960c hpijs, 3.9.8',
                                 'printer-more-info': u'http://localhost:631/printers/HP-Deskjet-960c',
                                 'printer-name': u'HP-Deskjet-960c',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1267863413,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8425500,
                                 'printer-up-time': 1267863739,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/HP-Deskjet-960c'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': False,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'DryTime': u'Zero',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 263782L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': '06/Mar/2010:00:23:37 +0000',
 'test_page_job_id': [34],
 'test_page_job_status': [(True,
                           34,
                           'HP-Deskjet-960c',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 34,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/34',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'hafiz',
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'connecting-to-device'],
                            'job-printer-up-time': 1267863829,
                            'job-printer-uri': u'ipp://hafiz-desktop:0/printers/HP-Deskjet-960c',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/34',
                            'job-uuid': u'urn:uuid:c9fb36cd-b6f3-37f4-69f8-e81f438ad54e',
                            'printer-uri': u'ipp://localhost/printers/HP-Deskjet-960c',
                            'time-at-completed': None,
                            'time-at-creation': 1267863817,
                            'time-at-processing': 1267863817})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Printing jobs',
               'D [06/Mar/2010:00:23:31 -0800] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Active clients and printing jobs',
               'D [06/Mar/2010:00:23:31 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:31 -0800] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [06/Mar/2010:00:23:31 -0800] Get-Jobs ipp://localhost/printers/',
               'D [06/Mar/2010:00:23:31 -0800] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Printing jobs',
               'D [06/Mar/2010:00:23:31 -0800] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Active clients and printing jobs',
               'D [06/Mar/2010:00:23:31 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:31 -0800] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [06/Mar/2010:00:23:31 -0800] Get-Jobs ipp://localhost/printers/',
               'D [06/Mar/2010:00:23:31 -0800] [Job 1] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 2] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 3] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 4] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 5] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 6] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 7] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 8] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 9] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 10] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 11] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 12] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 13] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 14] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 15] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 16] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 17] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 18] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 19] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 20] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 21] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 22] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 23] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 24] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 25] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 26] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 27] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 28] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 29] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 30] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 31] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] [Job 32] Loading attributes...',
               'D [06/Mar/2010:00:23:31 -0800] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Printing jobs',
               'D [06/Mar/2010:00:23:31 -0800] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Active clients and printing jobs',
               'D [06/Mar/2010:00:23:31 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:31 -0800] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1',
               'D [06/Mar/2010:00:23:31 -0800] Create-Printer-Subscription /',
               'D [06/Mar/2010:00:23:31 -0800] cupsdCreateSubscription(con=0x222d60d0(12), uri="/")',
               'D [06/Mar/2010:00:23:31 -0800] pullmethod="ippget"',
               'D [06/Mar/2010:00:23:31 -0800] notify-lease-duration=86400',
               'D [06/Mar/2010:00:23:31 -0800] notify-time-interval=0',
               'D [06/Mar/2010:00:23:31 -0800] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [06/Mar/2010:00:23:31 -0800] Added subscription 158 for server',
               'D [06/Mar/2010:00:23:31 -0800] cupsdMarkDirty(-----S)',
               'D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:31 -0800] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [06/Mar/2010:00:23:31 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:32 -0800] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:32 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:32 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:32 -0800] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [06/Mar/2010:00:23:32 -0800] Get-Notifications /',
               'D [06/Mar/2010:00:23:32 -0800] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [06/Mar/2010:00:23:32 -0800] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [06/Mar/2010:00:23:32 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 14 POST /printers/HP-Deskjet-960c HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 14 1.1 Print-Job 1',
               'D [06/Mar/2010:00:23:37 -0800] Print-Job ipp://localhost/printers/HP-Deskjet-960c',
               'D [06/Mar/2010:00:23:37 -0800] [Job ???] Auto-typing file...',
               'I [06/Mar/2010:00:23:37 -0800] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(----J-)',
               'D [06/Mar/2010:00:23:37 -0800] add_job: requesting-user-name="hafiz"',
               'D [06/Mar/2010:00:23:37 -0800] Adding default job-sheets values "none,none"...',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Adding start banner page "none".',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(-----S)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(----J-)',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Adding end banner page "none".',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] File of type application/vnd.cups-banner queued by "hafiz".',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] hold_until=0',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Queued on "HP-Deskjet-960c" by "hafiz".',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(----J-)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(-----S)',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] job-sheets=none,none',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] argv[0]="HP-Deskjet-960c"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] argv[1]="34"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] argv[2]="hafiz"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] argv[3]="Test Page"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] argv[4]="1"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] argv[5]="job-uuid=urn:uuid:c9fb36cd-b6f3-37f4-69f8-e81f438ad54e job-originating-host-name=localhost"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] argv[6]="/var/spool/cups/d00034-001"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[10]="SERVER_ADMIN=root@hafiz-desktop"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[11]="SOFTWARE=CUPS/1.4.1"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[13]="TZ=America/Los_Angeles"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[14]="USER=root"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[17]="IPP_PORT=631"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[18]="CHARSET=utf-8"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[19]="LANG=en_US.UTF-8"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[20]="PPD=/etc/cups/ppd/HP-Deskjet-960c.ppd"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[21]="RIP_MAX_CACHE=512780k"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[24]="PRINTER_INFO=HP Deskjet 960c"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[25]="PRINTER_LOCATION="',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[26]="PRINTER=HP-Deskjet-960c"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[27]="CUPS_FILETYPE=document"',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] envp[28]="FINAL_CONTENT_TYPE=printer/HP-Deskjet-960c"',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Started filter /usr/lib/cups/filter/bannertops (PID 2520)',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Started filter /usr/lib/cups/filter/pstopdf (PID 2521)',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Started filter /usr/lib/cups/filter/pdftopdf (PID 2522)',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Started filter /usr/lib/cups/filter/foomatic-rip (PID 2525)',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Started backend /usr/lib/cups/backend/parallel (PID 2529)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(-----S)',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-Deskjet-960c) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] PID 2520 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] load_banner(filename="/var/spool/cups/d00034-001")',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Page = 612x792; 18,36 to 594,783',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] pstopdf 5 args: 34 hafiz Test Page 1 job-uuid=urn:uuid:c9fb36cd-b6f3-37f4-69f8-e81f438ad54e job-originating-host-name=localhost',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] PPD: /etc/cups/ppd/HP-Deskjet-960c.ppd',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Getting input from file',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] foomatic-rip version 4.0.3.215 running...',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Parsing PPD file ...',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option Resolution',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option PageSize',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option Model',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option PrintoutMode',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option InputSlot',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option Duplex',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option DryTime',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option Quality',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option ImageableArea',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option PaperDimension',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Added option Font',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34]',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Parameter Summary',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] -----------------',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34]',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Spooler: cups',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Printer: HP-Deskjet-960c',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Shell: /bin/bash',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] PPD file: /etc/cups/ppd/HP-Deskjet-960c.ppd',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] ATTR file:',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Printer model: HP Deskjet 960c hpijs, 3.9.8',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Job title: Test Page',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] File(s) to be printed:',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] <STDIN>',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34]',
               "D [06/Mar/2010:00:23:37 -0800] [Job 34] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Printing system options:',
               "D [06/Mar/2010:00:23:37 -0800] [Job 34] Pondering option 'job-uuid=urn:uuid:c9fb36cd-b6f3-37f4-69f8-e81f438ad54e'",
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Unknown option job-uuid=urn:uuid:c9fb36cd-b6f3-37f4-69f8-e81f438ad54e.',
               "D [06/Mar/2010:00:23:37 -0800] [Job 34] Pondering option 'job-originating-host-name=localhost'",
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Unknown option job-originating-host-name=localhost.',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Options from the PPD file:',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34]',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] ================================================',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34]',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] File: <STDIN>',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34]',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] ================================================',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34]',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] STATE: +connecting-to-device',
               'I [06/Mar/2010:00:23:37 -0800] [Job 34] Printer busy; will retry in 30 seconds...',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(-----S)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdMarkDirty(-----S)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Resolution: 1200',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Page size: Letter',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Width: 612, height: 792, absolute margins: 18, 36, 594, 783',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Relative margins: 18, 36, 18, 9',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] PPD options: -r1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] PostScript to be injected:',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dDoNumCopies -r1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [06/Mar/2010:00:23:37 -0800] [Job 34] GPL Ghostscript 8.70: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [06/Mar/2010:00:23:37 -0800] Get-Jobs ipp://localhost/printers/',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [06/Mar/2010:00:23:37 -0800] cupsdCloseClient: 17',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [06/Mar/2010:00:23:37 -0800] Get-Notifications /',
               'D [06/Mar/2010:00:23:37 -0800] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 1.1 Get-Job-Attributes 1',
               'D [06/Mar/2010:00:23:37 -0800] Get-Job-Attributes ipp://localhost/jobs/34',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/34) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 1.1 Get-Notifications 1',
               'D [06/Mar/2010:00:23:37 -0800] Get-Notifications /',
               'D [06/Mar/2010:00:23:37 -0800] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 WAITING Closing on EOF',
               'D [06/Mar/2010:00:23:37 -0800] cupsdCloseClient: 18',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAcceptClient: 18 from localhost (Domain)',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [06/Mar/2010:00:23:37 -0800] Get-Notifications /',
               'D [06/Mar/2010:00:23:37 -0800] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1',
               'D [06/Mar/2010:00:23:37 -0800] CUPS-Get-Printers',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [06/Mar/2010:00:23:37 -0800] cupsdCloseClient: 17',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1',
               'D [06/Mar/2010:00:23:37 -0800] CUPS-Get-Classes',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 1.1 CUPS-Get-Default 1',
               'D [06/Mar/2010:00:23:37 -0800] CUPS-Get-Default',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 1.1 CUPS-Get-Printers 1',
               'D [06/Mar/2010:00:23:37 -0800] CUPS-Get-Printers',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 1.1 CUPS-Get-Classes 1',
               'D [06/Mar/2010:00:23:37 -0800] CUPS-Get-Classes',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:37 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:37 -0800] cupsdReadClient: 18 1.1 CUPS-Get-Default 1',
               'D [06/Mar/2010:00:23:37 -0800] CUPS-Get-Default',
               'D [06/Mar/2010:00:23:37 -0800] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [06/Mar/2010:00:23:37 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:38 -0800] PID 2521 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] Filetype: PDF',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] Storing temporary files in /var/spool/cups/tmp',
               'D [06/Mar/2010:00:23:38 -0800] PID 2522 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] File contains 1 pages',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="DESKJET 990" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-Tk5MDx',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] Starting process "kid3" (generation 1)',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] Starting process "kid4" (generation 2)',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] JCL: \x1b%-12345X@PJL',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] <job data>',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34]',
               'D [06/Mar/2010:00:23:38 -0800] [Job 34] Starting process "renderer" (generation 2)',
               'D [06/Mar/2010:00:23:39 -0800] Report: clients=3',
               'D [06/Mar/2010:00:23:39 -0800] Report: jobs=34',
               'D [06/Mar/2010:00:23:39 -0800] Report: jobs-active=2',
               'D [06/Mar/2010:00:23:39 -0800] Report: printers=2',
               'D [06/Mar/2010:00:23:39 -0800] Report: printers-implicit=0',
               'D [06/Mar/2010:00:23:39 -0800] Report: stringpool-string-count=6393',
               'D [06/Mar/2010:00:23:39 -0800] Report: stringpool-alloc-bytes=11976',
               'D [06/Mar/2010:00:23:39 -0800] Report: stringpool-total-bytes=139528',
               'D [06/Mar/2010:00:23:49 -0800] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:49 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:49 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:49 -0800] cupsdReadClient: 12 1.1 Get-Job-Attributes 1',
               'D [06/Mar/2010:00:23:49 -0800] Get-Job-Attributes ipp://localhost/jobs/34',
               'D [06/Mar/2010:00:23:49 -0800] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/34) from localhost',
               'D [06/Mar/2010:00:23:49 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:49 -0800] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [06/Mar/2010:00:23:49 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:49 -0800] cupsdAuthorize: No authentication data provided.',
               'D [06/Mar/2010:00:23:49 -0800] cupsdReadClient: 12 1.1 Cancel-Subscription 1',
               'D [06/Mar/2010:00:23:49 -0800] Cancel-Subscription /',
               'D [06/Mar/2010:00:23:49 -0800] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [06/Mar/2010:00:23:49 -0800] cupsdMarkDirty(-----S)',
               'D [06/Mar/2010:00:23:49 -0800] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [06/Mar/2010:00:23:49 -0800] cupsdSetBusyState: Printing jobs and dirty files',
               'D [06/Mar/2010:00:23:49 -0800] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [06/Mar/2010:00:23:49 -0800] cupsdReadClient: 17 GET /admin/log/error_log HTTP/1.1',
               'D [06/Mar/2010:00:23:49 -0800] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [06/Mar/2010:00:23:49 -0800] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 10 (Printer state reasons):
{'printer-state-message': u'Printer busy; will retry in 30 seconds...',
 'printer-state-reasons': [u'connecting-to-device']}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by cdw on 2010-05-24
> **thodges999 said:**
> What worked for me was as follows;
1. Select System, Admin, Printing from the menu
2. Press New and when the dialogue box comes up for New Printer press forward and then select your printer (HP LJ4 in my case). I know this will not be for a USB connection but we'll fix that later.
3. Once you have selected your printer driver press Apply and when asked if you want to print a test page select No.
4. Now you have your printer driver installed you should see it in the Printer Configuration window. Right click on it and select properties.
5. Change the Device URL to parallel:/dev/usb/lp0 and press Apply.

Thats it and it worked for me and others. If this fails please post the results of running lsusb in Terminal.

I am trying to install a brother printer via usb on ubuntu lynx
Following the above instructions, when I press server->new, two grayed out options appear: printer and class, but I cant do anything with them??

---

### Post by thodges999 on 2010-05-25
> **cdw said:**
> I am trying to install a brother printer via usb on ubuntu lynx
Following the above instructions, when I press server->new, two grayed out options appear: printer and class, but I cant do anything with them??

I'm not sure why the menu items are greyed out. Is there an item on the Printer Configuration toolbar which is titled New, and what happens if you click it?

Possibly a red herring but do you have CUPS installed?

---

### Post by moth17 on 2010-05-25
Did I miss something?

---

### Post by thodges999 on 2010-05-25
> **moth17 said:**
> Did I miss something?

I dont know but I missed your much earlier question and thought you might not still be looking. Have you resolved your issue and if not could you explain where my process isnt working for you.

I'm not an expert but will help if I can.

---

### Post by moth17 on 2010-05-25
> I dont know but I missed your much earlier question and thought you might not still be looking. Have you resolved your issue and if not could you explain where my process isnt working for you.

I tried the fix and nothing changed. It's funny, it can tell me I'm hooked up to a HP 960 printer, but it keeps asking  "Not connected?"  and won't print.  I am running Ubuntu 10 now. I have not tried to run your fix again since the upgrade. Window's Vista had no problem dealing with the adapter cable (surprisingly), so I reboot and switch to Vista if I need to print now. But, I'd rather run Ubuntu all the time. It makes me happy. :)

I'm also at work right now, so I can't give much more info than that.

---

### Post by thodges999 on 2010-05-26
> **moth17 said:**
> I tried the fix and nothing changed. It's funny, it can tell me I'm hooked up to a HP 960 printer, but it keeps asking  "Not connected?"  and won't print.  I am running Ubuntu 10 now. I have not tried to run your fix again since the upgrade. Window's Vista had no problem dealing with the adapter cable (surprisingly), so I reboot and switch to Vista if I need to print now. But, I'd rather run Ubuntu all the time. It makes me happy. :)

I'm also at work right now, so I can't give much more info than that.

Sorry its not working. Could you post the output of lsusb?

When you do System, Administration, Printing does your printer show up in the window?

I assume from your response that it does so right click on it and select Properties (or use the menuu Printer, Properties) and what are the values for the device URI and Make & Model. What is the printer state.

---

### Post by moth17 on 2010-05-27
> **thodges999 said:**
> Sorry its not working. Could you post the output of lsusb?

When you do System, Administration, Printing does your printer show up in the window?

I assume from your response that it does so right click on it and select Properties (or use the menuu Printer, Properties) and what are the values for the device URI and Make & Model. What is the printer state.

When I go into the New Printer box, "Forward" is greyed out. But I can click on the printer properties:

Device URI: parallel:/dev/usb/lp0
Make and Model: HP Deskjet 960c hpijs, 3.9.8
Printer State: Processing

What is the lsusb?

---

### Post by thodges999 on 2010-05-27
> **moth17 said:**
> When I go into the New Printer box, "Forward" is greyed out. But I can click on the printer properties:

Device URI: parallel:/dev/usb/lp0
Make and Model: HP Deskjet 960c hpijs, 3.9.8
Printer State: Processing

What is the lsusb?

In the New Printer box the left hand side should list devices, serial ports, network etc. What items are on your list?

You should have a couple of serial ports listed, if you select one of these is the forward still greyed out?

To run lsusb, open a terminal (Applications, Accessories, Terminal) and type lsusb. Then paste the result here.

---

### Post by moth17 on 2010-05-27
> **thodges999 said:**
> In the New Printer box the left hand side should list devices, serial ports, network etc. What items are on your list?

You should have a couple of serial ports listed, if you select one of these is the forward still greyed out?

To run lsusb, open a terminal (Applications, Accessories, Terminal) and type lsusb. Then paste the result here.

New Printer window:

other
Network Printer
   Find Network Printer
   AppSocket/HP Jet Direct
   Internet Printing Protocol (ipp)
   LPD/LPR Host or Printer
   windowes Printer via SAMBA


Selecting one of these, and then typing something into the window for each one causes the Forward button to activate. 

hafiz@hafiz-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Does that help?[-o<

---

### Post by thodges999 on 2010-05-27
I think so although I'm not sure why you have no serial ports showing. We may need to come back to that.

First you'll need to remove your non-working installation. When you first open the Printer Config window I guess you will see your HP Deskjet 960c showing. Right click on it and select Delete.

Then go back to the New Printer window, select Other and enter parallel:/dev/usb/lp0 as the URI. Then select your HP printer from the list and install following the prompts and print a test page when prompted. Any luck?

I'm sure we'll get there but you may need to be very patient!

---

### Post by moth17 on 2010-05-30
I thought I replied to this but it's not here. Anyway, I did all that and it's the same. It still doesn't work. It just says "Processing" for days...

Patience is not an issue- I've been chipping away at this problem for a long time.

---

### Post by thodges999 on 2010-05-30
> **moth17 said:**
> I thought I replied to this but it's not here. Anyway, I did all that and it's the same. It still doesn't work. It just says "Processing" for days...

Patience is not an issue- I've been chipping away at this problem for a long time.

Apologies in advance if I'm repeating what you've already done. My only experience is from 'eventually' getting my printer to work.

OK. Uninstall your printer from the Printer Configuration dialogue.

Reboot with your printer connected and turned on.

Enter [http://localhost:631/](http://localhost:631/) in your web browser and if you see the CUPS control panel select 'Add Printers and Classes' and then 'Add Printer' (Use your logon name and password when prompted)

What local printers do you see?

---

### Post by thodges999 on 2010-05-30
By the way do you not have any serial ports on your machine?

---

### Post by thodges999 on 2010-05-30
Couple of other things.

Try plugging the usb/parallel adapter into a different USB socket if you have one.

Run dmesg | tail in terminal and post result.

---

### Post by thodges999 on 2010-05-30
Sorry about this, I'm looking back at all the things I tried before.

Run ls -l /dev/usb/lp* in terminal and post result.

---

### Post by moth17 on 2010-05-30
hafiz@hafiz-desktop:~$ ls -l /dev/usb/lp*
crw-rw---- 1 root lp 180, 0 2010-05-30 09:52 /dev/usb/lp0

---

### Post by moth17 on 2010-05-30
Oh, wait! I didn't see all thoes posts above...got to try that.

---

### Post by moth17 on 2010-05-30
There are no serial ports on this machine, that's why I'm going through this. When I bought my Dell it came with only USB, so I had to get an adapter for my printer.

As far as the CUPS thing, I don't have a user name and password.

hafiz@hafiz-desktop:~$ dmesg | tail
[  293.086013] type=1503 audit(1275240300.177:16):  operation="open" pid=1049 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  293.086048] type=1503 audit(1275240300.177:17):  operation="open" pid=1049 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  379.806150] type=1503 audit(1275240386.897:18):  operation="open" pid=1049 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  379.806170] type=1503 audit(1275240386.897:19):  operation="open" pid=1049 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  713.664056] usb 5-1: USB disconnect, address 2
[  713.664299] usblp0: removed
[  721.504030] usb 5-2: new full speed USB device using uhci_hcd and address 3
[  721.696148] usb 5-2: configuration #1 chosen from 1 choice
[  721.705153] usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[  722.916480] usb 5-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

---

### Post by thodges999 on 2010-05-30
When you try to start CUPS do you get the CUPS Home Page? You should only need your username and password when you try to add a new printer. This is your system username 'hafiz' I presume, and your system password.

I assume you have deleted your printer from Printing Config but was it connected and turned on when you ran dmesg | tail?

---

### Post by thodges999 on 2010-05-30
When you try to start CUPS do you get the CUPS Home Page? You should only need your username and password when you try to add a new printer. This is your system username 'hafiz' I presume, and your system password.

I assume you have deleted your printer from Printing Config but was it connected and turned on when you ran dmesg | tail?

---

### Post by moth17 on 2010-05-30
> **thodges999 said:**
> When you try to start CUPS do you get the CUPS Home Page? You should only need your username and password when you try to add a new printer. This is your system username 'hafiz' I presume, and your system password.

I assume you have deleted your printer from Printing Config but was it connected and turned on when you ran dmesg | tail?


You assume correctly. And yes, it was connected and turned on. 

From CUPS:

Add Printer
Local Printers: 	
SCSI Printer
HP Printer (HPLIP)
HP Fax (HPLIP)

Discovered Network Printers: 
	
Other Network Printers: 
Internet Printing Protocol (http)
LPD/LPR Host or Printer
AppSocket/HP JetDirect
Internet Printing Protocol (ipp)
Backend Error Handler
Windows Printer via SAMBA 

I'll run it again:

hafiz@hafiz-desktop:~$  dmesg | tail
[  379.806170] type=1503 audit(1275240386.897:19):  operation="open" pid=1049 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  713.664056] usb 5-1: USB disconnect, address 2
[  713.664299] usblp0: removed
[  721.504030] usb 5-2: new full speed USB device using uhci_hcd and address 3
[  721.696148] usb 5-2: configuration #1 chosen from 1 choice
[  721.705153] usblp0: USB Bidirectional printer dev 3 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[  722.916480] usb 5-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  918.100620] usb 5-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  972.716242] usb 5-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[15596.280906] usb 5-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

Rebooting and running it again yields:

hafiz@hafiz-desktop:~$ dmesg | tail
[   20.848782] e1000e 0000:00:19.0: irq 25 for MSI/MSI-X
[   20.904086] e1000e 0000:00:19.0: irq 25 for MSI/MSI-X
[   20.904376] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.160182] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   21.160185] apm: disabled - APM is not SMP safe.
[   21.265967] ppdev: user-space parallel port driver
[   22.780810] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   22.780814] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   22.781042] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.836019] eth0: no IPv6 routers present

Which seems very different...

---

### Post by moth17 on 2010-05-31
I can't figure out how to delete a post, so, just ignore this...

:guitar:

---

### Post by thodges999 on 2010-05-31
In order to see if I could replicate your problem I have upgraded to 10.04 but I'm afraid my printer still works!! Also when I delete my printer from printer config it seems to still remember it as it reappears when I plug in the parallel adapter so I cant replicate your situation. Oh well!

Delete the printer from printer config again and turn it off, unplug the usb connection and reboot your computer.

Then plug in the usb connection (with the printer still turned off) and run **tail -n 20 /var/log/syslog** (this will show the last 20 entries in your syslog file, something I've just learned and gives more info than using dmesg) 

In terminal run **ls -l /dev/bus/usb/002/005** (check in lsusb that your parallel port is still Bus 005 Device 002) Sorry I think it should be **ls -l /dev/bus/usb/005/002**

---

### Post by jrd43 on 2010-05-31
Hey, thodges999 and moth17.  Just thought I'd let you know I'm being a  voyeur to your posts as I'm experiencing the same problem.  I have an  old NEC SuperScript 860 conncted via a parallel>USB adapter that I'm  trying to get working.  I  spent 10 straight hours trying to get this to work last week, and even  had some flashes of success (i.e. it would spit out a blank page, or  maybe a page with the first line of text from an OpenOffice writer  document, etc. - at one point I even printed out a test page  successfully, only to have the problems start all over).  Anyway, I  don't want to ask you to get ahead of yourself, thodges999, as I don't  want you to have to deal with two people at once who are likely going  through the same steps,  But I did want to mention, since you asked,  that my computer *does* have a serial port, but it does **not**  appear to be listed when I run lsusb, either....

jr@jr-laptop:~$  lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus  004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint  Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus  003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002  Device 005: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus  002 Device 004: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus  002 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel  Port
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub  / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux  Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux  Foundation 2.0 root hub

...Or maybe it is and I'm not recognizing  the lingo.

Anyway, I'm a very recent Ubuntu convert and am  following along with most of what you guys are saying.  You're a badass,  theodges, for all the time you've put in to helping everyone (including  me) out.  Thanks - I'll interject if I have anything to offer.

---

### Post by thodges999 on 2010-06-01
jrd43
I've had plenty of help from others on these forums in solving my problems so I'm happy if I can pass it on but I'm only an amateur so don't expect to much. :)

With regard to your post it is not lsusb that will show your serial ports as it only lists the usb connections. If you follow the original suggestion in post 11 page 2, you should see the Serial Ports when you are adding a printer.

The suggestion was "If you do System, Admin, Printing and then install a new printer of your model using one of the serial ports. On completion don't print a test page but go to the properties of the newly installed printer and change the device url to parallel:/dev/usb/lp0. Your printer will hopefully now work!" 

I have since tried it selecting 'Other' and putting parallel:/dev/usb/lp0 directly as the URI so this may work for you although the intermittent nature of your faults may mean the problem lies elsewhere.

Please try this and feel free to ask questions, if it is not successful please try the options I've suggested to moth17 and post the results here.

---

### Post by jrd43 on 2010-06-01
thodges999
Truth be told, I still don't know why you were inquiring about the serial ports.  I was just offering the info because I thought it would be helpful... it wasn't.  

As far as the parallel:/dev/usb/lp0 business - I got there a while ago and tried it with each of the five drivers listed for my printer, but was never successful.  I am indeed still using that parallel:/dev/usb/lp0 URI and the *good* news, that keeps me thinking I'm *so* close and tells me my printer and my computer are communicating, is: every 2 out of 3 print jobs (test pages and OpenOffice Writer documents) will spit out a page with the top 1/4 inch of the document printed before the "Document Print Status" comes up as "Stopped."  Perhaps moth17 has experienced the same thing?

I just tried your "Other" method and got the same results.  Thanks again.  Looking forward to playing you English boys in Round 1 in two weeks (assuming you're English, that is)....

---

### Post by thodges999 on 2010-06-01
> **jrd43 said:**
> thodges999
Truth be told, I still don't know why you were inquiring about the serial ports.  I was just offering the info because I thought it would be helpful... it wasn't.  

As far as the parallel:/dev/usb/lp0 business - I got there a while ago and tried it with each of the five drivers listed for my printer, but was never successful.  I am indeed still using that parallel:/dev/usb/lp0 URI and the *good* news, that keeps me thinking I'm *so* close and tells me my printer and my computer are communicating, is: every 2 out of 3 print jobs (test pages and OpenOffice Writer documents) will spit out a page with the top 1/4 inch of the document printed before the "Document Print Status" comes up as "Stopped."  Perhaps moth17 has experienced the same thing?

I just tried your "Other" method and got the same results.  Thanks again.  Looking forward to playing you English boys in Round 1 in two weeks (assuming you're English, that is)....

Hi
The only reason for my asking about the serial ports initially was because it was different to my machine and therefore may have been relevant, as you say it wasn't.

You say the parallel:/dev/usb/lp0 was never successful but then say you are still using it? I assume you mean your printing is erratic sometimes stopping before it is complete.

As you say communication with the printer is working, albeit erratically, which is different from Moth14. From my investigations there are sometimes problems with timing talking to the printer which causes errors.

If you run tail -n 20 /var/log/syslog immediately after a failed print it may give us a clue.

When the "Document Print Status" comes up as "Stopped." if you right click on the print job what options do you have, can you restart the print and does that work? You could also try rebooting and see if the items are still in the print queue and can be restarted. This is only to aid diagnostics not a solution.

Hope you enjoy the football (soccer), and both teams do well (but we win, if only!)

---

### Post by thodges999 on 2010-06-01
Moth17
In your post 33 back in March you gave a long output from Troubleshooting Printing (which I have only just discovered!) and I have compared this with mine.

In may not be relevant but part way through it refers to a DESKJET 990 driver when I believe you are using a 960, do you have the correct driver in case this makes a difference.

It could be useful if you could install your printer and then run this again answering yes to whether the test page printed OK even if it didn't and post the result (put it inside code tags # so it doesn't fill the page)

Could you also post the contents of /etc/cups/printers.conf.

There appears to be an error just over halfway down which results in the printer appearing to be busy but I don't understand what is causing this yet.

---

### Post by jrd43 on 2010-06-01
Well, I went back to using that URI because when I tried others the results were even less fruitful (meaning, I got absolutely nothing).  So, I've gone back to parallel:/dev/usb/lp0 until I have reason to think something else might work.  

You used the word "timing" which is something that had occurred to me, also.  I just don't know how to address it, yet.  And yes, it simply refuses to print anything past a bit at the top of the page, though it always roll out the entire page - the rest of it blank.  It does this, as I said, about half the time, or 2/3, depending on the program I'm printing from.  Also, interestingly, it will sometimes print out the document from the *previous* command (the small portion of it anyway) - for example: I try to print from Firefox, and it does nothing; minutes later, I try to print from Open Office, the light starts blinking and it prints out the little bit from the FireFox page I'd attempted before.  

Whenever the "Document Print Status" reads "Stopped," and I right click on it, the only options it gives me are "Cancel," "Delete," or "View Attributes" - the other options, such as "Reprint," are grayed out.  And yes, the queue is still there after rebooting, but my options are the same.  

I have the results of the after the most recent tail -n 20 /var/log/syslog (wherever the hell you found that!), but I should mention that it's now reading "Processing" and "Pending" for the last two documents, instead of "Stopped," and has been for 15 minutes or so....

d printer: usb://NEC/SuperScript%20860, normalized: nec superscript 860
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:58 jr-laptop kernel: [ 3712.720149] usb 2-2: new full speed USB device using uhci_hcd and address 14
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop kernel: [ 3712.901559] usb 2-2: configuration #1 chosen from 1 choice
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-2
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: Device vendor/product is 067B:2305
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop kernel: [ 3713.058543] usblp0: USB Bidirectional printer dev 14 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: failed to claim interface
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: failed to claim interface
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/usb/lp0
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-2
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: MFG:NEC MDL:SuperScript 860 SERN:- serial:
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:00 jr-laptop kernel: [ 3714.083805] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: URI matches without serial number: usb://NEC/SuperScript%20860
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: No serial number URI matches so using those without
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: URI of print queue: parallel:/dev/usb/lp0, normalized: parallel dev usb lp0
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: URI of detected printer: usb://NEC/SuperScript%20860, normalized: nec superscript 860
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: Queue ipp://localhost:631/printers/NEC-SuperScript-860 has matching device URI
Jun: command not found
jr@jr-laptop:~$ 

Can you make anything of that?

I really am looking forward to the World Cup.  It's the only chance I get, living in Arizona, to watch any soccer on basic TV.  Should be fun.

---

### Post by moth17 on 2010-06-01
I'm just catching up here, which post should I follow, post #56 or #61?

---

### Post by thodges999 on 2010-06-02
> **moth17 said:**
> I'm just catching up here, which post should I follow, post #56 or #61?

Both please. Note the change in the command in post 56

---

### Post by thodges999 on 2010-06-02
> **jrd43 said:**
> Well, I went back to using that URI because when I tried others the results were even less fruitful (meaning, I got absolutely nothing).  So, I've gone back to parallel:/dev/usb/lp0 until I have reason to think something else might work.  

You used the word "timing" which is something that had occurred to me, also.  I just don't know how to address it, yet.  And yes, it simply refuses to print anything past a bit at the top of the page, though it always roll out the entire page - the rest of it blank.  It does this, as I said, about half the time, or 2/3, depending on the program I'm printing from.  Also, interestingly, it will sometimes print out the document from the *previous* command (the small portion of it anyway) - for example: I try to print from Firefox, and it does nothing; minutes later, I try to print from Open Office, the light starts blinking and it prints out the little bit from the FireFox page I'd attempted before.  

Whenever the "Document Print Status" reads "Stopped," and I right click on it, the only options it gives me are "Cancel," "Delete," or "View Attributes" - the other options, such as "Reprint," are grayed out.  And yes, the queue is still there after rebooting, but my options are the same.  

I have the results of the after the most recent tail -n 20 /var/log/syslog (wherever the hell you found that!), but I should mention that it's now reading "Processing" and "Pending" for the last two documents, instead of "Stopped," and has been for 15 minutes or so....

```
d printer: usb://NEC/SuperScript%20860, normalized: nec superscript 860
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:58 jr-laptop kernel: [ 3712.720149] usb 2-2: new full speed USB device using uhci_hcd and address 14
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop kernel: [ 3712.901559] usb 2-2: configuration #1 chosen from 1 choice
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-2
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: Device vendor/product is 067B:2305
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop kernel: [ 3713.058543] usblp0: USB Bidirectional printer dev 14 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: failed to claim interface
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: failed to claim interface
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/usb/lp0
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-2
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:18:59 jr-laptop udev-configure-printer: MFG:NEC MDL:SuperScript 860 SERN:- serial:
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:00 jr-laptop kernel: [ 3714.083805] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: URI matches without serial number: usb://NEC/SuperScript%20860
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: No serial number URI matches so using those without
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: URI of print queue: parallel:/dev/usb/lp0, normalized: parallel dev usb lp0
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: URI of detected printer: usb://NEC/SuperScript%20860, normalized: nec superscript 860
Jun: command not found
jr@jr-laptop:~$ Jun  1 19:19:02 jr-laptop udev-configure-printer: Queue ipp://localhost:631/printers/NEC-SuperScript-860 has matching device URI
Jun: command not found
jr@jr-laptop:~$ 
```

Can you make anything of that?

I really am looking forward to the World Cup.  It's the only chance I get, living in Arizona, to watch any soccer on basic TV.  Should be fun.

OK thanks for that. (If you put any long outputs between # CODE tags (as I have done to your message above) this should make the forum pages more readable. Also what version of Ubuntu are you using?)

I think the problem is not the connection to the printer (the parallel:/dev/usb/lp0 bit) but the printer doesn't seem to properly understand what the computer is saying.

Your print out above is odd in the **Jun: command not found** on every other line which doesn't occur on mine? I don't know if the Jun relates to the month but why is it trying to run?

If I ignore that for the moment it otherwise looks similar to mine and the error type messages are the same as mine. One problem is the addresses as these can change between sessions so if I have print outs at different time they may not tie together.

To overcome that could you delete anything in the print queue, reboot (with the printer turned off and disconnected).

In a terminal run 
```
cupsctl LogLevel=debug
```
and when complete plug in the printer making sure the connections are good and turn it on.

Then run the following commands one at a time and post the reponses (all in one copy will be fine)
```
lsusb
lsmod
```
 
Try to print a test page and wait until it has stopped or after say 20 secs if nothing is happening. 

Then in a terminal run

```
gedit /var/log/cups/error_log
```

save this file and attach it to your response.

Just for the sake of completeness also run;

```
tail -n 20 /var/log/syslog
dmesg | tail
```

Finally go System, Admin, Printing, Help, Troubleshoot, follow the instructions and select your NEC printer. Try to print a test page and then save the file and attach to your response.

Sorry for all the work, I just it hope it works in the end.

Over here we can't get away from the soccer so its nice to do a bit of Shelock Holmes on printing problems!

---

### Post by mathiaho on 2010-06-02
Thanks!

I followed the description in #15, and it worked for me :)
HP Laserjet 4L + Manhattan usb/parallel cable.

---

### Post by jrd43 on 2010-06-03
So, I ran cupsctl LogLevel=debug .  I don't know if it was supposed to, but it returned no response.

Then, the response for lsusb ```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 002 Device 004: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 002 Device 003: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```...and the response for lsmod ```
Module                  Size  Used by
usblp                  10481  0 
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
pcmcia                 33024  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                68727  0 
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
joydev                  8708  0 
iwlcore               105922  1 iwl3945
drm                   162471  4 nouveau,ttm,drm_kms_helper
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_7xx1               3690  0 
psmouse                63245  0 
mac80211              204922  2 iwl3945,iwlcore
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  1 snd
usbhid                 36110  0 
hid                    67032  1 usbhid
sdhci_pci               5470  0 
intel_agp              24177  0 
sdhci                  15462  1 sdhci_pci
led_class               2864  3 iwl3945,iwlcore,sdhci
tifm_core               6045  1 tifm_7xx1
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               3978  0 
cfg80211              126485  3 iwl3945,iwlcore,mac80211
i2c_algo_bit            5028  1 nouveau
agpgart                31724  3 ttm,drm,intel_agp
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
e1000e                119856  0 

```Attempted test page, nothing happened.  Ran gedit /var/log/cups/error_log but it would not let me save the file ask you specified.  I tried, first, saving to the desktop (I would click 'save' and nothing would happen) and, second, to the cups folder, but in a big red box it told me I didn't have the "necessary permissions" to continue.  So I am posting the response in code here...```
E [03/Jun/2010:11:24:25 -0700] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
I [03/Jun/2010:11:26:06 -0700] Listening to 0.0.0.0:631 (IPv4)
I [03/Jun/2010:11:26:06 -0700] Listening to :::631 (IPv6)
I [03/Jun/2010:11:26:06 -0700] Listening to /var/run/cups/cups.sock (Domain)
I [03/Jun/2010:11:26:06 -0700] Remote access is enabled.
D [03/Jun/2010:11:26:06 -0700] Added auto ServerAlias jr-laptop
I [03/Jun/2010:11:26:06 -0700] Loaded configuration file "/etc/cups/cupsd.conf"
I [03/Jun/2010:11:26:06 -0700] Using default TempDir of /var/spool/cups/tmp...
I [03/Jun/2010:11:26:06 -0700] Configured for up to 100 clients.
I [03/Jun/2010:11:26:06 -0700] Allowing up to 100 client connections per host.
I [03/Jun/2010:11:26:06 -0700] Using policy "default" as the default!
D [03/Jun/2010:11:26:06 -0700] load_ppd: Loading /var/cache/cups/NEC-SuperScript-860.ipp...
D [03/Jun/2010:11:26:06 -0700] cupsdRegisterPrinter(p=0x21ffd218(NEC-SuperScript-860))
D [03/Jun/2010:11:26:06 -0700] cupsdMarkDirty(---p--)
D [03/Jun/2010:11:26:06 -0700] cupsdSetBusyState: Dirty files
I [03/Jun/2010:11:26:06 -0700] Partial reload complete.
I [03/Jun/2010:11:26:06 -0700] Listening to 0.0.0.0:631 on fd 3...
I [03/Jun/2010:11:26:06 -0700] Listening to :::631 on fd 6...
I [03/Jun/2010:11:26:06 -0700] Listening to /var/run/cups/cups.sock on fd 7...
I [03/Jun/2010:11:26:06 -0700] Resuming new connection processing...
D [03/Jun/2010:11:26:06 -0700] cupsdRegisterPrinter(p=0x21ffd218(NEC-SuperScript-860))
D [03/Jun/2010:11:26:06 -0700] Discarding unused server-restarted event...
D [03/Jun/2010:11:26:07 -0700] Report: clients=0
D [03/Jun/2010:11:26:07 -0700] Report: jobs=43
D [03/Jun/2010:11:26:07 -0700] Report: jobs-active=0
D [03/Jun/2010:11:26:07 -0700] Report: printers=1
D [03/Jun/2010:11:26:07 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:26:07 -0700] Report: stringpool-string-count=343
D [03/Jun/2010:11:26:07 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:26:07 -0700] Report: stringpool-total-bytes=7184
D [03/Jun/2010:11:26:30 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:26:30 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:26:30 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:26:30 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
I [03/Jun/2010:11:26:37 -0700] Generating printcap /var/run/cups/printcap...
D [03/Jun/2010:11:26:37 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:11:27:32 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:27:32 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:27:32 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:27:32 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:27:32 -0700] Report: clients=0
D [03/Jun/2010:11:27:32 -0700] Report: jobs=43
D [03/Jun/2010:11:27:32 -0700] Report: jobs-active=0
D [03/Jun/2010:11:27:32 -0700] Report: printers=1
D [03/Jun/2010:11:27:32 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:27:32 -0700] Report: stringpool-string-count=343
D [03/Jun/2010:11:27:32 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:27:32 -0700] Report: stringpool-total-bytes=7184
D [03/Jun/2010:11:27:51 -0700] cupsdAcceptClient: 11 from localhost (Domain)
D [03/Jun/2010:11:27:51 -0700] cupsdReadClient: 11 PUT /admin/conf/cupsd.conf HTTP/1.1
D [03/Jun/2010:11:27:51 -0700] cupsdSetBusyState: Active clients
D [03/Jun/2010:11:27:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:27:51 -0700] cupsdIsAuthorized: username=""
D [03/Jun/2010:11:27:51 -0700] cupsdSendHeader: 11 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [03/Jun/2010:11:27:51 -0700] cupsdCloseClient: 11
D [03/Jun/2010:11:27:51 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:11:27:51 -0700] cupsdAcceptClient: 11 from localhost (Domain)
D [03/Jun/2010:11:27:51 -0700] cupsdReadClient: 11 PUT /admin/conf/cupsd.conf HTTP/1.1
D [03/Jun/2010:11:27:51 -0700] cupsdSetBusyState: Active clients
D [03/Jun/2010:11:27:51 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:11:27:51 -0700] cupsdIsAuthorized: username="jr"
I [03/Jun/2010:11:27:51 -0700] Installing config file "/etc/cups/cupsd.conf"...
D [03/Jun/2010:11:27:51 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:11:27:51 -0700] cupsdCloseClient: 11
D [03/Jun/2010:11:27:51 -0700] cupsdDeregisterPrinter(p=0x21ffd218(NEC-SuperScript-860), removeit=1)
I [03/Jun/2010:11:27:51 -0700] cupsdDefaultRIPCacheSize: 515068k
I [03/Jun/2010:11:27:51 -0700] Listening to 0.0.0.0:631 (IPv4)
I [03/Jun/2010:11:27:51 -0700] Listening to :::631 (IPv6)
I [03/Jun/2010:11:27:51 -0700] Listening to /var/run/cups/cups.sock (Domain)
I [03/Jun/2010:11:27:51 -0700] Remote access is enabled.
D [03/Jun/2010:11:27:51 -0700] Added auto ServerAlias jr-laptop
I [03/Jun/2010:11:27:51 -0700] Loaded configuration file "/etc/cups/cupsd.conf"
I [03/Jun/2010:11:27:51 -0700] Using default TempDir of /var/spool/cups/tmp...
I [03/Jun/2010:11:27:51 -0700] Configured for up to 100 clients.
I [03/Jun/2010:11:27:51 -0700] Allowing up to 100 client connections per host.
I [03/Jun/2010:11:27:51 -0700] Using policy "default" as the default!
D [03/Jun/2010:11:27:51 -0700] load_ppd: Loading /var/cache/cups/NEC-SuperScript-860.ipp...
D [03/Jun/2010:11:27:51 -0700] cupsdRegisterPrinter(p=0x21ffd218(NEC-SuperScript-860))
D [03/Jun/2010:11:27:51 -0700] cupsdMarkDirty(---p--)
D [03/Jun/2010:11:27:51 -0700] cupsdSetBusyState: Dirty files
I [03/Jun/2010:11:27:51 -0700] Partial reload complete.
I [03/Jun/2010:11:27:51 -0700] Listening to 0.0.0.0:631 on fd 5...
I [03/Jun/2010:11:27:51 -0700] Listening to :::631 on fd 6...
I [03/Jun/2010:11:27:51 -0700] Listening to /var/run/cups/cups.sock on fd 7...
I [03/Jun/2010:11:27:51 -0700] Resuming new connection processing...
D [03/Jun/2010:11:27:51 -0700] cupsdRegisterPrinter(p=0x21ffd218(NEC-SuperScript-860))
D [03/Jun/2010:11:27:51 -0700] Discarding unused server-restarted event...
I [03/Jun/2010:11:28:22 -0700] Generating printcap /var/run/cups/printcap...
D [03/Jun/2010:11:28:22 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:11:28:34 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:28:34 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:28:34 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:28:34 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:28:34 -0700] Report: clients=0
D [03/Jun/2010:11:28:34 -0700] Report: jobs=43
D [03/Jun/2010:11:28:34 -0700] Report: jobs-active=0
D [03/Jun/2010:11:28:34 -0700] Report: printers=1
D [03/Jun/2010:11:28:34 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:28:34 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:28:34 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:28:34 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:29:36 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:29:36 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:29:36 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:29:36 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:29:36 -0700] Report: clients=0
D [03/Jun/2010:11:29:36 -0700] Report: jobs=43
D [03/Jun/2010:11:29:36 -0700] Report: jobs-active=0
D [03/Jun/2010:11:29:36 -0700] Report: printers=1
D [03/Jun/2010:11:29:36 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:29:36 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:29:36 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:29:36 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:30:38 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:30:38 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:30:38 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:30:38 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:30:38 -0700] Report: clients=0
D [03/Jun/2010:11:30:38 -0700] Report: jobs=43
D [03/Jun/2010:11:30:38 -0700] Report: jobs-active=0
D [03/Jun/2010:11:30:38 -0700] Report: printers=1
D [03/Jun/2010:11:30:38 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:30:38 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:30:38 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:30:38 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:31:40 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:31:40 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:31:40 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:31:40 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:31:40 -0700] Report: clients=0
D [03/Jun/2010:11:31:40 -0700] Report: jobs=43
D [03/Jun/2010:11:31:40 -0700] Report: jobs-active=0
D [03/Jun/2010:11:31:40 -0700] Report: printers=1
D [03/Jun/2010:11:31:40 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:31:40 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:31:40 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:31:40 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:32:42 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:32:42 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:32:42 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:32:42 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:32:42 -0700] Report: clients=0
D [03/Jun/2010:11:32:42 -0700] Report: jobs=43
D [03/Jun/2010:11:32:42 -0700] Report: jobs-active=0
D [03/Jun/2010:11:32:42 -0700] Report: printers=1
D [03/Jun/2010:11:32:42 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:32:42 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:32:42 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:32:42 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:33:44 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:33:44 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:33:44 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:33:44 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:33:44 -0700] Report: clients=0
D [03/Jun/2010:11:33:44 -0700] Report: jobs=43
D [03/Jun/2010:11:33:44 -0700] Report: jobs-active=0
D [03/Jun/2010:11:33:44 -0700] Report: printers=1
D [03/Jun/2010:11:33:44 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:33:44 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:33:44 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:33:44 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:34:46 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:34:46 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:34:46 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:34:46 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:34:46 -0700] Report: clients=0
D [03/Jun/2010:11:34:46 -0700] Report: jobs=43
D [03/Jun/2010:11:34:46 -0700] Report: jobs-active=0
D [03/Jun/2010:11:34:46 -0700] Report: printers=1
D [03/Jun/2010:11:34:46 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:34:46 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:34:46 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:34:46 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:35:48 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:35:48 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:35:48 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:35:48 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:35:48 -0700] Report: clients=0
D [03/Jun/2010:11:35:48 -0700] Report: jobs=43
D [03/Jun/2010:11:35:48 -0700] Report: jobs-active=0
D [03/Jun/2010:11:35:48 -0700] Report: printers=1
D [03/Jun/2010:11:35:48 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:35:48 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:35:48 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:35:48 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:36:50 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:36:50 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:36:50 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:36:50 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:36:50 -0700] Report: clients=0
D [03/Jun/2010:11:36:50 -0700] Report: jobs=43
D [03/Jun/2010:11:36:50 -0700] Report: jobs-active=0
D [03/Jun/2010:11:36:50 -0700] Report: printers=1
D [03/Jun/2010:11:36:50 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:36:50 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:36:50 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:36:50 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:37:52 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:37:52 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:37:52 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:37:52 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:37:52 -0700] Report: clients=0
D [03/Jun/2010:11:37:52 -0700] Report: jobs=43
D [03/Jun/2010:11:37:52 -0700] Report: jobs-active=0
D [03/Jun/2010:11:37:52 -0700] Report: printers=1
D [03/Jun/2010:11:37:52 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:37:52 -0700] Report: stringpool-string-count=344
D [03/Jun/2010:11:37:52 -0700] Report: stringpool-alloc-bytes=6200
D [03/Jun/2010:11:37:52 -0700] Report: stringpool-total-bytes=7192
D [03/Jun/2010:11:38:15 -0700] cupsdAcceptClient: 11 from localhost (Domain)
D [03/Jun/2010:11:38:15 -0700] cupsdAcceptClient: 12 from localhost (Domain)
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Active clients
D [03/Jun/2010:11:38:15 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1
D [03/Jun/2010:11:38:15 -0700] Create-Printer-Subscription /
D [03/Jun/2010:11:38:15 -0700] cupsdCreateSubscription(con=0x2203cd20(12), uri="/")
D [03/Jun/2010:11:38:15 -0700] pullmethod="ippget"
D [03/Jun/2010:11:38:15 -0700] notify-lease-duration=86400
D [03/Jun/2010:11:38:15 -0700] notify-time-interval=0
D [03/Jun/2010:11:38:15 -0700] cupsdAddSubscription(mask=18f, dest=(nil)(), job=(nil)(0), uri="(null)")
D [03/Jun/2010:11:38:15 -0700] Added subscription 82 for server
D [03/Jun/2010:11:38:15 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:15 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:15 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:15 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:15 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:15 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 12 WAITING Closing on EOF
D [03/Jun/2010:11:38:15 -0700] cupsdCloseClient: 12
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:15 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:15 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:11:38:15 -0700] CUPS-Get-Classes
D [03/Jun/2010:11:38:15 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:15 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:15 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:11:38:15 -0700] CUPS-Get-Default
D [03/Jun/2010:11:38:15 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:11:38:15 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:16 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:16 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:16 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:16 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:16 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:16 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:16 -0700] cupsdAcceptClient: 12 from localhost (Domain)
D [03/Jun/2010:11:38:16 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [03/Jun/2010:11:38:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:16 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:16 -0700] cupsdReadClient: 12 1.1 Get-Notifications 1
D [03/Jun/2010:11:38:16 -0700] Get-Notifications /
D [03/Jun/2010:11:38:16 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:11:38:16 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:11:38:16 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:16 -0700] cupsdReadClient: 12 WAITING Closing on EOF
D [03/Jun/2010:11:38:16 -0700] cupsdCloseClient: 12
D [03/Jun/2010:11:38:18 -0700] cupsdAcceptClient: 12 from localhost (Domain)
D [03/Jun/2010:11:38:18 -0700] cupsdReadClient: 12 POST /printers/NEC-SuperScript-860 HTTP/1.1
D [03/Jun/2010:11:38:18 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:18 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:18 -0700] cupsdReadClient: 12 1.1 Print-Job 1
D [03/Jun/2010:11:38:18 -0700] Print-Job ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:18 -0700] [Job ???] Auto-typing file...
I [03/Jun/2010:11:38:18 -0700] [Job ???] Request file type is application/postscript.
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(----J-)
D [03/Jun/2010:11:38:18 -0700] add_job: requesting-user-name="jr"
D [03/Jun/2010:11:38:18 -0700] Adding default job-sheets values "none,none"...
I [03/Jun/2010:11:38:18 -0700] [Job 135] Adding start banner page "none".
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(----J-)
I [03/Jun/2010:11:38:18 -0700] [Job 135] Adding end banner page "none".
I [03/Jun/2010:11:38:18 -0700] [Job 135] File of type application/postscript queued by "jr".
D [03/Jun/2010:11:38:18 -0700] [Job 135] hold_until=0
I [03/Jun/2010:11:38:18 -0700] [Job 135] Queued on "NEC-SuperScript-860" by "jr".
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(----J-)
D [03/Jun/2010:11:38:18 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:18 -0700] [Job 135] job-sheets=none,none
D [03/Jun/2010:11:38:18 -0700] [Job 135] argv[0]="NEC-SuperScript-860"
D [03/Jun/2010:11:38:18 -0700] [Job 135] argv[1]="135"
D [03/Jun/2010:11:38:18 -0700] [Job 135] argv[2]="jr"
D [03/Jun/2010:11:38:18 -0700] [Job 135] argv[3]="Test Page"
D [03/Jun/2010:11:38:18 -0700] [Job 135] argv[4]="1"
D [03/Jun/2010:11:38:18 -0700] [Job 135] argv[5]="PageSize=Letter job-uuid=urn:uuid:b0fce6cd-e8fe-3009-660c-d1658b3fd4a7 job-originating-host-name=localhost"
D [03/Jun/2010:11:38:18 -0700] [Job 135] argv[6]="/var/spool/cups/d00135-001"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[8]="HOME=/var/spool/cups/tmp"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[10]="SERVER_ADMIN=root@jr-laptop"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[11]="SOFTWARE=CUPS/1.4.3"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[13]="TZ=America/Phoenix"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[14]="USER=root"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[17]="IPP_PORT=631"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[18]="CHARSET=utf-8"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[19]="LANG=en_US.UTF-8"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[20]="PPD=/etc/cups/ppd/NEC-SuperScript-860.ppd"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[21]="RIP_MAX_CACHE=515068k"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[22]="CONTENT_TYPE=application/postscript"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[24]="PRINTER_INFO=NEC SuperScript 860"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[25]="PRINTER_LOCATION="
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[26]="PRINTER=NEC-SuperScript-860"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[27]="CUPS_FILETYPE=document"
D [03/Jun/2010:11:38:18 -0700] [Job 135] envp[28]="FINAL_CONTENT_TYPE=printer/NEC-SuperScript-860"
I [03/Jun/2010:11:38:18 -0700] [Job 135] Started filter /usr/lib/cups/filter/pstopdf (PID 1676)
I [03/Jun/2010:11:38:18 -0700] [Job 135] Started filter /usr/lib/cups/filter/pdftopdf (PID 1677)
I [03/Jun/2010:11:38:18 -0700] [Job 135] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1678)
I [03/Jun/2010:11:38:18 -0700] [Job 135] Started backend /usr/lib/cups/backend/parallel (PID 1679)
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:18 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:18 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:18 -0700] [Job 135] pstopdf 6 args: 135 jr Test Page 1 PageSize=Letter job-uuid=urn:uuid:b0fce6cd-e8fe-3009-660c-d1658b3fd4a7 job-originating-host-name=localhost /var/spool/cups/d00135-001
D [03/Jun/2010:11:38:18 -0700] [Job 135] PPD: /etc/cups/ppd/NEC-SuperScript-860.ppd
D [03/Jun/2010:11:38:18 -0700] [Job 135] STATE: +connecting-to-device
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:18 -0700] [Job 135] STATE: -connecting-to-device
D [03/Jun/2010:11:38:18 -0700] [Job 135] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x6e6150)
D [03/Jun/2010:11:38:18 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:18 -0700] [Job 135] Resolution: 300x300
D [03/Jun/2010:11:38:18 -0700] [Job 135] Page size: Letter
D [03/Jun/2010:11:38:18 -0700] [Job 135] Getting input from file 
D [03/Jun/2010:11:38:18 -0700] [Job 135] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [03/Jun/2010:11:38:18 -0700] [Job 135] foomatic-rip version 4.0.4.217 running...
D [03/Jun/2010:11:38:18 -0700] [Job 135] Parsing PPD file ...
D [03/Jun/2010:11:38:18 -0700] [Job 135] Added option PageSize
D [03/Jun/2010:11:38:18 -0700] [Job 135] Added option ImageableArea
D [03/Jun/2010:11:38:18 -0700] [Job 135] Added option PaperDimension
D [03/Jun/2010:11:38:18 -0700] [Job 135] Added option InputSlot
D [03/Jun/2010:11:38:18 -0700] [Job 135] Added option Resolution
D [03/Jun/2010:11:38:18 -0700] [Job 135] Added option HalftoningAlgorithm
D [03/Jun/2010:11:38:18 -0700] [Job 135] Added option Font
D [03/Jun/2010:11:38:18 -0700] [Job 135] 
D [03/Jun/2010:11:38:18 -0700] [Job 135] Parameter Summary
D [03/Jun/2010:11:38:18 -0700] [Job 135] -----------------
D [03/Jun/2010:11:38:18 -0700] [Job 135] 
D [03/Jun/2010:11:38:18 -0700] [Job 135] Spooler: cups
D [03/Jun/2010:11:38:18 -0700] [Job 135] Printer: NEC-SuperScript-860
D [03/Jun/2010:11:38:18 -0700] [Job 135] Shell: /bin/bash
D [03/Jun/2010:11:38:18 -0700] [Job 135] PPD file: /etc/cups/ppd/NEC-SuperScript-860.ppd
D [03/Jun/2010:11:38:18 -0700] [Job 135] ATTR file: 
D [03/Jun/2010:11:38:18 -0700] [Job 135] Printer model: NEC SuperScript 860 Foomatic/ljet2p (recommended)
D [03/Jun/2010:11:38:18 -0700] [Job 135] Job title: Test Page
D [03/Jun/2010:11:38:18 -0700] [Job 135] File(s) to be printed:
D [03/Jun/2010:11:38:18 -0700] [Job 135] <STDIN>
D [03/Jun/2010:11:38:18 -0700] [Job 135] 
D [03/Jun/2010:11:38:18 -0700] [Job 135] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [03/Jun/2010:11:38:18 -0700] [Job 135] Printing system options:
D [03/Jun/2010:11:38:18 -0700] [Job 135] Pondering option 'job-uuid=urn:uuid:b0fce6cd-e8fe-3009-660c-d1658b3fd4a7'
D [03/Jun/2010:11:38:18 -0700] [Job 135] Unknown option job-uuid=urn:uuid:b0fce6cd-e8fe-3009-660c-d1658b3fd4a7.
D [03/Jun/2010:11:38:18 -0700] [Job 135] Pondering option 'job-originating-host-name=localhost'
D [03/Jun/2010:11:38:18 -0700] [Job 135] Unknown option job-originating-host-name=localhost.
D [03/Jun/2010:11:38:18 -0700] [Job 135] Options from the PPD file:
D [03/Jun/2010:11:38:18 -0700] [Job 135] Pondering option 'PageSize=Letter'
D [03/Jun/2010:11:38:18 -0700] [Job 135] 
D [03/Jun/2010:11:38:18 -0700] [Job 135] ================================================
D [03/Jun/2010:11:38:18 -0700] [Job 135] 
D [03/Jun/2010:11:38:18 -0700] [Job 135] File: <STDIN>
D [03/Jun/2010:11:38:18 -0700] [Job 135] 
D [03/Jun/2010:11:38:18 -0700] [Job 135] ================================================
D [03/Jun/2010:11:38:18 -0700] [Job 135] 
D [03/Jun/2010:11:38:18 -0700] [Job 135] Relative margins: 18, 36, 18, 36
D [03/Jun/2010:11:38:18 -0700] [Job 135] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [03/Jun/2010:11:38:18 -0700] [Job 135] PostScript to be injected: 
D [03/Jun/2010:11:38:18 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [03/Jun/2010:11:38:18 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:18 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:18 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:18 -0700] cupsdReadClient: 16 1.1 Get-Jobs 1
D [03/Jun/2010:11:38:18 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:11:38:18 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:11:38:18 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:18 -0700] [Job 135] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dUseCIEColor -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [03/Jun/2010:11:38:18 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:18 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:19 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 1.1 Create-Printer-Subscription 1
D [03/Jun/2010:11:38:19 -0700] Create-Printer-Subscription /
D [03/Jun/2010:11:38:19 -0700] cupsdCreateSubscription(con=0x22047800(16), uri="/")
D [03/Jun/2010:11:38:19 -0700] pullmethod="ippget"
D [03/Jun/2010:11:38:19 -0700] notify-lease-duration=86400
D [03/Jun/2010:11:38:19 -0700] notify-time-interval=0
D [03/Jun/2010:11:38:19 -0700] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")
D [03/Jun/2010:11:38:19 -0700] Added subscription 83 for server
D [03/Jun/2010:11:38:19 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAcceptClient: 17 from localhost (Domain)
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:19 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [03/Jun/2010:11:38:19 -0700] cupsdCloseClient: 17
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:19 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:19 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 1.1 Get-Jobs 1
D [03/Jun/2010:11:38:19 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAcceptClient: 17 from localhost (Domain)
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:19 -0700] Get-Printer-Attributes 
D [03/Jun/2010:11:38:19 -0700] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [03/Jun/2010:11:38:19 -0700] Returning IPP client-error-not-found for Get-Printer-Attributes () from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAcceptClient: 18 from localhost (Domain)
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [03/Jun/2010:11:38:19 -0700] Get-Job-Attributes ipp://localhost/jobs/135
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/135) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 18 WAITING Closing on EOF
D [03/Jun/2010:11:38:19 -0700] cupsdCloseClient: 18
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [03/Jun/2010:11:38:19 -0700] cupsdCloseClient: 17
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:19 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:19 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 1.1 Get-Jobs 1
D [03/Jun/2010:11:38:19 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:19 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:19 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1
D [03/Jun/2010:11:38:19 -0700] Get-Notifications /
D [03/Jun/2010:11:38:19 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:19 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:19 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:19 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:19 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Classes
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Default
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Classes
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Default
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Classes
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:19 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:19 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:11:38:19 -0700] CUPS-Get-Default
D [03/Jun/2010:11:38:19 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:11:38:19 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:20 -0700] PID 1676 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [03/Jun/2010:11:38:20 -0700] [Job 135] Filetype: PDF
D [03/Jun/2010:11:38:20 -0700] [Job 135] Storing temporary files in /var/spool/cups/tmp
D [03/Jun/2010:11:38:20 -0700] PID 1677 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [03/Jun/2010:11:38:20 -0700] [Job 135] File contains 1 pages
D [03/Jun/2010:11:38:20 -0700] [Job 135] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ljet2p -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-2utnuE 
D [03/Jun/2010:11:38:20 -0700] [Job 135] Starting process "kid3" (generation 1)
D [03/Jun/2010:11:38:20 -0700] [Job 135] Starting process "kid4" (generation 2)
D [03/Jun/2010:11:38:20 -0700] [Job 135] Starting process "renderer" (generation 2)
D [03/Jun/2010:11:38:20 -0700] [Job 135] JCL: %-12345X@PJL
D [03/Jun/2010:11:38:20 -0700] [Job 135] <job data> 
D [03/Jun/2010:11:38:20 -0700] [Job 135] 
D [03/Jun/2010:11:38:20 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [03/Jun/2010:11:38:20 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:20 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:11:38:20 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:20 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1
D [03/Jun/2010:11:38:20 -0700] Get-Notifications /
D [03/Jun/2010:11:38:20 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:11:38:20 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:11:38:20 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:11:38:20 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:20 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:20 -0700] [Job 135] Read 8192 bytes of print data...
E [03/Jun/2010:11:38:20 -0700] [Job 135] Unable to write print data: Input/output error
D [03/Jun/2010:11:38:20 -0700] [Job 135] Set job-printer-state-message to "Unable to write print data: Input/output error", current level=ERROR
D [03/Jun/2010:11:38:20 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:20 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:20 -0700] PID 1679 (/usr/lib/cups/backend/parallel) exited with no errors.
D [03/Jun/2010:11:38:20 -0700] [Job 135] renderer received signal 13
D [03/Jun/2010:11:38:20 -0700] [Job 135] Kid3 exit status: 1
D [03/Jun/2010:11:38:20 -0700] PID 1678 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [03/Jun/2010:11:38:20 -0700] cupsdMarkDirty(-----S)
E [03/Jun/2010:11:38:20 -0700] [Job 135] Job stopped due to filter errors; please consult the error_log file for details.
D [03/Jun/2010:11:38:20 -0700] cupsdMarkDirty(----J-)
D [03/Jun/2010:11:38:20 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:11:38:21 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [03/Jun/2010:11:38:21 -0700] [Job 135] Unloading...
D [03/Jun/2010:11:38:21 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 15 1.1 Get-Jobs 1
D [03/Jun/2010:11:38:21 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:11:38:21 -0700] [Job 135] Loading attributes...
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1
D [03/Jun/2010:11:38:21 -0700] Get-Notifications /
D [03/Jun/2010:11:38:21 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [03/Jun/2010:11:38:21 -0700] cupsdCloseClient: 15
D [03/Jun/2010:11:38:21 -0700] cupsdAcceptClient: 15 from localhost (Domain)
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 15 1.1 Get-Notifications 1
D [03/Jun/2010:11:38:21 -0700] Get-Notifications /
D [03/Jun/2010:11:38:21 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdAcceptClient: 17 from localhost (Domain)
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:21 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [03/Jun/2010:11:38:21 -0700] Get-Job-Attributes ipp://localhost/jobs/135
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/135) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [03/Jun/2010:11:38:21 -0700] cupsdCloseClient: 17
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAcceptClient: 17 from localhost (Domain)
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [03/Jun/2010:11:38:21 -0700] Get-Job-Attributes ipp://localhost/jobs/135
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/135) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAcceptClient: 18 from localhost (Domain)
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:21 -0700] Get-Printer-Attributes ipp://jr-laptop:631/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://jr-laptop:631/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [03/Jun/2010:11:38:21 -0700] Get-Job-Attributes ipp://localhost/jobs/135
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/135) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [03/Jun/2010:11:38:21 -0700] cupsdCloseClient: 17
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:11:38:21 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:21 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:21 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:11:38:21 -0700] CUPS-Get-Classes
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:11:38:21 -0700] CUPS-Get-Default
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:21 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:11:38:21 -0700] CUPS-Get-Classes
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:11:38:21 -0700] CUPS-Get-Default
D [03/Jun/2010:11:38:21 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:11:38:21 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:21 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [03/Jun/2010:11:38:21 -0700] cupsdCloseClient: 15
D [03/Jun/2010:11:38:22 -0700] cupsdAcceptClient: 15 from localhost:631 (IPv6)
D [03/Jun/2010:11:38:22 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [03/Jun/2010:11:38:22 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:22 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:22 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Devices 1
D [03/Jun/2010:11:38:22 -0700] CUPS-Get-Devices
D [03/Jun/2010:11:38:22 -0700] cupsdIsAuthorized: username=""
D [03/Jun/2010:11:38:22 -0700] Returning HTTP Unauthorized for CUPS-Get-Devices (no URI) from localhost
D [03/Jun/2010:11:38:22 -0700] cupsdSendHeader: 15 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [03/Jun/2010:11:38:22 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [03/Jun/2010:11:38:22 -0700] cupsdCloseClient: 15
D [03/Jun/2010:11:38:22 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:22 -0700] cupsdAcceptClient: 15 from localhost:631 (IPv6)
D [03/Jun/2010:11:38:22 -0700] cupsdAcceptClient: 16 from localhost:631 (IPv6)
D [03/Jun/2010:11:38:22 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [03/Jun/2010:11:38:22 -0700] cupsdCloseClient: 15
D [03/Jun/2010:11:38:22 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [03/Jun/2010:11:38:22 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:22 -0700] cupsdAuthorize: Authorized as root using Local
D [03/Jun/2010:11:38:22 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Devices 1
D [03/Jun/2010:11:38:22 -0700] CUPS-Get-Devices
D [03/Jun/2010:11:38:22 -0700] cupsdIsAuthorized: username="root"
D [03/Jun/2010:11:38:22 -0700] [CGI] argv[0] = "/usr/lib/cups/daemon/cups-deviced"
D [03/Jun/2010:11:38:22 -0700] [CGI] argv[1] = "1"
D [03/Jun/2010:11:38:22 -0700] [CGI] argv[2] = "0"
D [03/Jun/2010:11:38:22 -0700] [CGI] argv[3] = "2"
D [03/Jun/2010:11:38:22 -0700] [CGI] argv[4] = "7"
D [03/Jun/2010:11:38:22 -0700] [CGI] argv[5] = "requested-attributes=all exclude-schemes='beh','bluetooth','cups-pdf','http','https','ipp','lpd','ncp','parallel','scsi','smb','snmp','socket'"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@jr-laptop"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[14] = "USER=root"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Local"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[26] = "SCRIPT_NAME=/"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[28] = "REMOTE_USER=root"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[29] = "SERVER_PROTOCOL=HTTP/1.1"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[30] = "HTTP_USER_AGENT=CUPS/1.4.3"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[31] = "REQUEST_METHOD=POST"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[32] = "CONTENT_LENGTH=234"
D [03/Jun/2010:11:38:22 -0700] [CGI] envp[33] = "CONTENT_TYPE=application/ipp"
D [03/Jun/2010:11:38:22 -0700] [CGI] Started /usr/lib/cups/daemon/cups-deviced (PID 1724)
I [03/Jun/2010:11:38:22 -0700] Started "/usr/lib/cups/daemon/cups-deviced" (pid=1724)
D [03/Jun/2010:11:38:22 -0700] cupsdSendCommand: 16 file=15
D [03/Jun/2010:11:38:22 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/usb (PID 1725)
D [03/Jun/2010:11:38:22 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/dnssd (PID 1726)
D [03/Jun/2010:11:38:22 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/serial (PID 1727)
D [03/Jun/2010:11:38:22 -0700] [CGI] list_devices_libusb
D [03/Jun/2010:11:38:22 -0700] [CGI] usb_find_busses=5
D [03/Jun/2010:11:38:22 -0700] [CGI] usb_find_devices=10
D [03/Jun/2010:11:38:22 -0700] [cups-deviced] PID 1727 (serial) exited with no errors.
D [03/Jun/2010:11:38:22 -0700] [CGI] Flushed attributes...
D [03/Jun/2010:11:38:22 -0700] [cups-deviced] Found device "usb://NEC/SuperScript%20860"...
D [03/Jun/2010:11:38:22 -0700] Script header: Content-Type: application/ipp
D [03/Jun/2010:11:38:22 -0700] Script header: 
D [03/Jun/2010:11:38:22 -0700] [cups-deviced] PID 1725 (usb) exited with no errors.
D [03/Jun/2010:11:38:24 -0700] PID 1724 (/usr/lib/cups/daemon/cups-deviced) exited with no errors.
D [03/Jun/2010:11:38:24 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:24 -0700] cupsdAcceptClient: 15 from localhost:631 (IPv6)
D [03/Jun/2010:11:38:24 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [03/Jun/2010:11:38:24 -0700] cupsdCloseClient: 16
D [03/Jun/2010:11:38:24 -0700] cupsdReadClient: 15 POST / HTTP/1.1
D [03/Jun/2010:11:38:24 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:11:38:24 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:11:38:24 -0700] cupsdReadClient: 15 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:11:38:24 -0700] CUPS-Get-Printers
D [03/Jun/2010:11:38:24 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:11:38:24 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:11:38:24 -0700] cupsdReadClient: 15 WAITING Closing on EOF
D [03/Jun/2010:11:38:24 -0700] cupsdCloseClient: 15
I [03/Jun/2010:11:38:46 -0700] Saving job cache file "/var/cache/cups/job.cache"...
I [03/Jun/2010:11:38:46 -0700] Saving subscriptions.conf...
D [03/Jun/2010:11:38:46 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:11:38:52 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:38:52 -0700] cupsdNetIFUpdate: "eth0" = 70.176.188.8:631
D [03/Jun/2010:11:38:52 -0700] cupsdNetIFUpdate: "lo" = localhost:631
D [03/Jun/2010:11:38:52 -0700] cupsdNetIFUpdate: "eth0" = fe80::216:36ff:fef9:87a0%eth0:631
D [03/Jun/2010:11:38:52 -0700] Report: clients=3
D [03/Jun/2010:11:38:52 -0700] Report: jobs=44
D [03/Jun/2010:11:38:52 -0700] Report: jobs-active=1
D [03/Jun/2010:11:38:52 -0700] Report: printers=1
D [03/Jun/2010:11:38:52 -0700] Report: printers-implicit=0
D [03/Jun/2010:11:38:52 -0700] Report: stringpool-string-count=968
D [03/Jun/2010:11:38:52 -0700] Report: stringpool-alloc-bytes=7928
D [03/Jun/2010:11:38:52 -0700] Report: stringpool-total-bytes=21272
```Then, I ran...
tail -n 20 /var/log/syslog
dmesg | tail
...though this confused me with the return line in the middle, so I also ran...
tail -n 20 /var/log/syslog dmesg | tail
...and nothing happened either time (in terms of a response), so hopefully I did it right.

Then, went through the troubleshoot process, was not able to print a test page, and it gave me a new error log ```
D [03/Jun/2010:12:06:47 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:12:06:47 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:06:47 -0700] cupsdSetBusyState: Active clients
D [03/Jun/2010:12:06:47 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:06:47 -0700] cupsdReadClient: 19 1.1 Get-Jobs 1
D [03/Jun/2010:12:06:47 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:12:06:47 -0700] [Job 135] Loading attributes...
D [03/Jun/2010:12:06:47 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:12:06:47 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:12:06:47 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:06:47 -0700] cupsdSetBusyState: Active clients
D [03/Jun/2010:12:06:47 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:06:47 -0700] cupsdReadClient: 19 1.1 Get-Jobs 1
D [03/Jun/2010:12:06:47 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:12:06:47 -0700] [Job 92] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 92] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 93] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 93] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 94] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 94] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 95] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 95] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 96] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 96] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 97] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 97] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 98] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 98] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 99] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 99] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 100] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 100] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 101] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 101] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 102] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 102] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 103] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 103] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 104] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 104] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 105] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 105] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 106] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 106] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 107] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 107] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 108] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 108] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 109] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 109] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 110] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 110] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 111] Loading attributes...
E [03/Jun/2010:12:06:47 -0700] [Job 111] Unable to queue job for destination "superscript_860"!
D [03/Jun/2010:12:06:47 -0700] [Job 112] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 113] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 114] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 115] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 116] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 117] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 118] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 119] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 120] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 121] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 122] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 123] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 124] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 125] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 126] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 127] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 128] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 129] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 130] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 131] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 132] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 133] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] [Job 134] Loading attributes...
D [03/Jun/2010:12:06:48 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:12:06:48 -0700] cupsdSetBusyState: Not busy
D [03/Jun/2010:12:06:48 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:06:48 -0700] cupsdSetBusyState: Active clients
D [03/Jun/2010:12:06:48 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:06:48 -0700] cupsdReadClient: 19 1.1 Create-Printer-Subscription 1
D [03/Jun/2010:12:06:48 -0700] Create-Printer-Subscription /
D [03/Jun/2010:12:06:48 -0700] cupsdCreateSubscription(con=0x2205b878(19), uri="/")
D [03/Jun/2010:12:06:48 -0700] pullmethod="ippget"
D [03/Jun/2010:12:06:48 -0700] notify-lease-duration=86400
D [03/Jun/2010:12:06:48 -0700] notify-time-interval=0
D [03/Jun/2010:12:06:48 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [03/Jun/2010:12:06:48 -0700] Added subscription 85 for server
D [03/Jun/2010:12:06:48 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:48 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:48 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [03/Jun/2010:12:06:48 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:49 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:06:49 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:49 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:06:49 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:49 -0700] Get-Notifications /
D [03/Jun/2010:12:06:49 -0700] cupsdIsAuthorized: username="jr"
D [03/Jun/2010:12:06:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:49 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAcceptClient: 20 from localhost (Domain)
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 20 POST /printers/NEC-SuperScript-860 HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 20 1.1 Print-Job 1
D [03/Jun/2010:12:06:50 -0700] Print-Job ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:12:06:50 -0700] [Job ???] Auto-typing file...
I [03/Jun/2010:12:06:50 -0700] [Job ???] Request file type is application/vnd.cups-banner.
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(----J-)
D [03/Jun/2010:12:06:50 -0700] add_job: requesting-user-name="jr"
D [03/Jun/2010:12:06:50 -0700] Adding default job-sheets values "none,none"...
I [03/Jun/2010:12:06:50 -0700] [Job 136] Adding start banner page "none".
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(----J-)
I [03/Jun/2010:12:06:50 -0700] [Job 136] Adding end banner page "none".
I [03/Jun/2010:12:06:50 -0700] [Job 136] File of type application/vnd.cups-banner queued by "jr".
D [03/Jun/2010:12:06:50 -0700] [Job 136] hold_until=0
I [03/Jun/2010:12:06:50 -0700] [Job 136] Queued on "NEC-SuperScript-860" by "jr".
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(----J-)
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:50 -0700] [Job 136] job-sheets=none,none
D [03/Jun/2010:12:06:50 -0700] [Job 136] argv[0]="NEC-SuperScript-860"
D [03/Jun/2010:12:06:50 -0700] [Job 136] argv[1]="136"
D [03/Jun/2010:12:06:50 -0700] [Job 136] argv[2]="jr"
D [03/Jun/2010:12:06:50 -0700] [Job 136] argv[3]="Test Page"
D [03/Jun/2010:12:06:50 -0700] [Job 136] argv[4]="1"
D [03/Jun/2010:12:06:50 -0700] [Job 136] argv[5]="job-uuid=urn:uuid:3d1a89fc-825f-3955-4c22-22c4ed21d970 job-originating-host-name=localhost"
D [03/Jun/2010:12:06:50 -0700] [Job 136] argv[6]="/var/spool/cups/d00136-001"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[8]="HOME=/var/spool/cups/tmp"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[10]="SERVER_ADMIN=root@jr-laptop"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[11]="SOFTWARE=CUPS/1.4.3"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[13]="TZ=America/Phoenix"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[14]="USER=root"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[17]="IPP_PORT=631"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[18]="CHARSET=utf-8"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[19]="LANG=en_US.UTF-8"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[20]="PPD=/etc/cups/ppd/NEC-SuperScript-860.ppd"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[21]="RIP_MAX_CACHE=515068k"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[24]="PRINTER_INFO=NEC SuperScript 860"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[25]="PRINTER_LOCATION="
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[26]="PRINTER=NEC-SuperScript-860"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[27]="CUPS_FILETYPE=document"
D [03/Jun/2010:12:06:50 -0700] [Job 136] envp[28]="FINAL_CONTENT_TYPE=printer/NEC-SuperScript-860"
I [03/Jun/2010:12:06:50 -0700] [Job 136] Started filter /usr/lib/cups/filter/bannertops (PID 1805)
I [03/Jun/2010:12:06:50 -0700] [Job 136] Started filter /usr/lib/cups/filter/pstopdf (PID 1806)
I [03/Jun/2010:12:06:50 -0700] [Job 136] Started filter /usr/lib/cups/filter/pdftopdf (PID 1807)
I [03/Jun/2010:12:06:50 -0700] [Job 136] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1808)
I [03/Jun/2010:12:06:50 -0700] [Job 136] Started backend /usr/lib/cups/backend/parallel (PID 1809)
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] [Job 136] pstopdf 5 args: 136 jr Test Page 1 job-uuid=urn:uuid:3d1a89fc-825f-3955-4c22-22c4ed21d970 job-originating-host-name=localhost
D [03/Jun/2010:12:06:50 -0700] [Job 136] PPD: /etc/cups/ppd/NEC-SuperScript-860.ppd
D [03/Jun/2010:12:06:50 -0700] [Job 136] STATE: +connecting-to-device
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:50 -0700] [Job 136] STATE: -connecting-to-device
D [03/Jun/2010:12:06:50 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:50 -0700] [Job 136] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x5d5150)
D [03/Jun/2010:12:06:50 -0700] [Job 136] Getting input from file
D [03/Jun/2010:12:06:50 -0700] [Job 136] load_banner(filename="/var/spool/cups/d00136-001")
D [03/Jun/2010:12:06:50 -0700] [Job 136] foomatic-rip version 4.0.4.217 running...
D [03/Jun/2010:12:06:50 -0700] [Job 136] Parsing PPD file ...
D [03/Jun/2010:12:06:50 -0700] [Job 136] Added option PageSize
D [03/Jun/2010:12:06:50 -0700] [Job 136] Added option ImageableArea
D [03/Jun/2010:12:06:50 -0700] [Job 136] Added option PaperDimension
D [03/Jun/2010:12:06:50 -0700] [Job 136] Added option InputSlot
D [03/Jun/2010:12:06:50 -0700] [Job 136] Added option Resolution
D [03/Jun/2010:12:06:50 -0700] [Job 136] Added option HalftoningAlgorithm
D [03/Jun/2010:12:06:50 -0700] [Job 136] Added option Font
D [03/Jun/2010:12:06:50 -0700] [Job 136]
D [03/Jun/2010:12:06:50 -0700] [Job 136] Parameter Summary
D [03/Jun/2010:12:06:50 -0700] [Job 136] -----------------
D [03/Jun/2010:12:06:50 -0700] [Job 136]
D [03/Jun/2010:12:06:50 -0700] [Job 136] Spooler: cups
D [03/Jun/2010:12:06:50 -0700] [Job 136] Printer: NEC-SuperScript-860
D [03/Jun/2010:12:06:50 -0700] [Job 136] Shell: /bin/bash
D [03/Jun/2010:12:06:50 -0700] [Job 136] PPD file: /etc/cups/ppd/NEC-SuperScript-860.ppd
D [03/Jun/2010:12:06:50 -0700] [Job 136] ATTR file:
D [03/Jun/2010:12:06:50 -0700] [Job 136] Printer model: NEC SuperScript 860 Foomatic/ljet2p (recommended)
D [03/Jun/2010:12:06:50 -0700] [Job 136] Job title: Test Page
D [03/Jun/2010:12:06:50 -0700] [Job 136] File(s) to be printed:
D [03/Jun/2010:12:06:50 -0700] [Job 136] <STDIN>
D [03/Jun/2010:12:06:50 -0700] [Job 136]
D [03/Jun/2010:12:06:50 -0700] [Job 136] Page = 612x792; 18,36 to 594,756
D [03/Jun/2010:12:06:50 -0700] [Job 136] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [03/Jun/2010:12:06:50 -0700] [Job 136] Printing system options:
D [03/Jun/2010:12:06:50 -0700] [Job 136] Pondering option 'job-uuid=urn:uuid:3d1a89fc-825f-3955-4c22-22c4ed21d970'
D [03/Jun/2010:12:06:50 -0700] [Job 136] Unknown option job-uuid=urn:uuid:3d1a89fc-825f-3955-4c22-22c4ed21d970.
D [03/Jun/2010:12:06:50 -0700] [Job 136] Pondering option 'job-originating-host-name=localhost'
D [03/Jun/2010:12:06:50 -0700] [Job 136] Unknown option job-originating-host-name=localhost.
D [03/Jun/2010:12:06:50 -0700] [Job 136] Options from the PPD file:
D [03/Jun/2010:12:06:50 -0700] [Job 136]
D [03/Jun/2010:12:06:50 -0700] [Job 136] ================================================
D [03/Jun/2010:12:06:50 -0700] [Job 136]
D [03/Jun/2010:12:06:50 -0700] [Job 136] File: <STDIN>
D [03/Jun/2010:12:06:50 -0700] [Job 136]
D [03/Jun/2010:12:06:50 -0700] [Job 136] ================================================
D [03/Jun/2010:12:06:50 -0700] [Job 136]
D [03/Jun/2010:12:06:50 -0700] [Job 136] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
D [03/Jun/2010:12:06:50 -0700] [Job 136] PNG image: 192x128x8, color_type=2 (RGB)
D [03/Jun/2010:12:06:50 -0700] PID 1805 (/usr/lib/cups/filter/bannertops) exited with no errors.
D [03/Jun/2010:12:06:50 -0700] [Job 136] Resolution: 300x300
D [03/Jun/2010:12:06:50 -0700] [Job 136] Page size: Letter
D [03/Jun/2010:12:06:50 -0700] [Job 136] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [03/Jun/2010:12:06:50 -0700] [Job 136] Relative margins: 18, 36, 18, 36
D [03/Jun/2010:12:06:50 -0700] [Job 136] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [03/Jun/2010:12:06:50 -0700] [Job 136] PostScript to be injected:
D [03/Jun/2010:12:06:50 -0700] [Job 136] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer -dUseCIEColor -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -
D [03/Jun/2010:12:06:50 -0700] cupsdAcceptClient: 22 from localhost (Domain)
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdAcceptClient: 23 from localhost (Domain)
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 22 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:50 -0700] Get-Notifications /
D [03/Jun/2010:12:06:50 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 1.1 Get-Jobs 1
D [03/Jun/2010:12:06:50 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 WAITING Closing on EOF
D [03/Jun/2010:12:06:50 -0700] cupsdCloseClient: 23
D [03/Jun/2010:12:06:50 -0700] cupsdAcceptClient: 23 from localhost (Domain)
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:50 -0700] Get-Notifications /
D [03/Jun/2010:12:06:50 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdAcceptClient: 24 from localhost (Domain)
D [03/Jun/2010:12:06:50 -0700] cupsdAcceptClient: 25 from localhost (Domain)
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 24 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:12:06:50 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 24 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:50 -0700] Get-Notifications /
D [03/Jun/2010:12:06:50 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [03/Jun/2010:12:06:50 -0700] Get-Job-Attributes ipp://localhost/jobs/136
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/136) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 24 WAITING Closing on EOF
D [03/Jun/2010:12:06:50 -0700] cupsdCloseClient: 24
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:50 -0700] Get-Notifications /
D [03/Jun/2010:12:06:50 -0700] cupsdIsAuthorized: username="jr"
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:12:06:50 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 23 WAITING Closing on EOF
D [03/Jun/2010:12:06:50 -0700] cupsdCloseClient: 23
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:12:06:50 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 22 WAITING Closing on EOF
D [03/Jun/2010:12:06:50 -0700] cupsdCloseClient: 22
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:50 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:50 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:50 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:50 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:50 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAcceptClient: 22 from localhost:631 (IPv6)
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:51 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 22 WAITING Closing on EOF
D [03/Jun/2010:12:06:51 -0700] cupsdCloseClient: 22
D [03/Jun/2010:12:06:51 -0700] PID 1806 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [03/Jun/2010:12:06:51 -0700] [Job 136] Filetype: PDF
D [03/Jun/2010:12:06:51 -0700] [Job 136] Storing temporary files in /var/spool/cups/tmp
D [03/Jun/2010:12:06:51 -0700] PID 1807 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [03/Jun/2010:12:06:51 -0700] [Job 136] File contains 1 pages
D [03/Jun/2010:12:06:51 -0700] [Job 136] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ljet2p -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-vLryCd
D [03/Jun/2010:12:06:51 -0700] [Job 136] Starting process "kid3" (generation 1)
D [03/Jun/2010:12:06:51 -0700] [Job 136] Starting process "kid4" (generation 2)
D [03/Jun/2010:12:06:51 -0700] [Job 136] Starting process "renderer" (generation 2)
D [03/Jun/2010:12:06:51 -0700] [Job 136] JCL: %-12345X@PJL
D [03/Jun/2010:12:06:51 -0700] [Job 136] <job data>
D [03/Jun/2010:12:06:51 -0700] [Job 136]
D [03/Jun/2010:12:06:51 -0700] [Job 136] Read 8192 bytes of print data...
E [03/Jun/2010:12:06:51 -0700] [Job 136] Unable to write print data: No such device
D [03/Jun/2010:12:06:51 -0700] [Job 136] Set job-printer-state-message to "Unable to write print data: No such device", current level=ERROR
D [03/Jun/2010:12:06:51 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:51 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:51 -0700] PID 1809 (/usr/lib/cups/backend/parallel) exited with no errors.
D [03/Jun/2010:12:06:51 -0700] [Job 136] renderer received signal 13
D [03/Jun/2010:12:06:51 -0700] [Job 136] Kid3 exit status: 1
D [03/Jun/2010:12:06:51 -0700] PID 1808 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [03/Jun/2010:12:06:51 -0700] cupsdMarkDirty(-----S)
E [03/Jun/2010:12:06:51 -0700] [Job 136] Job stopped due to filter errors; please consult the error_log file for details.
D [03/Jun/2010:12:06:51 -0700] cupsdMarkDirty(----J-)
D [03/Jun/2010:12:06:51 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:06:51 -0700] cupsdAcceptClient: 21 from localhost (Domain)
D [03/Jun/2010:12:06:51 -0700] cupsdAcceptClient: 22 from localhost (Domain)
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 21 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdAcceptClient: 23 from localhost (Domain)
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 23 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 21 1.1 Get-Jobs 1
D [03/Jun/2010:12:06:51 -0700] Get-Jobs ipp://localhost/printers/
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 22 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:51 -0700] Get-Notifications /
D [03/Jun/2010:12:06:51 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 23 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:51 -0700] Get-Notifications /
D [03/Jun/2010:12:06:51 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 21 WAITING Closing on EOF
D [03/Jun/2010:12:06:51 -0700] cupsdCloseClient: 21
D [03/Jun/2010:12:06:51 -0700] cupsdAcceptClient: 21 from localhost (Domain)
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 21 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 21 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:51 -0700] Get-Notifications /
D [03/Jun/2010:12:06:51 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 23 WAITING Closing on EOF
D [03/Jun/2010:12:06:51 -0700] cupsdCloseClient: 23
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:12:06:51 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1
D [03/Jun/2010:12:06:51 -0700] Get-Notifications /
D [03/Jun/2010:12:06:51 -0700] cupsdIsAuthorized: username="jr"
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:51 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:51 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:51 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdAcceptClient: 23 from localhost (Domain)
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 23 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:12:06:51 -0700] Get-Printer-Attributes ipp://jr-laptop:631/printers/NEC-SuperScript-860
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://jr-laptop:631/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 23 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [03/Jun/2010:12:06:51 -0700] Get-Job-Attributes ipp://localhost/jobs/136
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/136) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:51 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:51 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:51 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:51 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:51 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1
D [03/Jun/2010:12:06:51 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC-SuperScript-860
D [03/Jun/2010:12:06:51 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC-SuperScript-860) from localhost
D [03/Jun/2010:12:06:51 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 22 WAITING Closing on EOF
D [03/Jun/2010:12:06:52 -0700] cupsdCloseClient: 22
D [03/Jun/2010:12:06:52 -0700] [Job 136] Unloading...
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:52 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 21 WAITING Closing on EOF
D [03/Jun/2010:12:06:52 -0700] cupsdCloseClient: 21
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:52 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:52 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:52 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Classes
D [03/Jun/2010:12:06:52 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Default
D [03/Jun/2010:12:06:52 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAcceptClient: 21 from localhost:631 (IPv6)
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 21 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 21 1.1 CUPS-Get-Devices 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Devices
D [03/Jun/2010:12:06:52 -0700] cupsdIsAuthorized: username=""
D [03/Jun/2010:12:06:52 -0700] Returning HTTP Unauthorized for CUPS-Get-Devices (no URI) from localhost
D [03/Jun/2010:12:06:52 -0700] cupsdSendHeader: 21 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 21 WAITING Closing on EOF
D [03/Jun/2010:12:06:52 -0700] cupsdCloseClient: 21
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAcceptClient: 21 from localhost:631 (IPv6)
D [03/Jun/2010:12:06:52 -0700] cupsdAcceptClient: 22 from localhost:631 (IPv6)
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 21 WAITING Closing on EOF
D [03/Jun/2010:12:06:52 -0700] cupsdCloseClient: 21
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 22 POST / HTTP/1.1
D [03/Jun/2010:12:06:52 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:52 -0700] cupsdAuthorize: Authorized as root using Local
D [03/Jun/2010:12:06:52 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Devices 1
D [03/Jun/2010:12:06:52 -0700] CUPS-Get-Devices
D [03/Jun/2010:12:06:52 -0700] cupsdIsAuthorized: username="root"
D [03/Jun/2010:12:06:52 -0700] [CGI] argv[0] = "/usr/lib/cups/daemon/cups-deviced"
D [03/Jun/2010:12:06:52 -0700] [CGI] argv[1] = "1"
D [03/Jun/2010:12:06:52 -0700] [CGI] argv[2] = "0"
D [03/Jun/2010:12:06:52 -0700] [CGI] argv[3] = "2"
D [03/Jun/2010:12:06:52 -0700] [CGI] argv[4] = "7"
D [03/Jun/2010:12:06:52 -0700] [CGI] argv[5] = "requested-attributes=all exclude-schemes='beh','bluetooth','cups-pdf','http','https','ipp','lpd','ncp','parallel','scsi','smb','snmp','socket'"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@jr-laptop"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[14] = "USER=root"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Local"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[26] = "SCRIPT_NAME=/"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[28] = "REMOTE_USER=root"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[29] = "SERVER_PROTOCOL=HTTP/1.1"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[30] = "HTTP_USER_AGENT=CUPS/1.4.3"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[31] = "REQUEST_METHOD=POST"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[32] = "CONTENT_LENGTH=234"
D [03/Jun/2010:12:06:52 -0700] [CGI] envp[33] = "CONTENT_TYPE=application/ipp"
D [03/Jun/2010:12:06:52 -0700] [CGI] Started /usr/lib/cups/daemon/cups-deviced (PID 1855)
I [03/Jun/2010:12:06:52 -0700] Started "/usr/lib/cups/daemon/cups-deviced" (pid=1855)
D [03/Jun/2010:12:06:52 -0700] cupsdSendCommand: 22 file=21
D [03/Jun/2010:12:06:52 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/usb (PID 1856)
D [03/Jun/2010:12:06:52 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/dnssd (PID 1857)
D [03/Jun/2010:12:06:52 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/serial (PID 1858)
D [03/Jun/2010:12:06:52 -0700] [CGI] list_devices_libusb
D [03/Jun/2010:12:06:52 -0700] [CGI] usb_find_busses=5
D [03/Jun/2010:12:06:52 -0700] [CGI] usb_find_devices=10
D [03/Jun/2010:12:06:52 -0700] [cups-deviced] PID 1858 (serial) exited with no errors.
D [03/Jun/2010:12:06:52 -0700] [CGI] Flushed attributes...
D [03/Jun/2010:12:06:52 -0700] [cups-deviced] Found device "usb://NEC/SuperScript%20860"...
D [03/Jun/2010:12:06:52 -0700] Script header: Content-Type: application/ipp
D [03/Jun/2010:12:06:52 -0700] Script header:
D [03/Jun/2010:12:06:52 -0700] [cups-deviced] PID 1856 (usb) exited with no errors.
D [03/Jun/2010:12:06:54 -0700] PID 1855 (/usr/lib/cups/daemon/cups-deviced) exited with no errors.
D [03/Jun/2010:12:06:54 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:54 -0700] cupsdReadClient: 22 WAITING Closing on EOF
D [03/Jun/2010:12:06:54 -0700] cupsdCloseClient: 22
D [03/Jun/2010:12:06:54 -0700] cupsdAcceptClient: 21 from localhost:631 (IPv6)
D [03/Jun/2010:12:06:54 -0700] cupsdReadClient: 21 POST / HTTP/1.1
D [03/Jun/2010:12:06:54 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:06:54 -0700] cupsdAuthorize: No authentication data provided.
D [03/Jun/2010:12:06:54 -0700] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1
D [03/Jun/2010:12:06:54 -0700] CUPS-Get-Printers
D [03/Jun/2010:12:06:54 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [03/Jun/2010:12:06:54 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:06:54 -0700] cupsdReadClient: 21 WAITING Closing on EOF
D [03/Jun/2010:12:06:54 -0700] cupsdCloseClient: 21
D [03/Jun/2010:12:07:02 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:07:02 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:07:02 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:07:02 -0700] cupsdReadClient: 19 1.1 Get-Job-Attributes 1
D [03/Jun/2010:12:07:02 -0700] Get-Job-Attributes ipp://localhost/jobs/136
D [03/Jun/2010:12:07:02 -0700] [Job 136] Loading attributes...
D [03/Jun/2010:12:07:02 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/136) from localhost
D [03/Jun/2010:12:07:02 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:07:02 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [03/Jun/2010:12:07:02 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:07:02 -0700] cupsdAuthorize: Authorized as jr using PeerCred
D [03/Jun/2010:12:07:02 -0700] cupsdReadClient: 19 1.1 Cancel-Subscription 1
D [03/Jun/2010:12:07:02 -0700] Cancel-Subscription /
D [03/Jun/2010:12:07:02 -0700] cupsdIsAuthorized: username="jr"
D [03/Jun/2010:12:07:02 -0700] cupsdMarkDirty(-----S)
D [03/Jun/2010:12:07:02 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost
D [03/Jun/2010:12:07:02 -0700] cupsdSetBusyState: Dirty files
D [03/Jun/2010:12:07:02 -0700] cupsdAcceptClient: 21 from localhost (Domain)
D [03/Jun/2010:12:07:02 -0700] cupsdReadClient: 21 GET /admin/log/error_log HTTP/1.1
D [03/Jun/2010:12:07:02 -0700] cupsdSetBusyState: Active clients and dirty files
D [03/Jun/2010:12:07:02 -0700] cupsdAuthorize: No authentication data provided.
```

In the end, it gave me a file to save if I wanted to report a bug, which I would like to, but I don't know to whom. I tried to attach it here in case you wanted to have a look at it, but it was too large for the forum (87.5 kb).  

Here's a return apology for all the work.  And a thanks.  I wish I knew what to make of all this.  

J.R.

---

### Post by thodges999 on 2010-06-03
Hi
Thanks for all that, I'll have a look in the morning.
The code
```

cupsctl LogLevel=debug
```
should just set your error log to debug mode which gives more info and no output would be seen.

The other two commands should be run seperately;
first
```
tail -n 20 /var/log/syslog
``` which should give an output then
```
dmesg | tail
```

could you post these results please.

If you don't have the permissions to open a file you need to open it as 'root' i.e
```
sudo gedit /var/log/cups/error_log
``` but you've given me the info anyway.

---

### Post by thodges999 on 2010-06-04
jrd43
I am looking through the info you sent me and found a couple of error messages that may be the problem. However one of them I can replicate on my machine and it still prints. Just to ensure it isn't the reason enter ```
sudo modprobe parport_pc
```which provides parallel port functionality. Try this first and then run ```
lsmod
``` to check it has loaded.

The other strange thing is that your 'localhost' address appears to be 0.0.0.0 when the default value is 127.0.0.1 (This is your computers internal address aka loopback) although research indicates that this may not be a problem.

Could you run ifconfig and post the output as it may clear this query. Could you also try typing 127.0.0.1:631 into your browser and see what you get. Then try 0.0.0.1:631.

You might also try intalling a different driver (use the CUPS + Gutenprint)

Finally the troubleshoot info is not complete (or is the wrong output) it should start with Page 1 (Scheduler not running?). Could you try this again please. You should get to a screen that says Sorry! and it has a button to Save which saves the full diagnostic report.

By the way I am using [[COLOR="Red"]https://wiki.ubuntu.com/DebuggingPrintingProblems[/COLOR]]("https://wiki.ubuntu.com/DebuggingPrintingProblems") to help if this makes it clearer.

I do like a puzzle!

---

### Post by moth17 on 2010-06-04
> **thodges999 said:**
> Delete the printer from printer config again and turn it off, unplug the usb connection and reboot your computer.

Then plug in the usb connection (with the printer still turned off) and run **tail -n 20 /var/log/syslog** (this will show the last 20 entries in your syslog file, something I've just learned and gives more info than using dmesg) 

In terminal run **ls -l /dev/bus/usb/002/005** (check in lsusb that your parallel port is still Bus 005 Device 002) Sorry I think it should be **ls -l /dev/bus/usb/005/002**

hafiz@hafiz-desktop:~$ tail -n 20 /var/log/syslog
Jun  4 18:28:08 hafiz-desktop pulseaudio[1587]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Jun  4 18:28:08 hafiz-desktop pulseaudio[1587]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/hafiz-desktop:@/tmp/.ICE-unix/1508,unix/hafiz-desktop:/tmp/.ICE-unix/1508"): initialization failed.
Jun  4 18:29:04 hafiz-desktop AptDaemon: INFO: Initializing daemon
Jun  4 18:32:35 hafiz-desktop pulseaudio[1587]: ratelimit.c: 2 events suppressed
Jun  4 18:35:04 hafiz-desktop AptDaemon: INFO: Quiting due to inactivity
Jun  4 18:35:04 hafiz-desktop AptDaemon: INFO: Shutdown was requested
Jun  4 18:40:43 hafiz-desktop kernel: [  798.868531] usb 5-1: new full speed USB device using uhci_hcd and address 2
Jun  4 18:40:44 hafiz-desktop kernel: [  799.064181] usb 5-1: configuration #1 chosen from 1 choice
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5/5-1
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: Device vendor/product is 067B:2305
Jun  4 18:40:44 hafiz-desktop kernel: [  799.094209] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
Jun  4 18:40:44 hafiz-desktop kernel: [  799.094250] usbcore: registered new interface driver usblp
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/usb/lp0
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: failed to claim interface
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: failed to claim interface
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5/5-1
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: MFG:HEWLETT-PACKARD MDL:DESKJET 960C SERN:MY13P1D0RFRO serial:
Jun  4 18:40:45 hafiz-desktop kernel: [  800.282554] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1


hafiz@hafiz-desktop:~$ ls -l /dev/bus/usb/002/005
ls: cannot access /dev/bus/usb/002/005: No such file or directory
hafiz@hafiz-desktop:~$ ls -l /dev/bus/usb/005/002
crw-rw-r-- 1 root lp 189, 513 2010-06-04 18:40 /dev/bus/usb/005/002

---

### Post by moth17 on 2010-06-04
> **thodges999 said:**
> Moth17
In your post 33 back in March you gave a long output from Troubleshooting Printing (which I have only just discovered!) and I have compared this with mine.

In may not be relevant but part way through it refers to a DESKJET 990 driver when I believe you are using a 960, do you have the correct driver in case this makes a difference.

It could be useful if you could install your printer and then run this again answering yes to whether the test page printed OK even if it didn't and post the result (put it inside code tags # so it doesn't fill the page)

Could you also post the contents of /etc/cups/printers.conf.

There appears to be an error just over halfway down which results in the printer appearing to be busy but I don't understand what is causing this yet.


Drivers:

HP Deskjet 960c hpijs, 3.10.2[en] (recommended)
HP Deskjet 960C - CUPS+Gutenprint v5.2.5 Simplified
HP Deskjet 960C - CUPS+Gutenprint v5.2.5 [en]
HP Deskjet 960C Foomatic/chp220 [en]
HP Deskjet 960C Foomatic/pcl3 [en]

I always select the first one...

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest HP-Deskjet-960c (default)>,
 'cups_instance': None,
 'cups_queue': 'HP-Deskjet-960c',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/usb/lp0',
                       'printer-info': u'HP Deskjet 960c',
                       'printer-is-shared': True,
                       'printer-location': u'Home',
                       'printer-make-and-model': u'HP Deskjet 960c hpijs, 3.10.2',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8556572,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP-Deskjet-960c'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'parallel:/dev/usb/lp0',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'iso_a6_105x148mm',
                                                     u'jis_b5_182x257mm',
                                                     u'adobe_CDDVD80_83.6083x83.6083mm',
                                                     u'adobe_CDDVD120_5x5in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_legal_8.5x14in',
                                                     u'adobe_Oufuku_7.875x5.83333in',
                                                     u'roc_16k_7.75x10.75in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'custom_min_1x4in',
                                                     u'custom_max_13x19in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'HP Deskjet 960c',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'Home',
                                 'printer-make-and-model': u'HP Deskjet 960c hpijs, 3.10.2',
                                 'printer-more-info': u'http://localhost:631/printers/HP-Deskjet-960c',
                                 'printer-name': u'HP-Deskjet-960c',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 4,
                                 'printer-state-change-time': 1275703503,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8556572,
                                 'printer-up-time': 1275703512,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/HP-Deskjet-960c'],
                                 'queued-job-count': 1,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'DryTime': u'Zero',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': '',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 28422L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': '04/Jun/2010:19:05:49 +0000',
 'test_page_job_id': [56],
 'test_page_job_status': [(True,
                           56,
                           'HP-Deskjet-960c',
                           'Test Page',
                           'Pending',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 56,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/56',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'hafiz',
                            'job-printer-up-time': 1275703563,
                            'job-printer-uri': u'ipp://hafiz-desktop:631/printers/HP-Deskjet-960c',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 3,
                            'job-state-reasons': u'none',
                            'job-uri': u'ipp://localhost:631/jobs/56',
                            'job-uuid': u'urn:uuid:e6365595-ead4-3c9a-586d-749e348c36dc',
                            'printer-uri': u'ipp://localhost/printers/HP-Deskjet-960c',
                            'time-at-completed': None,
                            'time-at-creation': 1275703549,
                            'time-at-processing': None})],
 'test_page_successful': True}
Page 9 (Error log fetch):
{'error_log': ['D [04/Jun/2010:19:05:43 -0700] [Job 54] Unloading...',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1',
               'D [04/Jun/2010:19:05:43 -0700] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2010:19:05:43 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1',
               'D [04/Jun/2010:19:05:43 -0700] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2010:19:05:43 -0700] [Job 24] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 28] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 29] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 30] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 31] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 32] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 34] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 40] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 41] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 42] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 43] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 44] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 46] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 47] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 48] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 49] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 50] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 51] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 52] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 53] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 54] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 1.1 Create-Printer-Subscription 1',
               'D [04/Jun/2010:19:05:43 -0700] Create-Printer-Subscription /',
               'D [04/Jun/2010:19:05:43 -0700] cupsdCreateSubscription(con=0x21a18e20(13), uri="/")',
               'D [04/Jun/2010:19:05:43 -0700] pullmethod="ippget"',
               'D [04/Jun/2010:19:05:43 -0700] notify-lease-duration=86400',
               'D [04/Jun/2010:19:05:43 -0700] notify-time-interval=0',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [04/Jun/2010:19:05:43 -0700] Added subscription 292 for server',
               'D [04/Jun/2010:19:05:43 -0700] cupsdMarkDirty(-----S)',
               'D [04/Jun/2010:19:05:43 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:45 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:45 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:45 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:45 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:45 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 15 POST /printers/HP-Deskjet-960c HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 15 1.1 Print-Job 1',
               'D [04/Jun/2010:19:05:49 -0700] Print-Job ipp://localhost/printers/HP-Deskjet-960c',
               'D [04/Jun/2010:19:05:49 -0700] [Job ???] Auto-typing file...',
               'I [04/Jun/2010:19:05:49 -0700] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdMarkDirty(----J-)',
               'D [04/Jun/2010:19:05:49 -0700] add_job: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Adding default job-sheets values "none,none"...',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] Adding start banner page "none".',
               'D [04/Jun/2010:19:05:49 -0700] cupsdMarkDirty(-----S)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdMarkDirty(----J-)',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] Adding end banner page "none".',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] File of type application/vnd.cups-banner queued by "hafiz".',
               'D [04/Jun/2010:19:05:49 -0700] [Job 56] hold_until=0',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] Queued on "HP-Deskjet-960c" by "hafiz".',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-Deskjet-960c) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:49 -0700] cupsdCloseClient: 16',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:49 -0700] cupsdCloseClient: 17',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:49 -0700] cupsdCloseClient: 19',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 1.1 Get-Job-Attributes 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Job-Attributes ipp://localhost/jobs/56',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/56) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:50 -0700] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:50 -0700] cupsdCloseClient: 16',
               'D [04/Jun/2010:19:05:59 -0700] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [04/Jun/2010:19:05:59 -0700] cupsdReadClient: 16 POST /jobs/ HTTP/1.1',
               'D [04/Jun/2010:19:05:59 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:59 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:59 -0700] cupsdReadClient: 16 1.1 Cancel-Job 1',
               'D [04/Jun/2010:19:05:59 -0700] Cancel-Job ipp://localhost/jobs/55',
               'D [04/Jun/2010:19:05:59 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:59 -0700] cupsdMarkDirty(-----S)',
               'I [04/Jun/2010:19:05:59 -0700] [Job 55] Job canceled by "hafiz"',
               'D [04/Jun/2010:19:05:59 -0700] cupsdMarkDirty(----J-)',
               'I [04/Jun/2010:19:05:59 -0700] [Job 55] Canceled by "hafiz".',
               'D [04/Jun/2010:19:05:59 -0700] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/55) from localhost',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Process is dying with "Caught termination signal: Job canceled',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] ", exit stat 0',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Cleaning up...',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Killing kid3',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Process is dying with "Caught termination signal: Job canceled',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] ", exit stat 0',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Cleaning up...',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Killing kid4',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Process is dying with "Caught termination signal: Job canceled',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] ", exit stat 0',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Cleaning up...',
               'D [04/Jun/2010:19:05:59 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:00 -0700] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [04/Jun/2010:19:06:00 -0700] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [04/Jun/2010:19:06:00 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:00 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:06:00 -0700] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:06:00 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:06:00 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:06:00 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:06:00 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:00 -0700] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [04/Jun/2010:19:06:00 -0700] cupsdCloseClient: 17',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 1.1 Get-Job-Attributes 1',
               'D [04/Jun/2010:19:06:03 -0700] Get-Job-Attributes ipp://localhost/jobs/56',
               'D [04/Jun/2010:19:06:03 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/56) from localhost',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 1.1 Cancel-Subscription 1',
               'D [04/Jun/2010:19:06:03 -0700] Cancel-Subscription /',
               'D [04/Jun/2010:19:06:03 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:06:03 -0700] cupsdMarkDirty(-----S)',
               'D [04/Jun/2010:19:06:03 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 17 GET /admin/log/error_log HTTP/1.1',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```


hafiz@hafiz-desktop:~$  /etc/cups/printers.conf
bash: /etc/cups/printers.conf: Permission denied


Mr Hodges, you make any sense of that?

---

### Post by thodges999 on 2010-06-05
> **moth17 said:**
> hafiz@hafiz-desktop:~$ tail -n 20 /var/log/syslog
Jun  4 18:28:08 hafiz-desktop pulseaudio[1587]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Jun  4 18:28:08 hafiz-desktop pulseaudio[1587]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/hafiz-desktop:@/tmp/.ICE-unix/1508,unix/hafiz-desktop:/tmp/.ICE-unix/1508"): initialization failed.
Jun  4 18:29:04 hafiz-desktop AptDaemon: INFO: Initializing daemon
Jun  4 18:32:35 hafiz-desktop pulseaudio[1587]: ratelimit.c: 2 events suppressed
Jun  4 18:35:04 hafiz-desktop AptDaemon: INFO: Quiting due to inactivity
Jun  4 18:35:04 hafiz-desktop AptDaemon: INFO: Shutdown was requested
Jun  4 18:40:43 hafiz-desktop kernel: [  798.868531] usb 5-1: new full speed USB device using uhci_hcd and address 2
Jun  4 18:40:44 hafiz-desktop kernel: [  799.064181] usb 5-1: configuration #1 chosen from 1 choice
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5/5-1
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: Device vendor/product is 067B:2305
Jun  4 18:40:44 hafiz-desktop kernel: [  799.094209] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
Jun  4 18:40:44 hafiz-desktop kernel: [  799.094250] usbcore: registered new interface driver usblp
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: add /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/usb/lp0
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: failed to claim interface
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: failed to claim interface
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.2/usb5/5-1
Jun  4 18:40:44 hafiz-desktop udev-configure-printer: MFG:HEWLETT-PACKARD MDL:DESKJET 960C SERN:MY13P1D0RFRO serial:
Jun  4 18:40:45 hafiz-desktop kernel: [  800.282554] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1


hafiz@hafiz-desktop:~$ ls -l /dev/bus/usb/002/005
ls: cannot access /dev/bus/usb/002/005: No such file or directory
hafiz@hafiz-desktop:~$ ls -l /dev/bus/usb/005/002
crw-rw-r-- 1 root lp 189, 513 2010-06-04 18:40 /dev/bus/usb/005/002

The output from **tail -n 20 /var/log/syslog** shows a printer being added on usb bus 5 dev(ice)/address 2 which ties in with lsusb. The error messages are the same as on my system and I don't believe affect printing.

The difference in yours are as follows;
1.You are using uhci_hcd driver whereas I am using ehci_hcd, but this appears to be USB 1 v USB 2 so shouldn't affect printing although may be an issue if you connect high speed drives/memory.
2. You actually get a printer reference which I don't but research shows others do too.
3. I don't have the references to usbcore or usbfs but I don't think these are curently the issue. Please run **lsmod** and post. 

The output from **ls -l /dev/bus/usb/005/002** is showing the file details of usb bus 5 address 2 (your printer) but the difference from mine is that the first few characters which define the permissions are crw-rw-r**[COLOR="Red"]w[/COLOR]**-. I've highlighted the difference.

This **[COLOR="Red"]w[/COLOR]** is the general write permission for everyone (the first is for root and the second for group) and may prevent things working although you should be a member of the lp group anyway. In order to test if it is permissions enter the following in Terminal
```
echo "This is a test" > test.txt
sudo lpr test.txt 
```

After all the testing on my setup it wouldn't print this morning but while the printer was turned on I unplugged and plugged back in and it then printed. Go figure!

---

### Post by thodges999 on 2010-06-05
> **moth17 said:**
> Drivers:

HP Deskjet 960c hpijs, 3.10.2[en] (recommended)
HP Deskjet 960C - CUPS+Gutenprint v5.2.5 Simplified
HP Deskjet 960C - CUPS+Gutenprint v5.2.5 [en]
HP Deskjet 960C Foomatic/chp220 [en]
HP Deskjet 960C Foomatic/pcl3 [en]

I always select the first one...

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest HP-Deskjet-960c (default)>,
 'cups_instance': None,
 'cups_queue': 'HP-Deskjet-960c',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/usb/lp0',
                       'printer-info': u'HP Deskjet 960c',
                       'printer-is-shared': True,
                       'printer-location': u'Home',
                       'printer-make-and-model': u'HP Deskjet 960c hpijs, 3.10.2',
                       'printer-state': 4,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8556572,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HP-Deskjet-960c'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'parallel:/dev/usb/lp0',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_5x7_5x7in',
                                                     u'na_index-4x6_4x6in',
                                                     u'na_index-3x5_3x5in',
                                                     u'na_index-5x8_5x8in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a6_105x148mm',
                                                     u'iso_a6_105x148mm',
                                                     u'jis_b5_182x257mm',
                                                     u'adobe_CDDVD80_83.6083x83.6083mm',
                                                     u'adobe_CDDVD120_5x5in',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_c6_114x162mm',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'jpn_hagaki_100x148mm',
                                                     u'na_legal_8.5x14in',
                                                     u'adobe_Oufuku_7.875x5.83333in',
                                                     u'roc_16k_7.75x10.75in',
                                                     u'na_foolscap_8.5x13in',
                                                     u'custom_min_1x4in',
                                                     u'custom_max_13x19in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'HP Deskjet 960c',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'Home',
                                 'printer-make-and-model': u'HP Deskjet 960c hpijs, 3.10.2',
                                 'printer-more-info': u'http://localhost:631/printers/HP-Deskjet-960c',
                                 'printer-name': u'HP-Deskjet-960c',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 4,
                                 'printer-state-change-time': 1275703503,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8556572,
                                 'printer-up-time': 1275703512,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/HP-Deskjet-960c'],
                                 'queued-job-count': 1,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'DryTime': u'Zero',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 6 (Local or remote?):
{'printer_is_remote': False}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': '',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 28422L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': '04/Jun/2010:19:05:49 +0000',
 'test_page_job_id': [56],
 'test_page_job_status': [(True,
                           56,
                           'HP-Deskjet-960c',
                           'Test Page',
                           'Pending',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 56,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/56',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'hafiz',
                            'job-printer-up-time': 1275703563,
                            'job-printer-uri': u'ipp://hafiz-desktop:631/printers/HP-Deskjet-960c',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 3,
                            'job-state-reasons': u'none',
                            'job-uri': u'ipp://localhost:631/jobs/56',
                            'job-uuid': u'urn:uuid:e6365595-ead4-3c9a-586d-749e348c36dc',
                            'printer-uri': u'ipp://localhost/printers/HP-Deskjet-960c',
                            'time-at-completed': None,
                            'time-at-creation': 1275703549,
                            'time-at-processing': None})],
 'test_page_successful': True}
Page 9 (Error log fetch):
{'error_log': ['D [04/Jun/2010:19:05:43 -0700] [Job 54] Unloading...',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1',
               'D [04/Jun/2010:19:05:43 -0700] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2010:19:05:43 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 1.1 Get-Jobs 1',
               'D [04/Jun/2010:19:05:43 -0700] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2010:19:05:43 -0700] [Job 24] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 28] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 29] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 30] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 31] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 32] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 34] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 40] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 41] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 42] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 43] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 44] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 46] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 47] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 48] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 49] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 50] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 51] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 52] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 53] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] [Job 54] Loading attributes...',
               'D [04/Jun/2010:19:05:43 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:43 -0700] cupsdReadClient: 13 1.1 Create-Printer-Subscription 1',
               'D [04/Jun/2010:19:05:43 -0700] Create-Printer-Subscription /',
               'D [04/Jun/2010:19:05:43 -0700] cupsdCreateSubscription(con=0x21a18e20(13), uri="/")',
               'D [04/Jun/2010:19:05:43 -0700] pullmethod="ippget"',
               'D [04/Jun/2010:19:05:43 -0700] notify-lease-duration=86400',
               'D [04/Jun/2010:19:05:43 -0700] notify-time-interval=0',
               'D [04/Jun/2010:19:05:43 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [04/Jun/2010:19:05:43 -0700] Added subscription 292 for server',
               'D [04/Jun/2010:19:05:43 -0700] cupsdMarkDirty(-----S)',
               'D [04/Jun/2010:19:05:43 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [04/Jun/2010:19:05:43 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:45 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:45 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:45 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:45 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:45 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 15 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 15 POST /printers/HP-Deskjet-960c HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 15 1.1 Print-Job 1',
               'D [04/Jun/2010:19:05:49 -0700] Print-Job ipp://localhost/printers/HP-Deskjet-960c',
               'D [04/Jun/2010:19:05:49 -0700] [Job ???] Auto-typing file...',
               'I [04/Jun/2010:19:05:49 -0700] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdMarkDirty(----J-)',
               'D [04/Jun/2010:19:05:49 -0700] add_job: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Adding default job-sheets values "none,none"...',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] Adding start banner page "none".',
               'D [04/Jun/2010:19:05:49 -0700] cupsdMarkDirty(-----S)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdMarkDirty(----J-)',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] Adding end banner page "none".',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] File of type application/vnd.cups-banner queued by "hafiz".',
               'D [04/Jun/2010:19:05:49 -0700] [Job 56] hold_until=0',
               'I [04/Jun/2010:19:05:49 -0700] [Job 56] Queued on "HP-Deskjet-960c" by "hafiz".',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/HP-Deskjet-960c) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 19 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 17 1.1 Get-Jobs 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Jobs ipp://localhost/printers/',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:49 -0700] cupsdCloseClient: 16',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:49 -0700] cupsdCloseClient: 17',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 19 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:49 -0700] cupsdCloseClient: 19',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 13 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:05:49 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:49 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:49 -0700] cupsdReadClient: 16 1.1 Get-Job-Attributes 1',
               'D [04/Jun/2010:19:05:49 -0700] Get-Job-Attributes ipp://localhost/jobs/56',
               'D [04/Jun/2010:19:05:49 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/56) from localhost',
               'D [04/Jun/2010:19:05:49 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:05:50 -0700] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [04/Jun/2010:19:05:50 -0700] cupsdCloseClient: 16',
               'D [04/Jun/2010:19:05:59 -0700] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [04/Jun/2010:19:05:59 -0700] cupsdReadClient: 16 POST /jobs/ HTTP/1.1',
               'D [04/Jun/2010:19:05:59 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:05:59 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:05:59 -0700] cupsdReadClient: 16 1.1 Cancel-Job 1',
               'D [04/Jun/2010:19:05:59 -0700] Cancel-Job ipp://localhost/jobs/55',
               'D [04/Jun/2010:19:05:59 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:05:59 -0700] cupsdMarkDirty(-----S)',
               'I [04/Jun/2010:19:05:59 -0700] [Job 55] Job canceled by "hafiz"',
               'D [04/Jun/2010:19:05:59 -0700] cupsdMarkDirty(----J-)',
               'I [04/Jun/2010:19:05:59 -0700] [Job 55] Canceled by "hafiz".',
               'D [04/Jun/2010:19:05:59 -0700] Returning IPP successful-ok for Cancel-Job (ipp://localhost/jobs/55) from localhost',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Process is dying with "Caught termination signal: Job canceled',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] ", exit stat 0',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Cleaning up...',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Killing kid3',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Process is dying with "Caught termination signal: Job canceled',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] ", exit stat 0',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Cleaning up...',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Killing kid4',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Process is dying with "Caught termination signal: Job canceled',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] ", exit stat 0',
               'D [04/Jun/2010:19:05:59 -0700] [Job 55] Cleaning up...',
               'D [04/Jun/2010:19:05:59 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:00 -0700] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [04/Jun/2010:19:06:00 -0700] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [04/Jun/2010:19:06:00 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:00 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:06:00 -0700] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [04/Jun/2010:19:06:00 -0700] Get-Notifications /',
               'D [04/Jun/2010:19:06:00 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:06:00 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [04/Jun/2010:19:06:00 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:00 -0700] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [04/Jun/2010:19:06:00 -0700] cupsdCloseClient: 17',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 1.1 Get-Job-Attributes 1',
               'D [04/Jun/2010:19:06:03 -0700] Get-Job-Attributes ipp://localhost/jobs/56',
               'D [04/Jun/2010:19:06:03 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/56) from localhost',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAuthorize: No authentication data provided.',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 13 1.1 Cancel-Subscription 1',
               'D [04/Jun/2010:19:06:03 -0700] Cancel-Subscription /',
               'D [04/Jun/2010:19:06:03 -0700] cupsdIsAuthorized: requesting-user-name="hafiz"',
               'D [04/Jun/2010:19:06:03 -0700] cupsdMarkDirty(-----S)',
               'D [04/Jun/2010:19:06:03 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [04/Jun/2010:19:06:03 -0700] cupsdReadClient: 17 GET /admin/log/error_log HTTP/1.1',
               'D [04/Jun/2010:19:06:03 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [04/Jun/2010:19:06:03 -0700] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```


hafiz@hafiz-desktop:~$  /etc/cups/printers.conf
bash: /etc/cups/printers.conf: Permission denied


Mr Hodges, you make any sense of that?

I'm getting better at reading these files:)

Under Page 4 the 'printer-state' is 4 which should be 3(idle) (and was in your original post) and as far as I can work out is actually idle-held which is waiting for something to happen to release the hold.

With regard to the error log it seems that you didn't wait long enough for the test page to print as the reason for non-printing is shown as you cancelling it.

Given the earlier error log file content I would suggest the following;

1. Run **cupsctl LogLevel=debug** (This puts the error log in debug mode).
2. Remove the existing printer setup and reboot the computer with the printer disconnected.
3. Reinstall using HP Deskjet 960C - CUPS+Gutenprint v5.2.5 [en] drivers and print test page. Wait for 30 secs before aborting (unless success!!)
4. Reboot the computer
5. With the printer on disconnect and reconnect the USB cable
6. Run **lsusb**
7. Run **dmesg|tail**
8. Run **lsmod**
9. From System, Admin, Printing, Print test page. Wait for 30 secs before aborting (unless success!!)
10. Run **sudo gedit /var/log/cups/error_log** and post output 
10. Run **sudo gedit /etc/cups/printers.conf** and post output

Thanks for your patience.

---

### Post by jrd43 on 2010-06-05
thodges999....

Okay, so I'm re-following the steps from post 65....

Ran cupsctl LogLevel=debug

Connected and turned on printer.

Ran lsusb, with response: ```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 002 Device 004: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 002 Device 003: ID 0518:0001 EzKEY Corp. USB to PS2 Adaptor v1.09
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Ran lsmod, with response: ```
Module                  Size  Used by
usblp                  10481  0 
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
pcmcia                 33024  0 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
iwl3945                68727  0 
nouveau               467048  2 
iwlcore               105922  1 iwl3945
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              204922  2 iwl3945,iwlcore
tifm_7xx1               3690  0 
drm                   162471  4 nouveau,ttm,drm_kms_helper
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
usbhid                 36110  0 
hid                    67032  1 usbhid
psmouse                63245  0 
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core               6045  1 tifm_7xx1
led_class               2864  3 iwl3945,iwlcore,sdhci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24177  0 
agpgart                31724  3 ttm,drm,intel_agp
i2c_algo_bit            5028  1 nouveau
cfg80211              126485  3 iwl3945,iwlcore,mac80211
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
e1000e                119856  0 

```Ran gedit var/log/cups/error_log.  Saved file, tried to attach, this time it told me "invalid file."  Tried posting response here in code, but WAY too large.  Do you need it?  Is there something I should look for in it?

Ran tail -n 20 /var/log/syslog, with response: ```
Jun  5 12:53:08 jr-laptop udev-configure-printer: URI of detected printer: usb://NEC/SuperScript%20860, normalized: nec superscript 860
Jun  5 12:53:08 jr-laptop udev-configure-printer: Queue ipp://localhost:631/printers/SuperScript-860 has matching device URI
Jun  5 12:53:08 jr-laptop udev-configure-printer: URI of print queue: parallel:/dev/usb/lp0, normalized: parallel dev usb lp0
Jun  5 12:53:08 jr-laptop udev-configure-printer: URI of detected printer: usb://NEC/SuperScript%20860, normalized: nec superscript 860
Jun  5 12:53:08 jr-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0
Jun  5 12:53:08 jr-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-2
Jun  5 12:53:08 jr-laptop udev-configure-printer: Device vendor/product is 067B:2305
Jun  5 12:53:08 jr-laptop udev-configure-printer: failed to claim interface
Jun  5 12:53:08 jr-laptop udev-configure-printer: failed to claim interface
Jun  5 12:53:08 jr-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jun  5 12:53:08 jr-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/usb/lp0
Jun  5 12:53:08 jr-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2/2-2
Jun  5 12:53:08 jr-laptop udev-configure-printer: MFG:NEC MDL:SuperScript 860 SERN:- serial:
Jun  5 12:53:09 jr-laptop kernel: [  556.194279] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Jun  5 12:53:11 jr-laptop udev-configure-printer: URI matches without serial number: usb://NEC/SuperScript%20860
Jun  5 12:53:11 jr-laptop udev-configure-printer: No serial number URI matches so using those without
Jun  5 12:53:11 jr-laptop udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Jun  5 12:53:11 jr-laptop udev-configure-printer: URI of print queue: parallel:/dev/usb/lp0, normalized: parallel dev usb lp0
Jun  5 12:53:11 jr-laptop udev-configure-printer: URI of detected printer: usb://NEC/SuperScript%20860, normalized: nec superscript 860
Jun  5 12:53:11 jr-laptop udev-configure-printer: Queue ipp://localhost:631/printers/SuperScript-860 has matching device URI

```Ran dmesg | tail, with response: ```
[  552.046964] usblp0: USB Bidirectional printer dev 6 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[  552.208817] usblp0: nonzero read bulk status received: -75
[  552.216160] hub 2-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
[  552.216170] usb 2-2: USB disconnect, address 6
[  552.216461] usblp0: removed
[  552.456083] usb 2-2: new full speed USB device using uhci_hcd and address 7
[  552.632941] usb 2-2: configuration #1 chosen from 1 choice
[  552.800914] usblp0: USB Bidirectional printer dev 7 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[  553.187996] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  556.194279] usb 2-2: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

```Did the Troubleshoot process, saved file, again too large to attach.  Copy and pasting here: ```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest SuperScript-860 (default)>,
 'cups_instance': None,
 'cups_queue': 'SuperScript-860',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/usb/lp0',
                       'printer-info': u'NEC SuperScript 860',
                       'printer-is-shared': True,
                       'printer-location': u'jr-laptop',
                       'printer-make-and-model': u'NEC SuperScript 860 Foomatic/ljet2p (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to write print data: Input/output error',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8531972,
                       'printer-uri-supported': u'ipp://localhost:631/printers/SuperScript-860'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': False,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'parallel:/dev/usb/lp0',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_ledger_11x17in',
                                                     u'iso_a3_297x420mm',
                                                     u'iso_a5_148x210mm',
                                                     u'jis_b5_182x257mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_legal_8.5x14in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'NEC SuperScript 860',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'jr-laptop',
                                 'printer-make-and-model': u'NEC SuperScript 860 Foomatic/ljet2p (recommended)',
                                 'printer-more-info': u'http://localhost:631/printers/SuperScript-860',
                                 'printer-name': u'SuperScript-860',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1275767584,
                                 'printer-state-message': u'Unable to write print data: Input/output error',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8531972,
                                 'printer-up-time': 1275768558,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/SuperScript-860'],
                                 'queued-job-count': 1,
                                 'server-is-sharing-printers': True,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'HalftoningAlgorithm': u'Standard'},
                               u'General': {u'InputSlot': u'Default',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'300x300dpi'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Printer state reasons):
{'printer-state-message': u'Unable to write print data: Input/output error',
 'printer-state-reasons': [u'none']}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '1',
                          '_remote_printers': '1',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 931239L}
Page 8 (Print test page):
{'test_page_attempted': '05/Jun/2010:13:09:44 +0000',
 'test_page_job_id': [149],
 'test_page_job_status': [(True,
                           149,
                           'SuperScript-860',
                           'Test Page',
                           'Stopped',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 149,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/149',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'jr',
                            'job-preserved': True,
                            'job-printer-state-message': u'Unable to write print data: No such device',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1275768610,
                            'job-printer-uri': u'ipp://jr-laptop:631/printers/SuperScript-860',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/149',
                            'job-uuid': u'urn:uuid:9b9f5278-9174-366d-6e12-c126b9162fc4',
                            'printer-uri': u'ipp://localhost/printers/SuperScript-860',
                            'time-at-completed': None,
                            'time-at-creation': 1275768584,
                            'time-at-processing': 1275768584})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Not busy',
               'D [05/Jun/2010:13:09:39 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Active clients',
               'D [05/Jun/2010:13:09:39 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [05/Jun/2010:13:09:39 -0700] cupsdReadClient: 19 1.1 Get-Jobs 1',
               'D [05/Jun/2010:13:09:39 -0700] Get-Jobs ipp://localhost/printers/',
               'D [05/Jun/2010:13:09:39 -0700] [Job 148] Loading attributes...',
               'D [05/Jun/2010:13:09:39 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Not busy',
               'D [05/Jun/2010:13:09:39 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Active clients',
               'D [05/Jun/2010:13:09:39 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [05/Jun/2010:13:09:39 -0700] cupsdReadClient: 19 1.1 Get-Jobs 1',
               'D [05/Jun/2010:13:09:39 -0700] Get-Jobs ipp://localhost/printers/',
               'D [05/Jun/2010:13:09:39 -0700] [Job 112] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 112] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 113] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 113] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 114] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 114] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 115] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 115] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 116] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 116] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 117] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 117] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 118] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 118] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 119] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 119] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 120] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 120] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 121] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 121] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 122] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 122] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 123] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 123] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 124] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 124] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 125] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 125] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 126] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 126] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 127] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 127] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 128] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 128] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 129] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 129] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 130] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 130] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 131] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 131] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 132] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 132] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 133] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 133] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 134] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 134] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 135] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 135] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 136] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 136] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 137] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 137] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 138] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 138] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 139] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 139] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 140] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 140] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 141] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 141] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 142] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 142] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 143] Loading attributes...',
               'E [05/Jun/2010:13:09:39 -0700] [Job 143] Unable to queue job for destination "NEC-SuperScript-860"!',
               'D [05/Jun/2010:13:09:39 -0700] [Job 144] Loading attributes...',
               'D [05/Jun/2010:13:09:39 -0700] [Job 145] Loading attributes...',
               'D [05/Jun/2010:13:09:39 -0700] [Job 146] Loading attributes...',
               'D [05/Jun/2010:13:09:39 -0700] [Job 147] Loading attributes...',
               'D [05/Jun/2010:13:09:39 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Not busy',
               'D [05/Jun/2010:13:09:39 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Active clients',
               'D [05/Jun/2010:13:09:39 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [05/Jun/2010:13:09:39 -0700] cupsdReadClient: 19 1.1 Create-Printer-Subscription 1',
               'D [05/Jun/2010:13:09:39 -0700] Create-Printer-Subscription /',
               'D [05/Jun/2010:13:09:39 -0700] cupsdCreateSubscription(con=0x21028dc8(19), uri="/")',
               'D [05/Jun/2010:13:09:39 -0700] pullmethod="ippget"',
               'D [05/Jun/2010:13:09:39 -0700] notify-lease-duration=86400',
               'D [05/Jun/2010:13:09:39 -0700] notify-time-interval=0',
               'D [05/Jun/2010:13:09:39 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [05/Jun/2010:13:09:39 -0700] Added subscription 95 for server',
               'D [05/Jun/2010:13:09:39 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:39 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [05/Jun/2010:13:09:39 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:41 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:41 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:41 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [05/Jun/2010:13:09:41 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:41 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:41 -0700] cupsdIsAuthorized: username="jr"',
               'D [05/Jun/2010:13:09:41 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:41 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAcceptClient: 20 from localhost (Domain)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 20 POST /printers/SuperScript-860 HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 20 1.1 Print-Job 1',
               'D [05/Jun/2010:13:09:44 -0700] Print-Job ipp://localhost/printers/SuperScript-860',
               'D [05/Jun/2010:13:09:44 -0700] [Job ???] Auto-typing file...',
               'I [05/Jun/2010:13:09:44 -0700] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(----J-)',
               'D [05/Jun/2010:13:09:44 -0700] add_job: requesting-user-name="jr"',
               'D [05/Jun/2010:13:09:44 -0700] Adding default job-sheets values "none,none"...',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Adding start banner page "none".',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(----J-)',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Adding end banner page "none".',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] File of type application/vnd.cups-banner queued by "jr".',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] hold_until=0',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Queued on "SuperScript-860" by "jr".',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(----J-)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] job-sheets=none,none',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] argv[0]="SuperScript-860"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] argv[1]="149"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] argv[2]="jr"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] argv[3]="Test Page"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] argv[4]="1"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] argv[5]="job-uuid=urn:uuid:9b9f5278-9174-366d-6e12-c126b9162fc4 job-originating-host-name=localhost"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] argv[6]="/var/spool/cups/d00149-001"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[10]="SERVER_ADMIN=root@jr-laptop"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[13]="TZ=America/Phoenix"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[14]="USER=root"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[17]="IPP_PORT=631"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[18]="CHARSET=utf-8"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[19]="LANG=en_US.UTF-8"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[20]="PPD=/etc/cups/ppd/SuperScript-860.ppd"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[21]="RIP_MAX_CACHE=515068k"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[24]="PRINTER_INFO=NEC SuperScript 860"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[25]="PRINTER_LOCATION=jr-laptop"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[26]="PRINTER=SuperScript-860"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[27]="CUPS_FILETYPE=document"',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] envp[28]="FINAL_CONTENT_TYPE=printer/SuperScript-860"',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Started filter /usr/lib/cups/filter/bannertops (PID 1814)',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Started filter /usr/lib/cups/filter/pstopdf (PID 1815)',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Started filter /usr/lib/cups/filter/pdftopdf (PID 1816)',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1817)',
               'I [05/Jun/2010:13:09:44 -0700] [Job 149] Started backend /usr/lib/cups/backend/parallel (PID 1818)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/SuperScript-860) from localhost',
               'D [05/Jun/2010:13:09:44 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] pstopdf 5 args: 149 jr Test Page 1 job-uuid=urn:uuid:9b9f5278-9174-366d-6e12-c126b9162fc4 job-originating-host-name=localhost',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] load_banner(filename="/var/spool/cups/d00149-001")',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] PPD: /etc/cups/ppd/SuperScript-860.ppd',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] STATE: +connecting-to-device',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] STATE: -connecting-to-device',
               'D [05/Jun/2010:13:09:44 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x4fe150)',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Page = 612x792; 18,36 to 594,756',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Getting input from file',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] foomatic-rip version 4.0.4.217 running...',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Parsing PPD file ...',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Added option PageSize',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Added option ImageableArea',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Added option PaperDimension',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Added option InputSlot',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Added option Resolution',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Added option HalftoningAlgorithm',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Added option Font',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149]',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Parameter Summary',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] -----------------',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149]',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Spooler: cups',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Printer: SuperScript-860',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Shell: /bin/bash',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] PPD file: /etc/cups/ppd/SuperScript-860.ppd',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] ATTR file:',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Printer model: NEC SuperScript 860 Foomatic/ljet2p (recommended)',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Job title: Test Page',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] File(s) to be printed:',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] <STDIN>',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149]',
               "D [05/Jun/2010:13:09:44 -0700] [Job 149] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Printing system options:',
               "D [05/Jun/2010:13:09:44 -0700] [Job 149] Pondering option 'job-uuid=urn:uuid:9b9f5278-9174-366d-6e12-c126b9162fc4'",
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Unknown option job-uuid=urn:uuid:9b9f5278-9174-366d-6e12-c126b9162fc4.',
               "D [05/Jun/2010:13:09:44 -0700] [Job 149] Pondering option 'job-originating-host-name=localhost'",
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Unknown option job-originating-host-name=localhost.',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Options from the PPD file:',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149]',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] ================================================',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149]',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] File: <STDIN>',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149]',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] ================================================',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149]',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [05/Jun/2010:13:09:44 -0700] PID 1814 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAcceptClient: 22 from localhost:631 (IPv6)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:44 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:44 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:44 -0700] cupsdCloseClient: 22',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Resolution: 300x300',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Page size: Letter',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Width: 612, height: 792, absolute margins: 18, 36, 594, 756',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Relative margins: 18, 36, 18, 36',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] PostScript to be injected:',
               'D [05/Jun/2010:13:09:44 -0700] [Job 149] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAcceptClient: 23 from localhost (Domain)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 23 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:44 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:44 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 23 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:44 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:44 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 24 1.1 Get-Jobs 1',
               'D [05/Jun/2010:13:09:44 -0700] Get-Jobs ipp://localhost/printers/',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 24 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:44 -0700] cupsdCloseClient: 24',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 24 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:44 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:44 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:44 -0700] cupsdCloseClient: 22',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1',
               'D [05/Jun/2010:13:09:44 -0700] Get-Printer-Attributes ipp://localhost/printers/SuperScript-860',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/SuperScript-860) from localhost',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:44 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:44 -0700] cupsdReadClient: 24 1.1 Get-Job-Attributes 1',
               'D [05/Jun/2010:13:09:44 -0700] Get-Job-Attributes ipp://localhost/jobs/149',
               'D [05/Jun/2010:13:09:44 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/149) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:45 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:45 -0700] cupsdIsAuthorized: username="jr"',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1',
               'D [05/Jun/2010:13:09:45 -0700] Get-Printer-Attributes ipp://localhost/printers/SuperScript-860',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/SuperScript-860) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1',
               'D [05/Jun/2010:13:09:45 -0700] Get-Printer-Attributes ipp://localhost/printers/SuperScript-860',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/SuperScript-860) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 24 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:45 -0700] cupsdCloseClient: 24',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 23 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:45 -0700] cupsdCloseClient: 23',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:45 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:45 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:45 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:45 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Jun/2010:13:09:45 -0700] PID 1815 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] Filetype: PDF',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] Storing temporary files in /var/spool/cups/tmp',
               'D [05/Jun/2010:13:09:45 -0700] PID 1816 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] File contains 1 pages',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ljet2p -dMediaPosition=0 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-UyQbLZ',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] Starting process "kid3" (generation 1)',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] Starting process "kid4" (generation 2)',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] Starting process "renderer" (generation 2)',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] JCL: \x1b%-12345X@PJL',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149] <job data>',
               'D [05/Jun/2010:13:09:45 -0700] [Job 149]',
               'D [05/Jun/2010:13:09:46 -0700] [Job 149] Read 8192 bytes of print data...',
               'E [05/Jun/2010:13:09:46 -0700] [Job 149] Unable to write print data: No such device',
               'D [05/Jun/2010:13:09:46 -0700] [Job 149] Set job-printer-state-message to "Unable to write print data: No such device", current level=ERROR',
               'D [05/Jun/2010:13:09:46 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:46 -0700] PID 1818 (/usr/lib/cups/backend/parallel) exited with no errors.',
               'D [05/Jun/2010:13:09:46 -0700] [Job 149] renderer received signal 13',
               'D [05/Jun/2010:13:09:46 -0700] [Job 149] Kid3 exit status: 1',
               'D [05/Jun/2010:13:09:46 -0700] PID 1817 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!',
               'D [05/Jun/2010:13:09:46 -0700] cupsdMarkDirty(-----S)',
               'E [05/Jun/2010:13:09:46 -0700] [Job 149] Job stopped due to filter errors; please consult the error_log file for details.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdMarkDirty(----J-)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 23 from localhost (Domain)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 23 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 1.1 Get-Jobs 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Jobs ipp://localhost/printers/',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:46 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 23 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:46 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:46 -0700] cupsdCloseClient: 21',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:46 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 23 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:46 -0700] cupsdCloseClient: 23',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Printer-Attributes ipp://localhost/printers/SuperScript-860',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/SuperScript-860) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 19 1.1 Get-Notifications 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Notifications /',
               'D [05/Jun/2010:13:09:46 -0700] cupsdIsAuthorized: username="jr"',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 23 from localhost (Domain)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 23 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Printer-Attributes ipp://jr-laptop:631/printers/SuperScript-860',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://jr-laptop:631/printers/SuperScript-860) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 23 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 23 1.1 Get-Job-Attributes 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Job-Attributes ipp://localhost/jobs/149',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/149) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 Get-Printer-Attributes 1',
               'D [05/Jun/2010:13:09:46 -0700] Get-Printer-Attributes ipp://localhost/printers/SuperScript-860',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/SuperScript-860) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:46 -0700] cupsdCloseClient: 22',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Classes 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Classes',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 25 1.1 CUPS-Get-Default 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Default',
               'D [05/Jun/2010:13:09:46 -0700] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:46 -0700] cupsdCloseClient: 21',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 21 from localhost:631 (IPv6)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 1.1 CUPS-Get-Devices 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Devices',
               'D [05/Jun/2010:13:09:46 -0700] cupsdIsAuthorized: username=""',
               'D [05/Jun/2010:13:09:46 -0700] Returning HTTP Unauthorized for CUPS-Get-Devices (no URI) from localhost',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSendHeader: 21 WWW-Authenticate: Basic realm="CUPS", trc="y"',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:46 -0700] cupsdCloseClient: 21',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 21 from localhost:631 (IPv6)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAcceptClient: 22 from localhost:631 (IPv6)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:46 -0700] cupsdCloseClient: 21',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:46 -0700] cupsdAuthorize: Authorized as root using Local',
               'D [05/Jun/2010:13:09:46 -0700] cupsdReadClient: 22 1.1 CUPS-Get-Devices 1',
               'D [05/Jun/2010:13:09:46 -0700] CUPS-Get-Devices',
               'D [05/Jun/2010:13:09:46 -0700] cupsdIsAuthorized: username="root"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] argv[0] = "/usr/lib/cups/daemon/cups-deviced"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] argv[1] = "1"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] argv[2] = "0"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] argv[3] = "2"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] argv[4] = "7"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] argv[5] = "requested-attributes=all exclude-schemes=\'beh\',\'bluetooth\',\'cups-pdf\',\'http\',\'https\',\'ipp\',\'lpd\',\'ncp\',\'parallel\',\'scsi\',\'smb\',\'snmp\',\'socket\'"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@jr-laptop"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[13] = "TZ=America/Phoenix"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[14] = "USER=root"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[17] = "IPP_PORT=631"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Local"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[23] = "SERVER_PORT=631"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[26] = "SCRIPT_NAME=/"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[28] = "REMOTE_USER=root"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[29] = "SERVER_PROTOCOL=HTTP/1.1"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[30] = "HTTP_USER_AGENT=CUPS/1.4.3"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[31] = "REQUEST_METHOD=POST"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[32] = "CONTENT_LENGTH=234"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] envp[33] = "CONTENT_TYPE=application/ipp"',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] Started /usr/lib/cups/daemon/cups-deviced (PID 1862)',
               'I [05/Jun/2010:13:09:46 -0700] Started "/usr/lib/cups/daemon/cups-deviced" (pid=1862)',
               'D [05/Jun/2010:13:09:46 -0700] cupsdSendCommand: 22 file=21',
               'D [05/Jun/2010:13:09:46 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/usb (PID 1863)',
               'D [05/Jun/2010:13:09:46 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/dnssd (PID 1864)',
               'D [05/Jun/2010:13:09:46 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/serial (PID 1865)',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] list_devices_libusb',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] usb_find_busses=5',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] usb_find_devices=10',
               'D [05/Jun/2010:13:09:46 -0700] [cups-deviced] PID 1865 (serial) exited with no errors.',
               'D [05/Jun/2010:13:09:46 -0700] [CGI] Flushed attributes...',
               'D [05/Jun/2010:13:09:46 -0700] [cups-deviced] Found device "usb://NEC/SuperScript%20860"...',
               'D [05/Jun/2010:13:09:46 -0700] Script header: Content-Type: application/ipp',
               'D [05/Jun/2010:13:09:46 -0700] Script header:',
               'D [05/Jun/2010:13:09:46 -0700] [cups-deviced] PID 1863 (usb) exited with no errors.',
               'D [05/Jun/2010:13:09:47 -0700] [Job 149] Unloading...',
               'D [05/Jun/2010:13:09:48 -0700] PID 1862 (/usr/lib/cups/daemon/cups-deviced) exited with no errors.',
               'D [05/Jun/2010:13:09:48 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:48 -0700] cupsdAcceptClient: 21 from localhost:631 (IPv6)',
               'D [05/Jun/2010:13:09:48 -0700] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:48 -0700] cupsdCloseClient: 22',
               'D [05/Jun/2010:13:09:48 -0700] cupsdReadClient: 21 POST / HTTP/1.1',
               'D [05/Jun/2010:13:09:48 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:09:48 -0700] cupsdAuthorize: No authentication data provided.',
               'D [05/Jun/2010:13:09:48 -0700] cupsdReadClient: 21 1.1 CUPS-Get-Printers 1',
               'D [05/Jun/2010:13:09:48 -0700] CUPS-Get-Printers',
               'D [05/Jun/2010:13:09:48 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [05/Jun/2010:13:09:48 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:09:48 -0700] cupsdReadClient: 21 WAITING Closing on EOF',
               'D [05/Jun/2010:13:09:48 -0700] cupsdCloseClient: 21',
               'D [05/Jun/2010:13:10:10 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:10:10 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:10:10 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'I [05/Jun/2010:13:10:10 -0700] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [05/Jun/2010:13:10:10 -0700] Saving subscriptions.conf...',
               'D [05/Jun/2010:13:10:10 -0700] cupsdSetBusyState: Active clients',
               'D [05/Jun/2010:13:10:10 -0700] Report: clients=10',
               'D [05/Jun/2010:13:10:10 -0700] Report: jobs=38',
               'D [05/Jun/2010:13:10:10 -0700] Report: jobs-active=2',
               'D [05/Jun/2010:13:10:10 -0700] Report: printers=1',
               'D [05/Jun/2010:13:10:10 -0700] Report: printers-implicit=0',
               'D [05/Jun/2010:13:10:10 -0700] Report: stringpool-string-count=2390',
               'D [05/Jun/2010:13:10:10 -0700] Report: stringpool-alloc-bytes=8176',
               'D [05/Jun/2010:13:10:10 -0700] Report: stringpool-total-bytes=51744',
               'D [05/Jun/2010:13:10:10 -0700] cupsdReadClient: 19 1.1 Get-Job-Attributes 1',
               'D [05/Jun/2010:13:10:10 -0700] Get-Job-Attributes ipp://localhost/jobs/149',
               'D [05/Jun/2010:13:10:10 -0700] [Job 149] Loading attributes...',
               'D [05/Jun/2010:13:10:10 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/149) from localhost',
               'D [05/Jun/2010:13:10:10 -0700] cupsdSetBusyState: Not busy',
               'D [05/Jun/2010:13:10:10 -0700] cupsdReadClient: 19 POST / HTTP/1.1',
               'D [05/Jun/2010:13:10:10 -0700] cupsdSetBusyState: Active clients',
               'D [05/Jun/2010:13:10:10 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [05/Jun/2010:13:10:10 -0700] cupsdReadClient: 19 1.1 Cancel-Subscription 1',
               'D [05/Jun/2010:13:10:10 -0700] Cancel-Subscription /',
               'D [05/Jun/2010:13:10:10 -0700] cupsdIsAuthorized: username="jr"',
               'D [05/Jun/2010:13:10:10 -0700] cupsdMarkDirty(-----S)',
               'D [05/Jun/2010:13:10:10 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:10:10 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [05/Jun/2010:13:10:10 -0700] cupsdSetBusyState: Dirty files',
               'D [05/Jun/2010:13:10:10 -0700] cupsdAcceptClient: 21 from localhost (Domain)',
               'D [05/Jun/2010:13:10:10 -0700] cupsdReadClient: 21 GET /admin/log/error_log HTTP/1.1',
               'D [05/Jun/2010:13:10:10 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Jun/2010:13:10:10 -0700] cupsdAuthorize: No authentication data provided.']}
Page 10 (Printer state reasons):
{'printer-state-message': u'Unable to write print data: No such device',
 'printer-state-reasons': [u'none']}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```Thus ends the instructions from posts 65/68.  

So, on to post 69.  I closed the terminal window and opened a new one.  

Ran sudo modprobe parport_pc, it asked me for a password, so I entered my usual one, it gave no response but gave me a new line to enter text.  Ran lsmod, with response: ```
Module                  Size  Used by
parport_pc             25962  0 
usblp                  10481  0 
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_hda_codec_conexant    22577  1 
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
pcmcia                 33024  0 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
joydev                  8708  0 
iwl3945                68727  0 
nouveau               467048  2 
iwlcore               105922  1 iwl3945
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              204922  2 iwl3945,iwlcore
tifm_7xx1               3690  0 
drm                   162471  4 nouveau,ttm,drm_kms_helper
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
usbhid                 36110  0 
hid                    67032  1 usbhid
psmouse                63245  0 
snd                    54148  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_core               6045  1 tifm_7xx1
led_class               2864  3 iwl3945,iwlcore,sdhci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              24177  0 
agpgart                31724  3 ttm,drm,intel_agp
i2c_algo_bit            5028  1 nouveau
cfg80211              126485  3 iwl3945,iwlcore,mac80211
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  3 parport_pc,ppdev,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
e1000e                119856  0 

```You said this was to "check it has loaded," but I don't know what I'm looking for.  I'll proceed anyway.  Ran ifconfig, with response: ```
eth0      Link encap:Ethernet  HWaddr 00:16:36:f9:87:a0  
          inet addr:70.176.188.8  Bcast:70.176.188.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fef9:87a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1804568 (1.8 MB)  TX bytes:1209128 (1.2 MB)
          Memory:84000000-84020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27494 (27.4 KB)  TX bytes:27494 (27.4 KB)

```Typed 127.0.0.1:631 in to browser and got the CUPS 1.4.3 page.  Then entered 0.0.0.1:631 and it didn't seem to do anything - just sat there.

I have tried the CUPS + Gutenprint driver before, and all it does is cause my printer to put on a fancier light show.

Hope I followed all the steps correctly.  Sorry about that error log.  I can't figure a way around it.  Glad you like puzzles, but why not settle for a jigsaw?

---

### Post by jrd43 on 2010-06-05
thodges999,

It occurred to me that you might have meant for me to enter 0.0.0.0:631 into my browser (instead of 0.0.0.1:631), so I tried that, too, and got a page that simply said "400 Bad Request."

---

### Post by thodges999 on 2010-06-06
> **jrd43 said:**
> thodges999,

It occurred to me that you might have meant for me to enter 0.0.0.0:631 into my browser (instead of 0.0.0.1:631), so I tried that, too, and got a page that simply said "400 Bad Request."

1. lsusb shows what usb devices are attached and clearly your adapter is being picked up on Bus 002 Device 005 (although in previous posts this has been a different device number) Am I right in guessing that your printer cable is connected to a USB hub and is it possible to connect it directly to a USB port on your computer for testing?

2. lsmod shows what 'modules' are loaded and you didn't have parport_pc loaded initially while I did, so for the process of elimination I got you to load it. Running sudo modprobe parport_pc loads it and when you ran lsmod again it is visible (right at the top). Unfortunately this doesn't last through a reboot but enables us to check if it makes a difference. I don't know why my system loads it as I don't have a parallel port and I'm dubious it is being used.

3. The var/log/cups/error_log gives info on what the printing process has done since the last boot and is easier to run. The troubleshoot output only gives the last few hundred lines of messages from the error log and is a bit more fiddly to achieve.

3. In a previous post your /var/log/cups/error_log contained the following lines at the beginning of the log, do they still occur?;
a) 'Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory'  You shouldn't be using hplip and this may be a hangup from before.
b) 'Listening to 0.0.0.0:631 (IPv4)'   From ifconfig your machine (localhost) address is identified internally as 127.0.0.1 as I would expect, so why would it say 0.0.0.0:631 which when you try in a browser doesn't work (well spotted there by the way)?

Run **sudo netstat -ntupl** and post the output. This will show the various connections and whether cups is on 127.0.0.1. Also reinstall CUPS, **sudo apt-get --reinstall install cups cupsys**

In order to rule this out run **sudo gedit /etc/cups/cupsd.conf** and change the line **Listen localhost:631** to **Listen 127.0.0.1:631** save, the run **sudo /etc/init.d/cups restart**

4. According to the Troubleshoot error log at 13:09:46 the print failed before anything printed '[Job 149] Unable to write print data: No such device'   which doesn't reflect the situation of a little bit being printed?
You also have several errors regarding loading of the printer queue but I don't suppose these will affect future printing.

5. tail -n 20 /var/log/syslog is the last 20 system messages and dmesg | tail is just the kernel messages (you can see one of these in syslog at [556.194279]. As with moth17 the error messages in syslog are the same as mine and so do not stop printing. dmesg | tail shows the printer disconnecting from address/(device) 006 and then 10 to 15 secs later it reconnects to address/(device) 007. Each time you unplug the USB cable and reconnect it will allocate a new address one up. Given that lsusb shows device 005 then you must have done this twice. If you are not doing it maybe there is a faulty usb connection.

6. In order to check there isn't a problem with permissions run the following one line at a time
```
echo "This is a test" > test.txt
sudo lpr test.txt
```
Does anything happen at the printer

7. Run **sudo cat /etc/cups/printers.conf** and post the output.

8. However my main thought is why should it print intermittently as you describe and I must say this doesn't sounds like a parallel/USB adapter problem? I guess what we need is as soon as you have printed something and the print stops after the top 1/4 inch of the document prints then post the output from sudo gedit /var/log/cups/error_log starting say 20 lines above where the last print job is allocated a number [JOB XXX] (this will still be several hundred lines)

The other problem with this is that as there are so many different changes or combinations that could be required it is hard to pin down what is correct. You should also reboot regularly as some of the changes may only take effect after reboot.

---

### Post by jrd43 on 2010-06-09
thodges999...

Forgive the delayed reply.  I was waiting til I had time to follow all these steps.  I also see you found my other thread soliciting new ideas.  No replies other than yours yet.  And thanks for ruling out that other idea.  It was something I had just stumbled upon.

So, in regards to post #76...

(#1) No hub.  Just an adapter connecting the USB port on my laptop to the parallel cable from the printer.

(#3) a.  I opened the error log with [OpenOffice] Word (220 pages!) and found that message about 3/4 of the way down twice, dated June 5th.  
    b. *Shrug*

Results for **sudo netstat -ntupl**: ```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      946/cupsd       
tcp6       0      0 :::631                  :::*                    LISTEN      946/cupsd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1149/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           511/avahi-daemon: r
udp        0      0 0.0.0.0:52081           0.0.0.0:*                           511/avahi-daemon: r
udp        0      0 0.0.0.0:631             0.0.0.0:*                           946/cupsd   
```Reinstalled CUPS.

Ran **sudo gedit /etc/cups/cupsd.conf,** but I don't see the line **Listen localhost:631**.  Here's what was returned:```
LogLevel debug
MaxLogSize 0
SystemGroup lpadmin
Port 631
Listen /var/run/cups/cups.sock
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
Require user @OWNER @SYSTEM
Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
  Require user @SYSTEM
  Order deny,allow
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Require user @OWNER @SYSTEM
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>
```...so I couldn't follow the rest of that instruction.

(4.) I may have been attempting a different driver at the time of the error msg for Job 149.

(5.) I have unlugged the USB cable at least twice, yes.  As you'll recall, two of those were the times I was following your instructions from post #65.  So the connection should be fine.

(I'm not sure if instructions 6-8 hinge on #3, as I was unsuccessful, but I will follow them anyhow.)

(6.) Nothing happened with command **echo "This is a text" > test.txt**, and **sudo lpr text.txt** returned: ```
lpr: Error - unable to access "text.txt" - No such file or directory
```(7.) **sudo cat /etc/cups/printers.conf **returned: ```
# Printer configuration file for CUPS v1.4.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<Printer NEC_SuperScript_860>
Info NEC SuperScript 860
Location Home
MakeModel NEC SuperScript 860 Foomatic/ljet2p (recommended)
DeviceURI parallel:/dev/usb/lp0
State Idle
StateTime 1275783010
Type 8400900
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 100 foomatic-rip
Filter application/vnd.cups-pdf 0 foomatic-rip
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```(8.) And here's a sampling of what I observe.  Just attempted test page, aka Job 176.  Printer light flashed for 10 or 15 seconds and stopped.  20 lines, as specified, of results of **sudo gedit /var/log/cups/error_log: **```
Attributes 1
D [09/Jun/2010:12:10:11 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [09/Jun/2010:12:10:11 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [09/Jun/2010:12:10:11 -0700] cupsdSetBusyState: Not busy
D [09/Jun/2010:12:10:12 -0700] cupsdAcceptClient: 13 from localhost (Domain)
D [09/Jun/2010:12:10:12 -0700] cupsdReadClient: 13 POST /printers/NEC_SuperScript_860 HTTP/1.1
D [09/Jun/2010:12:10:12 -0700] cupsdSetBusyState: Active clients
D [09/Jun/2010:12:10:12 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:10:12 -0700] cupsdReadClient: 13 1.1 Print-Job 1
D [09/Jun/2010:12:10:12 -0700] Print-Job ipp://localhost/printers/NEC_SuperScript_860
D [09/Jun/2010:12:10:12 -0700] [Job ???] Auto-typing file...
I [09/Jun/2010:12:10:12 -0700] [Job ???] Request file type is application/postscript.
D [09/Jun/2010:12:10:12 -0700] cupsdMarkDirty(----J-)
D [09/Jun/2010:12:10:12 -0700] cupsdSetBusyState: Active clients and dirty files
D [09/Jun/2010:12:10:12 -0700] add_job: requesting-user-name="jr"
D [09/Jun/2010:12:10:12 -0700] Adding default job-sheets values "none,none"...
I [09/Jun/2010:12:10:12 -0700] [Job 176] Adding start banner page "none".
D [09/Jun/2010:12:10:12 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:10:12 -0700] cupsdMarkDirty(----J-)
I [09/Jun/2010:12:10:12 -0700] [Job 176] Adding end banner page "none".
```Attempted another test page, aka Job 177, printer printed closer to 1/2" of document (exciting!), results: ```
D [09/Jun/2010:12:15:15 -0700] cupsdCloseClient: 12
D [09/Jun/2010:12:15:15 -0700] Closing client 18 after 300 seconds of inactivity...
D [09/Jun/2010:12:15:15 -0700] cupsdCloseClient: 18
D [09/Jun/2010:12:17:19 -0700] cupsdAcceptClient: 12 from localhost (Domain)
D [09/Jun/2010:12:17:19 -0700] Report: clients=1
D [09/Jun/2010:12:17:19 -0700] Report: jobs=17
D [09/Jun/2010:12:17:19 -0700] Report: jobs-active=10
D [09/Jun/2010:12:17:19 -0700] Report: printers=1
D [09/Jun/2010:12:17:19 -0700] Report: printers-implicit=0
D [09/Jun/2010:12:17:19 -0700] Report: stringpool-string-count=892
D [09/Jun/2010:12:17:19 -0700] Report: stringpool-alloc-bytes=7168
D [09/Jun/2010:12:17:19 -0700] Report: stringpool-total-bytes=20048
D [09/Jun/2010:12:17:19 -0700] cupsdReadClient: 12 POST /printers/NEC_SuperScript_860 HTTP/1.1
D [09/Jun/2010:12:17:19 -0700] cupsdSetBusyState: Active clients
D [09/Jun/2010:12:17:19 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:17:19 -0700] cupsdReadClient: 12 1.1 Print-Job 1
D [09/Jun/2010:12:17:19 -0700] Print-Job ipp://localhost/printers/NEC_SuperScript_860
D [09/Jun/2010:12:17:19 -0700] [Job ???] Auto-typing file...
I [09/Jun/2010:12:17:19 -0700] [Job ???] Request file type is application/postscript.
D [09/Jun/2010:12:17:19 -0700] cupsdMarkDirty(----J-)
D [09/Jun/2010:12:17:19 -0700] cupsdSetBusyState: Active clients and dirty files
D [09/Jun/2010:12:17:19 -0700] add_job: requesting-user-name="jr"
D [09/Jun/2010:12:17:19 -0700] Adding default job-sheets values "none,none"...
I [09/Jun/2010:12:17:19 -0700] [Job 177] Adding start banner page "none".
```I'm going to post this, reboot, and do this once or twice more.  Then I'd like to offer one more thing....

---

### Post by jrd43 on 2010-06-09
Okay.  Rebooted, got some coffee, and realized I probably wasn't copy and pasting the right portion of the error log, so I'm just going to give you the entire length from the first mention of each Job.  Attempted Job 178, printer did NOTHING this time (not even a flashing light).  In spite of this, Document Print Status still reading "Processing" after 5 minutes.  Running [B]sudo gedit /var/log/cups/error_log:
[/B]
```
I [09/Jun/2010:12:29:46 -0700] [Job 178] Adding start banner page "none".
D [09/Jun/2010:12:29:46 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:29:46 -0700] cupsdMarkDirty(----J-)
I [09/Jun/2010:12:29:46 -0700] [Job 178] Adding end banner page "none".
I [09/Jun/2010:12:29:46 -0700] [Job 178] File of type application/postscript queued by "jr".
D [09/Jun/2010:12:29:46 -0700] [Job 178] hold_until=0
I [09/Jun/2010:12:29:46 -0700] [Job 178] Queued on "NEC_SuperScript_860" by "jr".
D [09/Jun/2010:12:29:46 -0700] cupsdMarkDirty(----J-)
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:29:46 -0700] [Job 178] job-sheets=none,none
D [09/Jun/2010:12:29:46 -0700] [Job 178] argv[0]="NEC_SuperScript_860"
D [09/Jun/2010:12:29:46 -0700] [Job 178] argv[1]="178"
D [09/Jun/2010:12:29:46 -0700] [Job 178] argv[2]="jr"
D [09/Jun/2010:12:29:46 -0700] [Job 178] argv[3]="Test Page"
D [09/Jun/2010:12:29:46 -0700] [Job 178] argv[4]="1"
D [09/Jun/2010:12:29:46 -0700] [Job 178] argv[5]="PageSize=Letter job-uuid=urn:uuid:6ad45677-caf8-3198-44ba-63a4335d4c01 job-originating-host-name=localhost"
D [09/Jun/2010:12:29:46 -0700] [Job 178] argv[6]="/var/spool/cups/d00178-001"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[8]="HOME=/var/spool/cups/tmp"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[10]="SERVER_ADMIN=root@jr-laptop"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[11]="SOFTWARE=CUPS/1.4.3"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[13]="TZ=America/Phoenix"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[14]="USER=root"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[17]="IPP_PORT=631"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[18]="CHARSET=utf-8"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[19]="LANG=en_US.UTF-8"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[20]="PPD=/etc/cups/ppd/NEC_SuperScript_860.ppd"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[21]="RIP_MAX_CACHE=515068k"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[22]="CONTENT_TYPE=application/postscript"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[24]="PRINTER_INFO=NEC SuperScript 860"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[25]="PRINTER_LOCATION=Home"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[26]="PRINTER=NEC_SuperScript_860"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[27]="CUPS_FILETYPE=document"
D [09/Jun/2010:12:29:46 -0700] [Job 178] envp[28]="FINAL_CONTENT_TYPE=printer/NEC_SuperScript_860"
I [09/Jun/2010:12:29:46 -0700] [Job 178] Started filter /usr/lib/cups/filter/pstopdf (PID 1652)
I [09/Jun/2010:12:29:46 -0700] [Job 178] Started filter /usr/lib/cups/filter/pdftopdf (PID 1653)
I [09/Jun/2010:12:29:46 -0700] [Job 178] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1654)
I [09/Jun/2010:12:29:46 -0700] [Job 178] Started backend /usr/lib/cups/backend/parallel (PID 1655)
D [09/Jun/2010:12:29:46 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] [Job 178] pstopdf 6 args: 178 jr Test Page 1 PageSize=Letter job-uuid=urn:uuid:6ad45677-caf8-3198-44ba-63a4335d4c01 job-originating-host-name=localhost /var/spool/cups/d00178-001
D [09/Jun/2010:12:29:46 -0700] [Job 178] PPD: /etc/cups/ppd/NEC_SuperScript_860.ppd
D [09/Jun/2010:12:29:46 -0700] [Job 178] Resolution: 300x300
D [09/Jun/2010:12:29:46 -0700] [Job 178] Page size: Letter
D [09/Jun/2010:12:29:46 -0700] [Job 178] Getting input from file 
D [09/Jun/2010:12:29:46 -0700] [Job 178] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [09/Jun/2010:12:29:46 -0700] [Job 178] foomatic-rip version 4.0.4.217 running...
D [09/Jun/2010:12:29:46 -0700] [Job 178] Parsing PPD file ...
D [09/Jun/2010:12:29:46 -0700] [Job 178] Added option PageSize
D [09/Jun/2010:12:29:46 -0700] [Job 178] Added option ImageableArea
D [09/Jun/2010:12:29:46 -0700] [Job 178] Added option PaperDimension
D [09/Jun/2010:12:29:46 -0700] [Job 178] Added option InputSlot
D [09/Jun/2010:12:29:46 -0700] [Job 178] Added option Resolution
D [09/Jun/2010:12:29:46 -0700] [Job 178] Added option HalftoningAlgorithm
D [09/Jun/2010:12:29:46 -0700] [Job 178] Added option Font
D [09/Jun/2010:12:29:46 -0700] [Job 178] 
D [09/Jun/2010:12:29:46 -0700] [Job 178] Parameter Summary
D [09/Jun/2010:12:29:46 -0700] [Job 178] -----------------
D [09/Jun/2010:12:29:46 -0700] [Job 178] 
D [09/Jun/2010:12:29:46 -0700] [Job 178] Spooler: cups
D [09/Jun/2010:12:29:46 -0700] [Job 178] Printer: NEC_SuperScript_860
D [09/Jun/2010:12:29:46 -0700] [Job 178] Shell: /bin/bash
D [09/Jun/2010:12:29:46 -0700] [Job 178] PPD file: /etc/cups/ppd/NEC_SuperScript_860.ppd
D [09/Jun/2010:12:29:46 -0700] [Job 178] ATTR file: 
D [09/Jun/2010:12:29:46 -0700] [Job 178] Printer model: NEC SuperScript 860 Foomatic/ljet2p (recommended)
D [09/Jun/2010:12:29:46 -0700] [Job 178] Job title: Test Page
D [09/Jun/2010:12:29:46 -0700] [Job 178] File(s) to be printed:
D [09/Jun/2010:12:29:46 -0700] [Job 178] <STDIN>
D [09/Jun/2010:12:29:46 -0700] [Job 178] 
D [09/Jun/2010:12:29:46 -0700] [Job 178] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [09/Jun/2010:12:29:46 -0700] [Job 178] Printing system options:
D [09/Jun/2010:12:29:46 -0700] [Job 178] Pondering option 'job-uuid=urn:uuid:6ad45677-caf8-3198-44ba-63a4335d4c01'
D [09/Jun/2010:12:29:46 -0700] [Job 178] Unknown option job-uuid=urn:uuid:6ad45677-caf8-3198-44ba-63a4335d4c01.
D [09/Jun/2010:12:29:46 -0700] [Job 178] Pondering option 'job-originating-host-name=localhost'
D [09/Jun/2010:12:29:46 -0700] [Job 178] Unknown option job-originating-host-name=localhost.
D [09/Jun/2010:12:29:46 -0700] [Job 178] Options from the PPD file:
D [09/Jun/2010:12:29:46 -0700] [Job 178] Pondering option 'PageSize=Letter'
D [09/Jun/2010:12:29:46 -0700] [Job 178] 
D [09/Jun/2010:12:29:46 -0700] [Job 178] ================================================
D [09/Jun/2010:12:29:46 -0700] [Job 178] 
D [09/Jun/2010:12:29:46 -0700] [Job 178] File: <STDIN>
D [09/Jun/2010:12:29:46 -0700] [Job 178] 
D [09/Jun/2010:12:29:46 -0700] [Job 178] ================================================
D [09/Jun/2010:12:29:46 -0700] [Job 178] 
D [09/Jun/2010:12:29:46 -0700] [Job 178] STATE: +connecting-to-device
D [09/Jun/2010:12:29:46 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:29:46 -0700] [Job 178] STATE: -connecting-to-device
D [09/Jun/2010:12:29:46 -0700] [Job 178] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x1e7150)
D [09/Jun/2010:12:29:46 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:29:46 -0700] [Job 178] Relative margins: 18, 36, 18, 36
D [09/Jun/2010:12:29:46 -0700] [Job 178] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [09/Jun/2010:12:29:46 -0700] [Job 178] PostScript to be injected: 
D [09/Jun/2010:12:29:46 -0700] [Job 178] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [09/Jun/2010:12:29:46 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 1.1 Get-Notifications 1
D [09/Jun/2010:12:29:46 -0700] Get-Notifications /
D [09/Jun/2010:12:29:46 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 1.1 Get-Job-Attributes 1
D [09/Jun/2010:12:29:46 -0700] Get-Job-Attributes ipp://localhost/jobs/178
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/178) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAcceptClient: 28 from localhost (Domain)
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 28 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 28 1.1 Get-Printer-Attributes 1
D [09/Jun/2010:12:29:46 -0700] Get-Printer-Attributes ipp://jr-laptop:631/printers/NEC_SuperScript_860
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://jr-laptop:631/printers/NEC_SuperScript_860) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 28 WAITING Closing on EOF
D [09/Jun/2010:12:29:46 -0700] cupsdCloseClient: 28
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 WAITING Closing on EOF
D [09/Jun/2010:12:29:46 -0700] cupsdCloseClient: 27
D [09/Jun/2010:12:29:46 -0700] cupsdAcceptClient: 27 from localhost (Domain)
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 1.1 Get-Notifications 1
D [09/Jun/2010:12:29:46 -0700] Get-Notifications /
D [09/Jun/2010:12:29:46 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 Get-Printer-Attributes 1
D [09/Jun/2010:12:29:46 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 Get-Printer-Attributes 1
D [09/Jun/2010:12:29:46 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 Get-Printer-Attributes 1
D [09/Jun/2010:12:29:46 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 27 WAITING Closing on EOF
D [09/Jun/2010:12:29:46 -0700] cupsdCloseClient: 27
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Printers 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Printers
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Classes 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Classes
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Default 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Default
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [09/Jun/2010:12:29:46 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Printers 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Printers
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Classes 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Classes
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Default 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Default
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [09/Jun/2010:12:29:46 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Printers 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Printers
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Classes 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Classes
D [09/Jun/2010:12:29:46 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 POST / HTTP/1.1
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:29:46 -0700] cupsdAuthorize: No authentication data provided.
D [09/Jun/2010:12:29:46 -0700] cupsdReadClient: 12 1.1 CUPS-Get-Default 1
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Default
D [09/Jun/2010:12:29:46 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [09/Jun/2010:12:29:46 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [09/Jun/2010:12:29:46 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:29:47 -0700] PID 1652 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [09/Jun/2010:12:29:47 -0700] [Job 178] Filetype: PDF
D [09/Jun/2010:12:29:47 -0700] [Job 178] Storing temporary files in /var/spool/cups/tmp
D [09/Jun/2010:12:29:47 -0700] PID 1653 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [09/Jun/2010:12:29:48 -0700] [Job 178] File contains 1 pages
D [09/Jun/2010:12:29:48 -0700] [Job 178] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ljet2p -dMediaPosition=8 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-X8Quvy 
D [09/Jun/2010:12:29:48 -0700] [Job 178] Starting process "kid3" (generation 1)
D [09/Jun/2010:12:29:48 -0700] [Job 178] Starting process "kid4" (generation 2)
D [09/Jun/2010:12:29:48 -0700] [Job 178] Starting process "renderer" (generation 2)
D [09/Jun/2010:12:29:48 -0700] [Job 178] JCL: %-12345X@PJL
D [09/Jun/2010:12:29:48 -0700] [Job 178] <job data> 
D [09/Jun/2010:12:29:48 -0700] [Job 178] 
D [09/Jun/2010:12:29:48 -0700] [Job 178] Read 8192 bytes of print data...
I [09/Jun/2010:12:30:14 -0700] Saving job cache file "/var/cache/cups/job.cache"...
I [09/Jun/2010:12:30:14 -0700] Saving subscriptions.conf...
D [09/Jun/2010:12:30:14 -0700] cupsdSetBusyState: Printing jobs
D [09/Jun/2010:12:30:14 -0700] Closing client 16 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 16
D [09/Jun/2010:12:30:14 -0700] Closing client 17 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 17
D [09/Jun/2010:12:30:14 -0700] Closing client 18 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 18
D [09/Jun/2010:12:30:14 -0700] Closing client 19 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 19
D [09/Jun/2010:12:30:14 -0700] Closing client 20 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 20
D [09/Jun/2010:12:30:14 -0700] Closing client 21 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 21
D [09/Jun/2010:12:30:14 -0700] Closing client 22 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 22
D [09/Jun/2010:12:30:14 -0700] Closing client 23 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 23
D [09/Jun/2010:12:30:14 -0700] Closing client 24 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 24
D [09/Jun/2010:12:30:14 -0700] Closing client 25 after 300 seconds of inactivity...
D [09/Jun/2010:12:30:14 -0700] cupsdCloseClient: 25
```

Job 179 will only read "Pending" as 178 is supposedly still "Processing".  Canceling both jobs.  Attempted Jobs 180 and 181, but they will only read "Pending."  Going to reboot...

---

### Post by jrd43 on 2010-06-09
Upon reboot, before even logging in, printer did the 1/4" thing.  Immediately ran **sudo gedit /var/log/cups/error_log**, and here's a chunk of the error log: ```
I [09/Jun/2010:12:46:52 -0700] [Job 181] Started filter /usr/lib/cups/filter/pstopdf (PID 14332)
I [09/Jun/2010:12:46:52 -0700] [Job 181] Started filter /usr/lib/cups/filter/pdftopdf (PID 14333)
I [09/Jun/2010:12:46:52 -0700] [Job 181] Started filter /usr/lib/cups/filter/foomatic-rip (PID 14334)
I [09/Jun/2010:12:46:52 -0700] [Job 181] Started backend /usr/lib/cups/backend/parallel (PID 14336)
D [09/Jun/2010:12:46:52 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:46:52 -0700] cupsdMarkDirty(----J-)
D [09/Jun/2010:12:46:52 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:46:52 -0700] cupsdMarkDirty(----J-)
D [09/Jun/2010:12:46:52 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:46:52 -0700] [Job 181] job-sheets=none,none
D [09/Jun/2010:12:46:52 -0700] [Job 181] argv[0]="NEC_SuperScript_860"
D [09/Jun/2010:12:46:52 -0700] [Job 181] argv[1]="181"
D [09/Jun/2010:12:46:52 -0700] [Job 181] argv[2]="jr"
D [09/Jun/2010:12:46:52 -0700] [Job 181] argv[3]="Test Page"
D [09/Jun/2010:12:46:52 -0700] [Job 181] argv[4]="1"
D [09/Jun/2010:12:46:52 -0700] [Job 181] argv[5]="PageSize=Letter job-uuid=urn:uuid:3a37e578-079f-33cf-50e9-0876f17186c9 job-originating-host-name=localhost"
D [09/Jun/2010:12:46:52 -0700] [Job 181] argv[6]="/var/spool/cups/d00181-001"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[8]="HOME=/var/spool/cups/tmp"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[10]="SERVER_ADMIN=root@jr-laptop"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[11]="SOFTWARE=CUPS/1.4.3"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[13]="TZ=America/Phoenix"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[14]="USER=root"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [09/Jun/2010:12:46:52 -0700] [Job 181] envp[16]="CUPS_ENCRYPTION=IfRequested
```

Job 182 immediately did the 1/4" thing.  **sudo gedit /var/log/cups/error_log **chunk of results: ```
I [09/Jun/2010:12:57:15 -0700] [Job 182] Adding start banner page "none".
D [09/Jun/2010:12:57:15 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:57:15 -0700] cupsdMarkDirty(----J-)
I [09/Jun/2010:12:57:15 -0700] [Job 182] Adding end banner page "none".
I [09/Jun/2010:12:57:15 -0700] [Job 182] File of type application/postscript queued by "jr".
D [09/Jun/2010:12:57:15 -0700] [Job 182] hold_until=0
I [09/Jun/2010:12:57:15 -0700] [Job 182] Queued on "NEC_SuperScript_860" by "jr".
D [09/Jun/2010:12:57:15 -0700] cupsdMarkDirty(----J-)
D [09/Jun/2010:12:57:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [09/Jun/2010:12:57:15 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:57:15 -0700] [Job 182] job-sheets=none,none
D [09/Jun/2010:12:57:15 -0700] [Job 182] argv[0]="NEC_SuperScript_860"
D [09/Jun/2010:12:57:15 -0700] [Job 182] argv[1]="182"
D [09/Jun/2010:12:57:15 -0700] [Job 182] argv[2]="jr"
D [09/Jun/2010:12:57:15 -0700] [Job 182] argv[3]="Test Page"
D [09/Jun/2010:12:57:15 -0700] [Job 182] argv[4]="1"
D [09/Jun/2010:12:57:15 -0700] [Job 182] argv[5]="PageSize=Letter job-uuid=urn:uuid:a333a3ef-be37-36f9-72dc-cf844e17729e job-originating-host-name=localhost"
D [09/Jun/2010:12:57:15 -0700] [Job 182] argv[6]="/var/spool/cups/d00182-001"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[8]="HOME=/var/spool/cups/tmp"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[10]="SERVER_ADMIN=root@jr-laptop"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[11]="SOFTWARE=CUPS/1.4.3"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[13]="TZ=America/Phoenix"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[14]="USER=root"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[17]="IPP_PORT=631"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[18]="CHARSET=utf-8"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[19]="LANG=en_US.UTF-8"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[20]="PPD=/etc/cups/ppd/NEC_SuperScript_860.ppd"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[21]="RIP_MAX_CACHE=515068k"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[22]="CONTENT_TYPE=application/postscript"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[24]="PRINTER_INFO=NEC SuperScript 860"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[25]="PRINTER_LOCATION=Home"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[26]="PRINTER=NEC_SuperScript_860"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[27]="CUPS_FILETYPE=document"
D [09/Jun/2010:12:57:15 -0700] [Job 182] envp[28]="FINAL_CONTENT_TYPE=printer/NEC_SuperScript_860"
I [09/Jun/2010:12:57:15 -0700] [Job 182] Started filter /usr/lib/cups/filter/pstopdf (PID 1702)
I [09/Jun/2010:12:57:15 -0700] [Job 182] Started filter /usr/lib/cups/filter/pdftopdf (PID 1703)
I [09/Jun/2010:12:57:15 -0700] [Job 182] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1704)
I [09/Jun/2010:12:57:15 -0700] [Job 182] Started backend /usr/lib/cups/backend/parallel (PID 1705)
D [09/Jun/2010:12:57:15 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:57:15 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [09/Jun/2010:12:57:15 -0700] [Job 182] pstopdf 6 args: 182 jr Test Page 1 PageSize=Letter job-uuid=urn:uuid:a333a3ef-be37-36f9-72dc-cf844e17729e job-originating-host-name=localhost /var/spool/cups/d00182-001
D [09/Jun/2010:12:57:15 -0700] [Job 182] PPD: /etc/cups/ppd/NEC_SuperScript_860.ppd
D [09/Jun/2010:12:57:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [09/Jun/2010:12:57:15 -0700] [Job 182] Getting input from file 
D [09/Jun/2010:12:57:15 -0700] [Job 182] foomatic-rip version 4.0.4.217 running...
D [09/Jun/2010:12:57:15 -0700] [Job 182] Parsing PPD file ...
D [09/Jun/2010:12:57:15 -0700] [Job 182] Added option PageSize
D [09/Jun/2010:12:57:15 -0700] [Job 182] Added option ImageableArea
D [09/Jun/2010:12:57:15 -0700] [Job 182] Added option PaperDimension
D [09/Jun/2010:12:57:15 -0700] [Job 182] Added option InputSlot
D [09/Jun/2010:12:57:15 -0700] [Job 182] Added option Resolution
D [09/Jun/2010:12:57:15 -0700] [Job 182] Added option HalftoningAlgorithm
D [09/Jun/2010:12:57:15 -0700] [Job 182] Added option Font
D [09/Jun/2010:12:57:15 -0700] [Job 182] 
D [09/Jun/2010:12:57:15 -0700] [Job 182] Parameter Summary
D [09/Jun/2010:12:57:15 -0700] [Job 182] -----------------
D [09/Jun/2010:12:57:15 -0700] [Job 182] 
D [09/Jun/2010:12:57:15 -0700] [Job 182] Spooler: cups
D [09/Jun/2010:12:57:15 -0700] [Job 182] Printer: NEC_SuperScript_860
D [09/Jun/2010:12:57:15 -0700] [Job 182] Shell: /bin/bash
D [09/Jun/2010:12:57:15 -0700] [Job 182] PPD file: /etc/cups/ppd/NEC_SuperScript_860.ppd
D [09/Jun/2010:12:57:15 -0700] [Job 182] ATTR file: 
D [09/Jun/2010:12:57:15 -0700] [Job 182] Printer model: NEC SuperScript 860 Foomatic/ljet2p (recommended)
D [09/Jun/2010:12:57:15 -0700] [Job 182] Job title: Test Page
D [09/Jun/2010:12:57:15 -0700] [Job 182] File(s) to be printed:
D [09/Jun/2010:12:57:15 -0700] [Job 182] <STDIN>
D [09/Jun/2010:12:57:15 -0700] [Job 182] 
D [09/Jun/2010:12:57:15 -0700] [Job 182] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [09/Jun/2010:12:57:15 -0700] [Job 182] Printing system options:
D [09/Jun/2010:12:57:15 -0700] [Job 182] Pondering option 'job-uuid=urn:uuid:a333a3ef-be37-36f9-72dc-cf844e17729e'
D [09/Jun/2010:12:57:15 -0700] [Job 182] Unknown option job-uuid=urn:uuid:a333a3ef-be37-36f9-72dc-cf844e17729e.
D [09/Jun/2010:12:57:15 -0700] [Job 182] Pondering option 'job-originating-host-name=localhost'
D [09/Jun/2010:12:57:15 -0700] [Job 182] Unknown option job-originating-host-name=localhost.
D [09/Jun/2010:12:57:15 -0700] [Job 182] Options from the PPD file:
D [09/Jun/2010:12:57:15 -0700] [Job 182] Pondering option 'PageSize=Letter'
D [09/Jun/2010:12:57:15 -0700] [Job 182] 
D [09/Jun/2010:12:57:15 -0700] [Job 182] ================================================
D [09/Jun/2010:12:57:15 -0700] [Job 182] 
D [09/Jun/2010:12:57:15 -0700] [Job 182] File: <STDIN>
D [09/Jun/2010:12:57:15 -0700] [Job 182] 
D [09/Jun/2010:12:57:15 -0700] [Job 182] ================================================
D [09/Jun/2010:12:57:15 -0700] [Job 182] 
D [09/Jun/2010:12:57:15 -0700] [Job 182] STATE: +connecting-to-device
D [09/Jun/2010:12:57:15 -0700] [Job 182] STATE: -connecting-to-device
D [09/Jun/2010:12:57:15 -0700] cupsdMarkDirty(-----S)
D [09/Jun/2010:12:57:15 -0700] [Job 182] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x2e5150)
D [09/Jun/2010:12:57:15 -0700] [Job 182] Resolution: 300x300
D [09/Jun/2010:12:57:15 -0700] [Job 182] Page size: Letter
D [09/Jun/2010:12:57:15 -0700] [Job 182] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [09/Jun/2010:12:57:15 -0700] [Job 182] Relative margins: 18, 36, 18, 36
D [09/Jun/2010:12:57:15 -0700] [Job 182] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [09/Jun/2010:12:57:15 -0700] [Job 182] PostScript to be injected: 
D [09/Jun/2010:12:57:15 -0700] [Job 182] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
```

So, job 182 was the ideal scenario with, hopefully, all the info you require.  Also attaching a screen shot of my print queue... just because.  

And just to throw this out there, the one time I successfully printed a complete test page (the day I installed Ubuntu) was right after the first time I attempted to do so after discovering the parallel:/dev/usb/lp0 URI.  I then tried to print from OpenOffice only to have my print sit there flashing for a few minutes, at which point I began f***ing with things, and have been getting the results described above ever since.  So - is there any way to wipe all printer settings back to the way they were, fresh after the install, short of reinstalling Ubuntu?  Just a thought.

Hope your patience isn't running thin.  Wish I could buy you a beer for your efforts.

---

### Post by jrd43 on 2010-06-09
Oh, and here's that screen shot....

---

### Post by thodges999 on 2010-06-09
Hi there,
To avoid my response getting too complicated I'll reiterate the points as I go. There is a lot of info you've given me but I'll try to concentrate on what appears the most important first although I'm still concerned that all the thoughts I have would prevent printing rather than the 1/4 page you are getting?

1. Your sudo gedit /etc/cups/cupsd.conf has a significant difference to mine in that your line 4 says **Port 631** whereas mine (and the default version) says **Listen localhost:631**. Change the **Port:631** to **Listen localhost:631**, save then run sudo /etc/init.d/cups restart and see if there is any difference in your printing.

2. The **echo "This is a test" > test.txt** is just saving the words 'This is a test' to the file test.txt. In the terminal window check you are in your home directory, the command prompt should be preceeded by **'your username'@'machine name':~$** if not enter **cd ~** first.

Then run the **echo "This is a test" > test.txt** command and use the file explorer (Nautilus) to check there is a file test.txt in your Home directory, then try **sudo lpr test.txt** again.

3. I may have misled you regarding wanting 20 lines from cups error_log, what I intended was the whole log but starting 20 lines before the first line that had the job number mentioned say [JOB 182] and from there to the end.

Post #79 is interesting as it seems to be saying that just after it tries to print its waiting for a response and will give up after 5 mins which ties in with your observations, but there is no reason given!!

Your posts from the cups error_log in post #79 don't seem to be complete. The starting point may do but the end doesn't seem to go far enough, there should be some lines starting **[Job 182] Read 4096 bytes of print data...** (which you can see in the log in post #78) and going on through the printing hopefully ending with **cupsdSetBusyState: Not busy** Could you look at this again please. If you post everything after **[Job 182] Adding start banner page "none"** this should be OK.

4. I'll have a think and do some research on resetting the printer settings, reinstalling CUPS was part of that but obviously not successful.

5. I notice from your print queue that you have old prints still in there. Its probably better to purge them all. Try **sudo lprm -** (yes that is a hyphen at the end) and if that fails(?) try deleting them from the print queue manually.

I'm happy to continue helping and just hope we end up with a good result. As you may have guessed I'm getting much of my knowledge from other reading so this is also improving my skills along the way. Thanks for the beer I'll put it in the fridge for tomorrow!

---

### Post by jrd43 on 2010-06-12
Regarding #'s from post 81...

1. Followed all instructions from #1 successfully.  Damn!  No luck (Job 183).  That was exciting for a second though.  

2. Oh, okay.  I understand better what's happening here.  Ran **echo "This is a test" > test.txt** , checked home directory and file was there, ran **sudo lpr test.txt** (and, unlike last time, I entered teSt instead of teXt) and got the reply ```
lpr: Error - no default destination available.
```  Don't know what that means.

5. Purge command didn't work... ```
lprm: Missing required attributes!
``` ...so I deleted them manually.  I've done this before, though.

3. Attempted test page (Job 184).  Got the 1/4".  It seems simple, I know, but I was still a little puzzled about the start point for the error log text.  I'm confident, though, you'll see everything you want to know regarding Job 184 here.  Let me know if I'm wrong.  Error log: ```
D [11/Jun/2010:22:40:15 -0700] [Job 182] Unloading...
D [11/Jun/2010:22:40:15 -0700] [Job 183] Unloading...
D [11/Jun/2010:22:40:15 -0700] Report: clients=2
D [11/Jun/2010:22:40:15 -0700] Report: jobs=24
D [11/Jun/2010:22:40:15 -0700] Report: jobs-active=1
D [11/Jun/2010:22:40:15 -0700] Report: printers=1
D [11/Jun/2010:22:40:15 -0700] Report: printers-implicit=0
D [11/Jun/2010:22:40:15 -0700] Report: stringpool-string-count=1590
D [11/Jun/2010:22:40:15 -0700] Report: stringpool-alloc-bytes=7192
D [11/Jun/2010:22:40:15 -0700] Report: stringpool-total-bytes=33440
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 13 POST /printers/NEC_SuperScript_860 HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 13 1.1 Print-Job 1
D [11/Jun/2010:22:40:15 -0700] Print-Job ipp://localhost/printers/NEC_SuperScript_860
D [11/Jun/2010:22:40:15 -0700] [Job ???] Auto-typing file...
I [11/Jun/2010:22:40:15 -0700] [Job ???] Request file type is application/postscript.
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(----J-)
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:15 -0700] add_job: requesting-user-name="jr"
D [11/Jun/2010:22:40:15 -0700] Adding default job-sheets values "none,none"...
I [11/Jun/2010:22:40:15 -0700] [Job 184] Adding start banner page "none".
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(----J-)
I [11/Jun/2010:22:40:15 -0700] [Job 184] Adding end banner page "none".
I [11/Jun/2010:22:40:15 -0700] [Job 184] File of type application/postscript queued by "jr".
D [11/Jun/2010:22:40:15 -0700] [Job 184] hold_until=0
I [11/Jun/2010:22:40:15 -0700] [Job 184] Queued on "NEC_SuperScript_860" by "jr".
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(----J-)
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:15 -0700] [Job 184] job-sheets=none,none
D [11/Jun/2010:22:40:15 -0700] [Job 184] argv[0]="NEC_SuperScript_860"
D [11/Jun/2010:22:40:15 -0700] [Job 184] argv[1]="184"
D [11/Jun/2010:22:40:15 -0700] [Job 184] argv[2]="jr"
D [11/Jun/2010:22:40:15 -0700] [Job 184] argv[3]="Test Page"
D [11/Jun/2010:22:40:15 -0700] [Job 184] argv[4]="1"
D [11/Jun/2010:22:40:15 -0700] [Job 184] argv[5]="PageSize=Letter job-uuid=urn:uuid:3a597ba1-ed7f-34a8-54e0-f3312a9a1d76 job-originating-host-name=localhost"
D [11/Jun/2010:22:40:15 -0700] [Job 184] argv[6]="/var/spool/cups/d00184-001"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[8]="HOME=/var/spool/cups/tmp"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[10]="SERVER_ADMIN=root@jr-laptop"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[11]="SOFTWARE=CUPS/1.4.3"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[13]="TZ=America/Phoenix"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[14]="USER=root"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[17]="IPP_PORT=631"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[18]="CHARSET=utf-8"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[19]="LANG=en_US.UTF-8"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[20]="PPD=/etc/cups/ppd/NEC_SuperScript_860.ppd"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[21]="RIP_MAX_CACHE=515068k"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[22]="CONTENT_TYPE=application/postscript"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[24]="PRINTER_INFO=NEC SuperScript 860"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[25]="PRINTER_LOCATION=Home"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[26]="PRINTER=NEC_SuperScript_860"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[27]="CUPS_FILETYPE=document"
D [11/Jun/2010:22:40:15 -0700] [Job 184] envp[28]="FINAL_CONTENT_TYPE=printer/NEC_SuperScript_860"
I [11/Jun/2010:22:40:15 -0700] [Job 184] Started filter /usr/lib/cups/filter/pstopdf (PID 1992)
I [11/Jun/2010:22:40:15 -0700] [Job 184] Started filter /usr/lib/cups/filter/pdftopdf (PID 1993)
I [11/Jun/2010:22:40:15 -0700] [Job 184] Started filter /usr/lib/cups/filter/foomatic-rip (PID 1994)
I [11/Jun/2010:22:40:15 -0700] [Job 184] Started backend /usr/lib/cups/backend/parallel (PID 1995)
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [11/Jun/2010:22:40:15 -0700] [Job 184] pstopdf 6 args: 184 jr Test Page 1 PageSize=Letter job-uuid=urn:uuid:3a597ba1-ed7f-34a8-54e0-f3312a9a1d76 job-originating-host-name=localhost /var/spool/cups/d00184-001
D [11/Jun/2010:22:40:15 -0700] [Job 184] PPD: /etc/cups/ppd/NEC_SuperScript_860.ppd
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] [Job 184] Getting input from file 
D [11/Jun/2010:22:40:15 -0700] [Job 184] foomatic-rip version 4.0.4.217 running...
D [11/Jun/2010:22:40:15 -0700] [Job 184] Parsing PPD file ...
D [11/Jun/2010:22:40:15 -0700] [Job 184] Added option PageSize
D [11/Jun/2010:22:40:15 -0700] [Job 184] Added option ImageableArea
D [11/Jun/2010:22:40:15 -0700] [Job 184] Added option PaperDimension
D [11/Jun/2010:22:40:15 -0700] [Job 184] Added option InputSlot
D [11/Jun/2010:22:40:15 -0700] [Job 184] Added option Resolution
D [11/Jun/2010:22:40:15 -0700] [Job 184] Added option HalftoningAlgorithm
D [11/Jun/2010:22:40:15 -0700] [Job 184] Added option Font
D [11/Jun/2010:22:40:15 -0700] [Job 184] 
D [11/Jun/2010:22:40:15 -0700] [Job 184] Parameter Summary
D [11/Jun/2010:22:40:15 -0700] [Job 184] -----------------
D [11/Jun/2010:22:40:15 -0700] [Job 184] 
D [11/Jun/2010:22:40:15 -0700] [Job 184] Spooler: cups
D [11/Jun/2010:22:40:15 -0700] [Job 184] Printer: NEC_SuperScript_860
D [11/Jun/2010:22:40:15 -0700] [Job 184] Shell: /bin/bash
D [11/Jun/2010:22:40:15 -0700] [Job 184] PPD file: /etc/cups/ppd/NEC_SuperScript_860.ppd
D [11/Jun/2010:22:40:15 -0700] [Job 184] ATTR file: 
D [11/Jun/2010:22:40:15 -0700] [Job 184] Printer model: NEC SuperScript 860 Foomatic/ljet2p (recommended)
D [11/Jun/2010:22:40:15 -0700] [Job 184] Job title: Test Page
D [11/Jun/2010:22:40:15 -0700] [Job 184] File(s) to be printed:
D [11/Jun/2010:22:40:15 -0700] [Job 184] <STDIN>
D [11/Jun/2010:22:40:15 -0700] [Job 184] 
D [11/Jun/2010:22:40:15 -0700] [Job 184] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [11/Jun/2010:22:40:15 -0700] [Job 184] Printing system options:
D [11/Jun/2010:22:40:15 -0700] [Job 184] Pondering option 'job-uuid=urn:uuid:3a597ba1-ed7f-34a8-54e0-f3312a9a1d76'
D [11/Jun/2010:22:40:15 -0700] [Job 184] Unknown option job-uuid=urn:uuid:3a597ba1-ed7f-34a8-54e0-f3312a9a1d76.
D [11/Jun/2010:22:40:15 -0700] [Job 184] Pondering option 'job-originating-host-name=localhost'
D [11/Jun/2010:22:40:15 -0700] [Job 184] Unknown option job-originating-host-name=localhost.
D [11/Jun/2010:22:40:15 -0700] [Job 184] Options from the PPD file:
D [11/Jun/2010:22:40:15 -0700] [Job 184] Pondering option 'PageSize=Letter'
D [11/Jun/2010:22:40:15 -0700] [Job 184] 
D [11/Jun/2010:22:40:15 -0700] [Job 184] ================================================
D [11/Jun/2010:22:40:15 -0700] [Job 184] 
D [11/Jun/2010:22:40:15 -0700] [Job 184] File: <STDIN>
D [11/Jun/2010:22:40:15 -0700] [Job 184] 
D [11/Jun/2010:22:40:15 -0700] [Job 184] ================================================
D [11/Jun/2010:22:40:15 -0700] [Job 184] 
D [11/Jun/2010:22:40:15 -0700] [Job 184] STATE: +connecting-to-device
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:15 -0700] [Job 184] STATE: -connecting-to-device
D [11/Jun/2010:22:40:15 -0700] [Job 184] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x688150)
D [11/Jun/2010:22:40:15 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:15 -0700] [Job 184] Resolution: 300x300
D [11/Jun/2010:22:40:15 -0700] [Job 184] Page size: Letter
D [11/Jun/2010:22:40:15 -0700] [Job 184] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [11/Jun/2010:22:40:15 -0700] [Job 184] Relative margins: 18, 36, 18, 36
D [11/Jun/2010:22:40:15 -0700] [Job 184] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [11/Jun/2010:22:40:15 -0700] [Job 184] PostScript to be injected: 
D [11/Jun/2010:22:40:15 -0700] [Job 184] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [11/Jun/2010:22:40:15 -0700] cupsdAcceptClient: 17 from localhost (Domain)
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 17 1.1 Get-Notifications 1
D [11/Jun/2010:22:40:15 -0700] Get-Notifications /
D [11/Jun/2010:22:40:15 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 17 1.1 Get-Job-Attributes 1
D [11/Jun/2010:22:40:15 -0700] Get-Job-Attributes ipp://localhost/jobs/184
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/184) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAcceptClient: 18 from localhost (Domain)
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 18 1.1 Get-Notifications 1
D [11/Jun/2010:22:40:15 -0700] Get-Notifications /
D [11/Jun/2010:22:40:15 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAcceptClient: 19 from localhost (Domain)
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [11/Jun/2010:22:40:15 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [11/Jun/2010:22:40:15 -0700] cupsdCloseClient: 17
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [11/Jun/2010:22:40:15 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [11/Jun/2010:22:40:15 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 18 WAITING Closing on EOF
D [11/Jun/2010:22:40:15 -0700] cupsdCloseClient: 18
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Printers
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Classes
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Default
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [11/Jun/2010:22:40:15 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Printers
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Classes
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Default
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [11/Jun/2010:22:40:15 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Printers
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Classes
D [11/Jun/2010:22:40:15 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [11/Jun/2010:22:40:15 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:15 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Default
D [11/Jun/2010:22:40:15 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [11/Jun/2010:22:40:15 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [11/Jun/2010:22:40:15 -0700] cupsdSetBusyState: Printing jobs and dirty files
D [11/Jun/2010:22:40:16 -0700] PID 1992 (/usr/lib/cups/filter/pstopdf) exited with no errors.
D [11/Jun/2010:22:40:16 -0700] [Job 184] Filetype: PDF
D [11/Jun/2010:22:40:16 -0700] [Job 184] Storing temporary files in /var/spool/cups/tmp
D [11/Jun/2010:22:40:16 -0700] PID 1993 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [11/Jun/2010:22:40:16 -0700] [Job 184] File contains 1 pages
D [11/Jun/2010:22:40:16 -0700] [Job 184] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ljet2p -dMediaPosition=8 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-g4YLvU 
D [11/Jun/2010:22:40:16 -0700] [Job 184] Starting process "kid3" (generation 1)
D [11/Jun/2010:22:40:16 -0700] [Job 184] Starting process "kid4" (generation 2)
D [11/Jun/2010:22:40:16 -0700] [Job 184] Starting process "renderer" (generation 2)
D [11/Jun/2010:22:40:16 -0700] [Job 184] JCL: %-12345X@PJL
D [11/Jun/2010:22:40:16 -0700] [Job 184] <job data> 
D [11/Jun/2010:22:40:16 -0700] [Job 184] 
D [11/Jun/2010:22:40:16 -0700] [Job 184] Read 8192 bytes of print data...
E [11/Jun/2010:22:40:16 -0700] [Job 184] Unable to write print data: Input/output error
D [11/Jun/2010:22:40:16 -0700] [Job 184] Set job-printer-state-message to "Unable to write print data: Input/output error", current level=ERROR
D [11/Jun/2010:22:40:16 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:16 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:16 -0700] PID 1995 (/usr/lib/cups/backend/parallel) exited with no errors.
D [11/Jun/2010:22:40:16 -0700] [Job 184] renderer received signal 13
D [11/Jun/2010:22:40:16 -0700] [Job 184] Kid3 exit status: 1
D [11/Jun/2010:22:40:16 -0700] PID 1994 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [11/Jun/2010:22:40:16 -0700] cupsdMarkDirty(-----S)
E [11/Jun/2010:22:40:16 -0700] [Job 184] Job stopped due to filter errors; please consult the error_log file for details.
D [11/Jun/2010:22:40:16 -0700] cupsdMarkDirty(----J-)
D [11/Jun/2010:22:40:16 -0700] cupsdMarkDirty(-----S)
D [11/Jun/2010:22:40:16 -0700] cupsdAcceptClient: 16 from localhost:631 (IPv6)
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Printers
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jun/2010:22:40:16 -0700] cupsdCloseClient: 16
D [11/Jun/2010:22:40:16 -0700] cupsdAcceptClient: 16 from localhost (Domain)
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdAcceptClient: 17 from localhost (Domain)
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 16 1.1 Get-Notifications 1
D [11/Jun/2010:22:40:16 -0700] Get-Notifications /
D [11/Jun/2010:22:40:16 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 17 1.1 Get-Notifications 1
D [11/Jun/2010:22:40:16 -0700] Get-Notifications /
D [11/Jun/2010:22:40:16 -0700] cupsdIsAuthorized: requesting-user-name="jr"
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [11/Jun/2010:22:40:16 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAcceptClient: 18 from localhost (Domain)
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 18 1.1 Get-Printer-Attributes 1
D [11/Jun/2010:22:40:16 -0700] Get-Printer-Attributes ipp://jr-laptop:0/printers/NEC_SuperScript_860
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://jr-laptop:0/printers/NEC_SuperScript_860) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 18 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 18 1.1 Get-Job-Attributes 1
D [11/Jun/2010:22:40:16 -0700] Get-Job-Attributes ipp://localhost/jobs/184
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/184) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 Get-Printer-Attributes 1
D [11/Jun/2010:22:40:16 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [11/Jun/2010:22:40:16 -0700] cupsdCloseClient: 17
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Printers
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Classes
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Default
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [11/Jun/2010:22:40:16 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Printers
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Classes
D [11/Jun/2010:22:40:16 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 POST / HTTP/1.1
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Default
D [11/Jun/2010:22:40:16 -0700] CUPS-Get-Default client-error-not-found: No default printer
D [11/Jun/2010:22:40:16 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost
D [11/Jun/2010:22:40:16 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:16 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jun/2010:22:40:16 -0700] cupsdCloseClient: 16
D [11/Jun/2010:22:40:17 -0700] [Job 184] Unloading...
D [11/Jun/2010:22:40:18 -0700] cupsdAcceptClient: 16 from localhost:631 (IPv6)
D [11/Jun/2010:22:40:18 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jun/2010:22:40:18 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:18 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:18 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Devices 1
D [11/Jun/2010:22:40:18 -0700] CUPS-Get-Devices
D [11/Jun/2010:22:40:18 -0700] cupsdIsAuthorized: username=""
D [11/Jun/2010:22:40:18 -0700] Returning HTTP Unauthorized for CUPS-Get-Devices (no URI) from localhost
D [11/Jun/2010:22:40:18 -0700] cupsdSendHeader: 16 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [11/Jun/2010:22:40:18 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jun/2010:22:40:18 -0700] cupsdCloseClient: 16
D [11/Jun/2010:22:40:18 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:18 -0700] cupsdAcceptClient: 16 from localhost:631 (IPv6)
D [11/Jun/2010:22:40:18 -0700] cupsdAcceptClient: 17 from localhost:631 (IPv6)
D [11/Jun/2010:22:40:18 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jun/2010:22:40:18 -0700] cupsdCloseClient: 16
D [11/Jun/2010:22:40:18 -0700] cupsdReadClient: 17 POST / HTTP/1.1
D [11/Jun/2010:22:40:18 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:18 -0700] cupsdAuthorize: Authorized as root using Local
D [11/Jun/2010:22:40:18 -0700] cupsdReadClient: 17 1.1 CUPS-Get-Devices 1
D [11/Jun/2010:22:40:18 -0700] CUPS-Get-Devices
D [11/Jun/2010:22:40:18 -0700] cupsdIsAuthorized: username="root"
D [11/Jun/2010:22:40:18 -0700] [CGI] argv[0] = "/usr/lib/cups/daemon/cups-deviced"
D [11/Jun/2010:22:40:18 -0700] [CGI] argv[1] = "1"
D [11/Jun/2010:22:40:18 -0700] [CGI] argv[2] = "0"
D [11/Jun/2010:22:40:18 -0700] [CGI] argv[3] = "2"
D [11/Jun/2010:22:40:18 -0700] [CGI] argv[4] = "7"
D [11/Jun/2010:22:40:18 -0700] [CGI] argv[5] = "requested-attributes=all exclude-schemes='beh','bluetooth','cups-pdf','http','https','ipp','lpd','ncp','parallel','scsi','smb','snmp','socket'"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[0] = "CUPS_CACHEDIR=/var/cache/cups"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[1] = "CUPS_DATADIR=/usr/share/cups"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[2] = "CUPS_DOCROOT=/usr/share/cups/doc-root"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[3] = "CUPS_FONTPATH=/usr/share/cups/fonts"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[4] = "CUPS_REQUESTROOT=/var/spool/cups"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[5] = "CUPS_SERVERBIN=/usr/lib/cups"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[6] = "CUPS_SERVERROOT=/etc/cups"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[7] = "CUPS_STATEDIR=/var/run/cups"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[8] = "HOME=/var/spool/cups/tmp"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[10] = "SERVER_ADMIN=root@jr-laptop"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[11] = "SOFTWARE=CUPS/1.4.3"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[12] = "TMPDIR=/var/spool/cups/tmp"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[13] = "TZ=America/Phoenix"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[14] = "USER=root"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[15] = "CUPS_SERVER=/var/run/cups/cups.sock"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[16] = "CUPS_ENCRYPTION=IfRequested"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[17] = "IPP_PORT=631"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[18] = "CUPSD_AUTH_TYPE=Local"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[19] = "LANG=en_US.UTF8"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[20] = "REDIRECT_STATUS=1"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[21] = "GATEWAY_INTERFACE=CGI/1.1"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[22] = "SERVER_NAME=localhost"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[23] = "SERVER_PORT=631"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[24] = "REMOTE_ADDR=::1"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[25] = "REMOTE_HOST=localhost"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[26] = "SCRIPT_NAME=/"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[27] = "SCRIPT_FILENAME=/usr/share/cups/doc-root/"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[28] = "REMOTE_USER=root"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[29] = "SERVER_PROTOCOL=HTTP/1.1"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[30] = "HTTP_USER_AGENT=CUPS/1.4.3"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[31] = "REQUEST_METHOD=POST"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[32] = "CONTENT_LENGTH=234"
D [11/Jun/2010:22:40:18 -0700] [CGI] envp[33] = "CONTENT_TYPE=application/ipp"
D [11/Jun/2010:22:40:18 -0700] [CGI] Started /usr/lib/cups/daemon/cups-deviced (PID 2038)
I [11/Jun/2010:22:40:18 -0700] Started "/usr/lib/cups/daemon/cups-deviced" (pid=2038)
D [11/Jun/2010:22:40:18 -0700] cupsdSendCommand: 17 file=16
D [11/Jun/2010:22:40:18 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/usb (PID 2039)
D [11/Jun/2010:22:40:18 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/dnssd (PID 2040)
D [11/Jun/2010:22:40:18 -0700] [cups-deviced] Started backend /usr/lib/cups/backend/serial (PID 2041)
D [11/Jun/2010:22:40:18 -0700] [CGI] list_devices_libusb
D [11/Jun/2010:22:40:18 -0700] [CGI] usb_find_busses=5
D [11/Jun/2010:22:40:18 -0700] [CGI] usb_find_devices=10
D [11/Jun/2010:22:40:18 -0700] [cups-deviced] PID 2041 (serial) exited with no errors.
D [11/Jun/2010:22:40:18 -0700] [CGI] Flushed attributes...
D [11/Jun/2010:22:40:18 -0700] [cups-deviced] Found device "usb://NEC/SuperScript%20860"...
D [11/Jun/2010:22:40:18 -0700] Script header: Content-Type: application/ipp
D [11/Jun/2010:22:40:18 -0700] Script header: 
D [11/Jun/2010:22:40:18 -0700] [cups-deviced] PID 2039 (usb) exited with no errors.
D [11/Jun/2010:22:40:20 -0700] PID 2038 (/usr/lib/cups/daemon/cups-deviced) exited with no errors.
D [11/Jun/2010:22:40:20 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:20 -0700] cupsdReadClient: 17 WAITING Closing on EOF
D [11/Jun/2010:22:40:20 -0700] cupsdCloseClient: 17
D [11/Jun/2010:22:40:20 -0700] cupsdAcceptClient: 16 from localhost:631 (IPv6)
D [11/Jun/2010:22:40:20 -0700] cupsdReadClient: 16 POST / HTTP/1.1
D [11/Jun/2010:22:40:20 -0700] cupsdSetBusyState: Active clients and dirty files
D [11/Jun/2010:22:40:20 -0700] cupsdAuthorize: No authentication data provided.
D [11/Jun/2010:22:40:20 -0700] cupsdReadClient: 16 1.1 CUPS-Get-Printers 1
D [11/Jun/2010:22:40:20 -0700] CUPS-Get-Printers
D [11/Jun/2010:22:40:20 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [11/Jun/2010:22:40:20 -0700] cupsdSetBusyState: Dirty files
D [11/Jun/2010:22:40:20 -0700] cupsdReadClient: 16 WAITING Closing on EOF
D [11/Jun/2010:22:40:20 -0700] cupsdCloseClient: 16
I [11/Jun/2010:22:40:46 -0700] Saving job cache file "/var/cache/cups/job.cache"...
I [11/Jun/2010:22:40:46 -0700] Saving subscriptions.conf...
D [11/Jun/2010:22:40:46 -0700] cupsdSetBusyState: Not busy
```4. The goal is to uncorrupt whatever I must have done minutes after I had that complete test page, so I could re-detect and reinstall my printer entering the correct URI right off the bat.  It's so strange that for that moment I was in the same boat as everyone else who had "parallel:/dev/usb/lp0" solve all their problems, but then I was back to where I'd started - though, I don't recall if I had achieved the 1/4" before that point.  

I accidentally caught the score of the match (in progress) online a bit ago, so part of the game is spoiled for me now.  It's 11 p.m. my time and the game is being broadcast here in about 12 hours.  Here's to a friendly game!  I don't know any U.S. soccer chants, so I'll just say, "Go team."  What do they say for team England?

---

### Post by thodges999 on 2010-06-14
> **jrd43 said:**
> Regarding #'s from post 81...

1. Followed all instructions from #1 successfully.  Damn!  No luck (Job 183).  That was exciting for a second though.  

2. Oh, okay.  I understand better what's happening here.  Ran **echo "This is a test" > test.txt** , checked home directory and file was there, ran **sudo lpr test.txt** (and, unlike last time, I entered teSt instead of teXt) and got the reply ```
lpr: Error - no default destination available.
```  Don't know what that means.

5. Purge command didn't work... ```
lprm: Missing required attributes!
``` ...so I deleted them manually.  I've done this before, though.

3. Attempted test page (Job 184).  Got the 1/4".  It seems simple, I know, but I was still a little puzzled about the start point for the error log text.  I'm confident, though, you'll see everything you want to know regarding Job 184 here.  Let me know if I'm wrong. 
The goal is to uncorrupt whatever I must have done minutes after I had that complete test page, so I could re-detect and reinstall my printer entering the correct URI right off the bat.  It's so strange that for that moment I was in the same boat as everyone else who had "parallel:/dev/usb/lp0" solve all their problems, but then I was back to where I'd started - though, I don't recall if I had achieved the 1/4" before that point.  

I accidentally caught the score of the match (in progress) online a bit ago, so part of the game is spoiled for me now.  It's 11 p.m. my time and the game is being broadcast here in about 12 hours.  Here's to a friendly game!  I don't know any U.S. soccer chants, so I'll just say, "Go team."  What do they say for team England?

Sorry for the delay in responding but I've been away for a couple of days. (and missed what was seen over here as a pretty poor display by England so the chants would have been quite derogatory!)

Back to the non-partisan printing problems using your notation!

1. Try once more but change to **Listen 127.0.0.1:631**. Reboot and run **sudo netstat -ntupl** and then **cat /etc/hosts**
2. The lpr command should just send something (the test.txt file in our case) to the default printer and in my case does just that. This implies that your computer isnt finding your printer but you are able to print 1/4 page??? Try **lp test.txt** instead.
5. The purge command is```
lprm -
```I think you missed off the trailing hyphen. I'm not sure if this does any more than delete the items from the print queue as you have now done manually but for completeness try **sudo lprm -a all**

Looking through your error log are the two lines;

E [11/Jun/2010:22:40:16 -0700] [Job 184] Unable to write print data: Input/output error
D [11/Jun/2010:22:40:16 -0700] [Job 184] Set job-printer-state-message to "Unable to write print data: Input/output error", current level=ERROR

and a little later;

D [11/Jun/2010:22:40:16 -0700] PID 1994 (/usr/lib/cups/filter/foomatic-rip) stopped with status 9!
D [11/Jun/2010:22:40:16 -0700] cupsdMarkDirty(-----S)
E [11/Jun/2010:22:40:16 -0700] [Job 184] Job stopped due to filter errors; please consult the error_log file for details.

which implies that there is a problem communicating with the printer, supported by the problem with the lpr command and yet you are intermittently printing 1/4 page???? There is also an apparent 'filter error' which is related to the driver which is why I suggested the alternative driver but this has no apparent impact.

As we are not having much luck with my current approach and on the basis that you were able to print the test page prior to trying OpenOffice perhaps we should try getting OpenOffice to rectify things, Assuming you have OO 3.2 can you open Printer Administation and what does it show? (screenshot is perhaps easiest)

You could also try removing all openoffice.org programs completely, inc config files which may be causing the problem. This shouldn't be too difficult to reinstall when required. Are you OK to do this.

In addition with your printer turned off you could try installing your printer again (using another name such as NECworkingprinter) using the same parallel:/dev/usb/lp0 trick. Then delete the original installation, turn on the printer and then trying a test print to it. This should hopefully overcome any problems with the original print queue.

I don't know how much you have customised Ubuntu but it may be that reinstalling would be an easier option although it will leave us still not knowing why it happened?

One other thing, when you do System, Admin, Printing and double click on your Printer what does the Printer State say? If you then press Change next to the Device URI (which should say parallel:/dev/usb/lp0) and wait for about 10 seconds you should get a Current Device appear which has the description 'A printer connected to the parallel port', does that happen to you?

---

### Post by thodges999 on 2010-06-15
Regarding the foomatic errors and after some further research if you run ```
sudo dpkg-reconfigure foomatic-filters
``` and then select cups (press enter), then Yes (press enter), then Yes (press enter)

This will reset your foomatic installation and enable logging of it. Now print a test page again.

If you now run ```
sudo gedit /tmp/foomatic-rip.log
``` this may show what the error in foomatic is.

---

### Post by jrd43 on 2010-06-16
Oooookay.   Continuing with our anti-numerical theme...

1. Changed line four of **sudo gedit /etc/cups/cupsd.conf** to **Listen 127.0.0.1:631.  **Rebooted.  Then ran**sudo netstat -ntupl**with response: ```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      957/cupsd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1166/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           522/avahi-daemon: r
udp        0      0 0.0.0.0:631             0.0.0.0:*                           957/cupsd       
udp        0      0 0.0.0.0:55567           0.0.0.0:*                           522/avahi-daemon: r
```

Then ran **cat /etc/hosts** with response: ```
127.0.0.1    localhost
127.0.1.1    jr-laptop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

2. Checked home folder "text.txt" file is still there.  Turned on printer.  Ran **sudo lp test.txt** with response: ```
lp: Error - no default destination available.
```.  Tried **sudo lpr test.txt** once more: ```
lpr: Error - no default destination available.
```

*For the heck of it, I tried to print a test page at this point.  Job 185 caused the printer to flash a few times, them came up as "Stopped" in print queue.  Jobs 186, 187, and 188 wouldn't even cause printer to flash, so I ran the walk through diagnosis after 188 and got this (I did this many times early on, but didn't know what to do with the  info - is this just the error log?): ```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest NEC_SuperScript_860>,
 'cups_instance': None,
 'cups_queue': 'NEC_SuperScript_860',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'parallel',
 'cups_printer_dict': {'device-uri': u'parallel:/dev/usb/lp0',
                       'printer-info': u'NEC SuperScript 860',
                       'printer-is-shared': False,
                       'printer-location': u'Home',
                       'printer-make-and-model': u'NEC SuperScript 860 Foomatic/ljet2p (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to write print data: No such device',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 10498052,
                       'printer-uri-supported': u'ipp://localhost:631/printers/NEC_SuperScript_860'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': False,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.3',
                                 'device-uri': u'parallel:/dev/usb/lp0',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'media-default': u'na_letter_8.5x11in',
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'iso_a4_210x297mm',
                                                     u'na_ledger_11x17in',
                                                     u'iso_a3_297x420mm',
                                                     u'iso_a5_148x210mm',
                                                     u'jis_b5_182x257mm',
                                                     u'na_number-10_4.125x9.5in',
                                                     u'iso_c5_162x229mm',
                                                     u'iso_dl_110x220mm',
                                                     u'iso_b5_176x250mm',
                                                     u'na_monarch_3.875x7.5in',
                                                     u'na_executive_7.25x10.5in',
                                                     u'na_legal_8.5x14in'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-info': u'NEC SuperScript 860',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': False,
                                 'printer-location': u'Home',
                                 'printer-make-and-model': u'NEC SuperScript 860 Foomatic/ljet2p (recommended)',
                                 'printer-more-info': u'http://localhost:631/printers/NEC_SuperScript_860',
                                 'printer-name': u'NEC_SuperScript_860',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1276715208,
                                 'printer-state-message': u'Unable to write print data: No such device',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 10498052,
                                 'printer-up-time': 1276715223,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/NEC_SuperScript_860'],
                                 'queued-job-count': 6,
                                 'server-is-sharing-printers': True,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'Adjustment': {u'HalftoningAlgorithm': u'Standard'},
                               u'General': {u'InputSlot': u'Tray1',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'Resolution': u'300x300dpi'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Printer state reasons):
{'printer-state-message': u'Unable to write print data: No such device',
 'printer-state-reasons': [u'none']}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '1',
                          '_remote_printers': '1',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 224077L}
Page 8 (Print test page):
{'test_page_attempted': '16/Jun/2010:12:07:40 +0000',
 'test_page_job_id': [189],
 'test_page_job_status': [(True,
                           189,
                           'NEC_SuperScript_860',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 189,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/189',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'jr',
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1276715275,
                            'job-printer-uri': u'ipp://jr-laptop:0/printers/NEC_SuperScript_860',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/189',
                            'job-uuid': u'urn:uuid:dc9787eb-1f5d-3949-5c07-25799b9799b0',
                            'printer-uri': u'ipp://localhost/printers/NEC_SuperScript_860',
                            'time-at-completed': None,
                            'time-at-creation': 1276715260,
                            'time-at-processing': 1276715260})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Not busy',
               'D [16/Jun/2010:12:07:27 -0700] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Active clients',
               'D [16/Jun/2010:12:07:27 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [16/Jun/2010:12:07:27 -0700] cupsdReadClient: 26 1.1 Get-Jobs 1',
               'D [16/Jun/2010:12:07:27 -0700] Get-Jobs ipp://localhost/printers/',
               'D [16/Jun/2010:12:07:27 -0700] [Job 175] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 184] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 185] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 186] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 188] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Not busy',
               'D [16/Jun/2010:12:07:27 -0700] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Active clients',
               'D [16/Jun/2010:12:07:27 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [16/Jun/2010:12:07:27 -0700] cupsdReadClient: 26 1.1 Get-Jobs 1',
               'D [16/Jun/2010:12:07:27 -0700] Get-Jobs ipp://localhost/printers/',
               'D [16/Jun/2010:12:07:27 -0700] [Job 160] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 161] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 162] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 163] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 164] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 165] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 166] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 167] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 168] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 169] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 170] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 171] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 172] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 173] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 174] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 176] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 177] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 178] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 179] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 180] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 181] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 182] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] [Job 183] Loading attributes...',
               'D [16/Jun/2010:12:07:27 -0700] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Not busy',
               'D [16/Jun/2010:12:07:27 -0700] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Active clients',
               'D [16/Jun/2010:12:07:27 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [16/Jun/2010:12:07:27 -0700] cupsdReadClient: 26 1.1 Create-Printer-Subscription 1',
               'D [16/Jun/2010:12:07:27 -0700] Create-Printer-Subscription /',
               'D [16/Jun/2010:12:07:27 -0700] cupsdCreateSubscription(con=0x20f2c158(26), uri="/")',
               'D [16/Jun/2010:12:07:27 -0700] pullmethod="ippget"',
               'D [16/Jun/2010:12:07:27 -0700] notify-lease-duration=86400',
               'D [16/Jun/2010:12:07:27 -0700] notify-time-interval=0',
               'D [16/Jun/2010:12:07:27 -0700] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [16/Jun/2010:12:07:27 -0700] Added subscription 127 for server',
               'D [16/Jun/2010:12:07:27 -0700] cupsdMarkDirty(-----S)',
               'D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [16/Jun/2010:12:07:27 -0700] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [16/Jun/2010:12:07:27 -0700] cupsdSetBusyState: Dirty files',
               'D [16/Jun/2010:12:07:29 -0700] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:29 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [16/Jun/2010:12:07:29 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [16/Jun/2010:12:07:29 -0700] cupsdReadClient: 26 1.1 Get-Notifications 1',
               'D [16/Jun/2010:12:07:29 -0700] Get-Notifications /',
               'D [16/Jun/2010:12:07:29 -0700] cupsdIsAuthorized: username="jr"',
               'D [16/Jun/2010:12:07:29 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [16/Jun/2010:12:07:29 -0700] cupsdSetBusyState: Dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAcceptClient: 27 from localhost (Domain)',
               'D [16/Jun/2010:12:07:40 -0700] [Job 187] Unloading...',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 27 POST /printers/NEC_SuperScript_860 HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 27 1.1 Print-Job 1',
               'D [16/Jun/2010:12:07:40 -0700] Print-Job ipp://localhost/printers/NEC_SuperScript_860',
               'D [16/Jun/2010:12:07:40 -0700] [Job ???] Auto-typing file...',
               'I [16/Jun/2010:12:07:40 -0700] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(----J-)',
               'D [16/Jun/2010:12:07:40 -0700] add_job: requesting-user-name="jr"',
               'D [16/Jun/2010:12:07:40 -0700] Adding default job-sheets values "none,none"...',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Adding start banner page "none".',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(-----S)',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(----J-)',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Adding end banner page "none".',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] File of type application/vnd.cups-banner queued by "jr".',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] hold_until=0',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Queued on "NEC_SuperScript_860" by "jr".',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(----J-)',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(-----S)',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] job-sheets=none,none',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] argv[0]="NEC_SuperScript_860"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] argv[1]="189"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] argv[2]="jr"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] argv[3]="Test Page"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] argv[4]="1"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] argv[5]="job-uuid=urn:uuid:dc9787eb-1f5d-3949-5c07-25799b9799b0 job-originating-host-name=localhost"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] argv[6]="/var/spool/cups/d00189-001"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[10]="SERVER_ADMIN=root@jr-laptop"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[11]="SOFTWARE=CUPS/1.4.3"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[13]="TZ=America/Phoenix"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[14]="USER=root"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[17]="IPP_PORT=631"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[18]="CHARSET=utf-8"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[19]="LANG=en_US.UTF-8"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[20]="PPD=/etc/cups/ppd/NEC_SuperScript_860.ppd"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[21]="RIP_MAX_CACHE=515068k"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[23]="DEVICE_URI=parallel:/dev/usb/lp0"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[24]="PRINTER_INFO=NEC SuperScript 860"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[25]="PRINTER_LOCATION=Home"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[26]="PRINTER=NEC_SuperScript_860"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[27]="CUPS_FILETYPE=document"',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] envp[28]="FINAL_CONTENT_TYPE=printer/NEC_SuperScript_860"',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Started filter /usr/lib/cups/filter/bannertops (PID 3015)',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Started filter /usr/lib/cups/filter/pstopdf (PID 3016)',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Started filter /usr/lib/cups/filter/pdftopdf (PID 3017)',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Started filter /usr/lib/cups/filter/foomatic-rip (PID 3018)',
               'I [16/Jun/2010:12:07:40 -0700] [Job 189] Started backend /usr/lib/cups/backend/parallel (PID 3019)',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(-----S)',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/NEC_SuperScript_860) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] STATE: +connecting-to-device',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(-----S)',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] pstopdf 5 args: 189 jr Test Page 1 job-uuid=urn:uuid:dc9787eb-1f5d-3949-5c07-25799b9799b0 job-originating-host-name=localhost',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] PPD: /etc/cups/ppd/NEC_SuperScript_860.ppd',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] STATE: -connecting-to-device',
               'D [16/Jun/2010:12:07:40 -0700] cupsdMarkDirty(-----S)',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x125150)',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] load_banner(filename="/var/spool/cups/d00189-001")',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Getting input from file',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] foomatic-rip version 4.0.4.217 running...',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Parsing PPD file ...',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Page = 612x792; 18,36 to 594,756',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Added option PageSize',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Added option ImageableArea',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Added option PaperDimension',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Added option InputSlot',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Added option Resolution',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Added option HalftoningAlgorithm',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Added option Font',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189]',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Parameter Summary',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] -----------------',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189]',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Spooler: cups',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Printer: NEC_SuperScript_860',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Shell: /bin/bash',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] PPD file: /etc/cups/ppd/NEC_SuperScript_860.ppd',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] ATTR file:',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Printer model: NEC SuperScript 860 Foomatic/ljet2p (recommended)',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Job title: Test Page',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] File(s) to be printed:',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] <STDIN>',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189]',
               "D [16/Jun/2010:12:07:40 -0700] [Job 189] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Printing system options:',
               "D [16/Jun/2010:12:07:40 -0700] [Job 189] Pondering option 'job-uuid=urn:uuid:dc9787eb-1f5d-3949-5c07-25799b9799b0'",
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Unknown option job-uuid=urn:uuid:dc9787eb-1f5d-3949-5c07-25799b9799b0.',
               "D [16/Jun/2010:12:07:40 -0700] [Job 189] Pondering option 'job-originating-host-name=localhost'",
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Unknown option job-originating-host-name=localhost.',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Options from the PPD file:',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189]',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] ================================================',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189]',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] File: <STDIN>',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189]',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] ================================================',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189]',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [16/Jun/2010:12:07:40 -0700] PID 3015 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Resolution: 300x300',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Page size: Letter',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Width: 612, height: 792, absolute margins: 18, 36, 594, 756',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Relative margins: 18, 36, 18, 36',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] PPD options: -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] PostScript to be injected:',
               'D [16/Jun/2010:12:07:40 -0700] [Job 189] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r300 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAcceptClient: 29 from localhost (Domain)',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 29 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 29 1.1 Get-Notifications 1',
               'D [16/Jun/2010:12:07:40 -0700] Get-Notifications /',
               'D [16/Jun/2010:12:07:40 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1',
               'D [16/Jun/2010:12:07:40 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAcceptClient: 30 from localhost (Domain)',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 30 1.1 Get-Notifications 1',
               'D [16/Jun/2010:12:07:40 -0700] Get-Notifications /',
               'D [16/Jun/2010:12:07:40 -0700] cupsdIsAuthorized: requesting-user-name="jr"',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 30 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 30 1.1 Get-Job-Attributes 1',
               'D [16/Jun/2010:12:07:40 -0700] Get-Job-Attributes ipp://localhost/jobs/189',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/189) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 26 1.1 Get-Notifications 1',
               'D [16/Jun/2010:12:07:40 -0700] Get-Notifications /',
               'D [16/Jun/2010:12:07:40 -0700] cupsdIsAuthorized: username="jr"',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1',
               'D [16/Jun/2010:12:07:40 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 Get-Printer-Attributes 1',
               'D [16/Jun/2010:12:07:40 -0700] Get-Printer-Attributes ipp://localhost/printers/NEC_SuperScript_860',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/NEC_SuperScript_860) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 29 WAITING Closing on EOF',
               'D [16/Jun/2010:12:07:40 -0700] cupsdCloseClient: 29',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Printers',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Classes',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Default',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Default client-error-not-found: No default printer',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Printers',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Classes',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Default',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Default client-error-not-found: No default printer',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Printers 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Printers',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Classes 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Classes',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdAuthorize: No authentication data provided.',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 11 1.1 CUPS-Get-Default 1',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Default',
               'D [16/Jun/2010:12:07:40 -0700] CUPS-Get-Default client-error-not-found: No default printer',
               'D [16/Jun/2010:12:07:40 -0700] Returning IPP client-error-not-found for CUPS-Get-Default (no URI) from localhost',
               'D [16/Jun/2010:12:07:40 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:40 -0700] cupsdReadClient: 30 WAITING Closing on EOF',
               'D [16/Jun/2010:12:07:40 -0700] cupsdCloseClient: 30',
               'D [16/Jun/2010:12:07:41 -0700] PID 3016 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] Filetype: PDF',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] Storing temporary files in /var/spool/cups/tmp',
               'D [16/Jun/2010:12:07:41 -0700] PID 3017 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] File contains 1 pages',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ljet2p -dMediaPosition=8 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r300x300 -sOutputFile=- -f   /var/spool/cups/tmp/foomatic-Lvj55h',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] Starting process "kid3" (generation 1)',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] Starting process "kid4" (generation 2)',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] Starting process "renderer" (generation 2)',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] JCL: \x1b%-12345X@PJL',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] <job data>',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189]',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] Read 8192 bytes of print data...',
               'D [16/Jun/2010:12:07:41 -0700] [Job 189] renderer exited with status 0',
               'D [16/Jun/2010:12:07:55 -0700] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:55 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:55 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [16/Jun/2010:12:07:55 -0700] cupsdReadClient: 26 1.1 Get-Job-Attributes 1',
               'D [16/Jun/2010:12:07:55 -0700] Get-Job-Attributes ipp://localhost/jobs/189',
               'D [16/Jun/2010:12:07:55 -0700] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/189) from localhost',
               'D [16/Jun/2010:12:07:55 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:55 -0700] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [16/Jun/2010:12:07:55 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:55 -0700] cupsdAuthorize: Authorized as jr using PeerCred',
               'D [16/Jun/2010:12:07:55 -0700] cupsdReadClient: 26 1.1 Cancel-Subscription 1',
               'D [16/Jun/2010:12:07:55 -0700] Cancel-Subscription /',
               'D [16/Jun/2010:12:07:55 -0700] cupsdIsAuthorized: username="jr"',
               'D [16/Jun/2010:12:07:55 -0700] cupsdMarkDirty(-----S)',
               'D [16/Jun/2010:12:07:55 -0700] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [16/Jun/2010:12:07:55 -0700] cupsdSetBusyState: Printing jobs and dirty files',
               'D [16/Jun/2010:12:07:55 -0700] cupsdAcceptClient: 29 from localhost (Domain)',
               'D [16/Jun/2010:12:07:55 -0700] cupsdReadClient: 29 GET /admin/log/error_log HTTP/1.1',
               'D [16/Jun/2010:12:07:55 -0700] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [16/Jun/2010:12:07:55 -0700] cupsdAuthorize: No authentication data provided.']}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

```

5. Not sure if I left off the hyphen last time.  I remember taking notice of it at the time.  Running **lprm -** , response: ```
lprm: Missing required attributes!

``` 

I swear it was there this time!  Ran **sudo lprm -** : ```
lprm: Missing required attributes!

```

Ran **sudo lprm -a all **with response: ```
lprm: Error - unknown option 'a'!

```

I was doing a little research and ran across command **lpq** .  When I entered that, I got a response saying there was no default location.  My printer was apparently not set as my default printer (although I think it was automatically after past installations - just not this most recent).  Then I tried lpq again and got a short list of print jobs.  So I ran lprm - and got not response.  Ran lpq again and then saw only print job 189 listed, which was strange since I was on job 192 or so at this point.  Attempted a few more test pages, ran lpq in between, new jobs will appear, but upon running lprm-, I still can't seem to get rid of job 189.  All the while, by the way, the physical print queue (that one accesses from the Ubuntu task bar) was not purging all the print jobs, even after I refreshed.  Thought this was odd.  I'm posting this reply and rebooting to see if I can get rid of job 189.  

J.R.

---

### Post by jrd43 on 2010-06-16
So, I did manage to purge Job 189.  I don't know what that was about.  And with the printer now set at default, let me retry some of your suggestions from post 83, as they relate, of course, to post 81.

1. (I didn't do anything further this time.)

2. Ran **sudo lpr test.txt** (as that was the original suggestion) - nothing.  Ran **sudo lp test.txt** - success!  ```
request id is NEC_SuperScript_860-200 (1 file(s))

```Sort of.  My printer did the 1/4" test page thing (as I've mentioned before, sometimes print commands yield the result of the previous command when the printer did nothing).  THEN, I ran **sudo lp test.txt** again ```
request id is NEC_SuperScript_860-200 (1 file(s))

``` and got precisely what you were looking for - a printed page with the text "This is a test".  Additionally, as with many test pages, there is a 1 to 3 character random blurb in the top left corner of the sheet.  In this instance it overlapped the "Th" in "This is a test" with a "2M".  I swear I'm not making this up.  Past and since cryptic messages have included "b2M", "10E", "M", "*r0F", and "*b2M".  Weird.  Anyway, that was a little bit of progress.  

5. (I didn't do anything further this go round.)

So things are a little weird today.  I'm on job 206, and the only 1/4" test page I've seen is the one mentioned just above.  I tried changing drivers a couple times, but under "Printer Properties, Printer State:" all it will say is "Idle - Unable to write print data: No such device" (this was something you asked me about).  Even with the "Foomat/lp2" driver, where as that used to yield a "Printer state:" of something like, "......Input/output error".

But on to your other suggestions and questions....

When I press press Change next to the Device URI (which says  parallel:/dev/usb/lp0) and wait for about 10 seconds, I do indeed get a Current Device which has the description "A printer connected to  the parallel port."  Oddly, it also lists "NEC SuperScript 860", "A printer connected to a USB port."  Shouldn't they be one and the same?  

I do have OO 3.2, but I couldn't find anything called "Printer Administration".  Clicking on printer settings, I got [see attachment].  

I installed the same printer with a different name, as you suggested, and in doing so discovered that the Location for the first printer installation probably should have also read "jr-laptop".  I changed that and attempted a few test pages and the Printer State is now reading "Processing", but nothing is happening.  I'm going to post this reply and reboot.

J.R.

---

### Post by thodges999 on 2010-06-17
Well I'll take this as progress, responding to #85 first.

The diagnosis you use brings together a number of reports for troubleshooting, the end of it being an extract of the cups error_log. I presume that when you ran it you printed a test page which was then job 189. The output is very interesting in that right near the end the last few lines refering to [Job 189] are

```
'D [16/Jun/2010:12:07:41 -0700] [Job 189] Read 8192 bytes of print data...',
'D [16/Jun/2010:12:07:41 -0700] [Job 189] renderer exited with status 0',
```

where previously (#82) it was;

```
D [11/Jun/2010:22:40:16 -0700] [Job 184] Read 8192 bytes of print data...
E [11/Jun/2010:22:40:16 -0700] [Job 184] Unable to write print data: Input/output error
D [11/Jun/2010:22:40:16 -0700] [Job 184] Set job-printer-state-message to "Unable to write print data: Input/output error", current level=ERROR
```

and before that (#74) it was 

```
'D [05/Jun/2010:13:09:46 -0700] [Job 149] Read 8192 bytes of print data...',
'E [05/Jun/2010:13:09:46 -0700] [Job 149] Unable to write print data: No such device',
'D [05/Jun/2010:13:09:46 -0700] [Job 149] Set job-printer-state-message to "Unable to write print data: No such device", current level=ERROR',
```

In addition there was no error with the foomatic filter. However I guess the test page wasn't output so only a small step for man!

I'm confused regarding the use of lprm. If you try lprm on its own it should give you the status of your default printer, please try that and see if it sees your NEC printer. Also try **lpstat -p -d** which should show you all available printers and which is the default.

I've just discovered if you type **lpc** you will get to a new command prompt **lpc>**, then type **status** will give you some more info on your print queues. Type quit when you are finished to return to the normal prompt.

Now post #86.

I'll take the printing of test.txt as good news (apart from sone cryptic characters) although somehow the printer has managed to go back to the 'Input/output error' and 'No such device' messages above!!!

Try opening **[http://localhost:631/printers](http://localhost:631/printers)** in your browser and seeing what printers are there (This should give the same as the lpstat commannd above). Assuming its just the NEC SuperScript 860 try some of the options like show completed jobs, and select cancel all jobs from the drop down list headed 

The Device URI is really weird and we may be getting closer. I attach a screenshot of my setup and I assume you have the NEC SuperScript 860 where I have the Brother MFC and if you click on it the message is "A printer connected to a USB port."? However my Brother is actually a separate USB printer and I think you are quite right that you shouldn't get two entries for the same printer. (What is even more weird is that after taking that screenshot I'm unable to replicate it, when I try now I only see the one printer called Current Device!)

If you try it again and still see the two printers try selecting the "NEC SuperScript 860", "A printer connected to a USB port." After a short while you will be returned to the Printer Properties screen and I guess the URI has changed to usb://NEC_SuperScript_860. Reboot and try printing a test page again.

If this doesn't work we'll need to reverse the process and change the URI back to parallel:/dev/usb/lp0 and try to remove the usb version (I'll have a think on this)

---

### Post by mdcsvt on 2010-06-17
hello, I too have a printer, it stopped working I guess after some update (on lucid 64-bit). I followed your instructions, after rebooting with printer off I had


$  tail -n 20 /var/log/syslog
Jun 17 13:08:49 modica pulseaudio[1648]: pid.c: Daemon already running.
Jun 17 13:08:51 modica NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 17 13:08:51 modica NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 17 13:08:51 modica anacron[1684]: Anacron 2.3 started on 2010-06-17
Jun 17 13:08:51 modica anacron[1684]: Normal exit (0 jobs run)
Jun 17 13:08:51 modica kernel: [   43.118442] CPU0 attaching NULL sched-domain.
Jun 17 13:08:51 modica kernel: [   43.118447] CPU1 attaching NULL sched-domain.
Jun 17 13:08:51 modica kernel: [   43.170120] CPU0 attaching sched-domain:
Jun 17 13:08:51 modica kernel: [   43.170123]  domain 0: span 0-1 level MC
Jun 17 13:08:51 modica kernel: [   43.170126]   groups: 0 1
Jun 17 13:08:51 modica kernel: [   43.170131] CPU1 attaching sched-domain:
Jun 17 13:08:51 modica kernel: [   43.170133]  domain 0: span 0-1 level MC
Jun 17 13:08:51 modica kernel: [   43.170136]   groups: 1 0
Jun 17 13:08:57 modica pulseaudio[1612]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Jun 17 13:08:57 modica pulseaudio[1612]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/modica:@/tmp/.ICE-unix/1387,unix/modica:/tmp/.ICE-unix/1387"): initialization failed.
Jun 17 13:08:59 modica acpid: client connected from 1794[107:116]
Jun 17 13:08:59 modica acpid: 1 client rule loaded
Jun 17 13:09:01 modica CRON[1806]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 17 13:09:03 modica NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 17 13:09:51 modica AptDaemon: INFO: Initializing daemon

The I turned on the printer, system configured automatically and said "ready to print", but I tried to print a line from gedit and it won't. It says "printer non connected?".

After that I get

$ tail -f /var/log/messages
Jun 17 13:08:27 modica kernel: [   19.044031] type=1505 audit(1276772907.684:12):  operation="profile_load" pid=989 name="/usr/bin/evince-previewer"
Jun 17 13:08:27 modica kernel: [   19.047639] type=1505 audit(1276772907.684:13):  operation="profile_load" pid=989 name="/usr/bin/evince-thumbnailer"
Jun 17 13:08:29 modica kernel: [   21.113194] type=1505 audit(1276772909.754:14):  operation="profile_load" pid=995 name="/usr/lib/cups/backend/cups-pdf"
Jun 17 13:08:29 modica kernel: [   21.332841] type=1505 audit(1276772909.974:15):  operation="profile_load" pid=995 name="/usr/sbin/cupsd"
Jun 17 13:12:30 modica kernel: [  261.770022] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jun 17 13:12:30 modica kernel: [  261.966266] usb 4-1: configuration #1 chosen from 1 choice
Jun 17 13:12:30 modica kernel: [  262.033266] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1D17
Jun 17 13:12:30 modica kernel: [  262.033347] usbcore: registered new interface driver usblp
Jun 17 13:12:31 modica kernel: [  263.171727] usb 4-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Jun 17 13:12:50 modica kernel: [  282.051031] usb 4-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

Can you help? 
Many many thanks
salvatore

---

### Post by thodges999 on 2010-06-17
> **mdcsvt said:**
> hello, I too have a printer, it stopped working I guess after some update (on lucid 64-bit). I followed your instructions, after rebooting with printer off I had


$  tail -n 20 /var/log/syslog
Jun 17 13:08:49 modica pulseaudio[1648]: pid.c: Daemon already running.
Jun 17 13:08:51 modica NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 17 13:08:51 modica NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 17 13:08:51 modica anacron[1684]: Anacron 2.3 started on 2010-06-17
Jun 17 13:08:51 modica anacron[1684]: Normal exit (0 jobs run)
Jun 17 13:08:51 modica kernel: [   43.118442] CPU0 attaching NULL sched-domain.
Jun 17 13:08:51 modica kernel: [   43.118447] CPU1 attaching NULL sched-domain.
Jun 17 13:08:51 modica kernel: [   43.170120] CPU0 attaching sched-domain:
Jun 17 13:08:51 modica kernel: [   43.170123]  domain 0: span 0-1 level MC
Jun 17 13:08:51 modica kernel: [   43.170126]   groups: 0 1
Jun 17 13:08:51 modica kernel: [   43.170131] CPU1 attaching sched-domain:
Jun 17 13:08:51 modica kernel: [   43.170133]  domain 0: span 0-1 level MC
Jun 17 13:08:51 modica kernel: [   43.170136]   groups: 1 0
Jun 17 13:08:57 modica pulseaudio[1612]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Jun 17 13:08:57 modica pulseaudio[1612]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/modica:@/tmp/.ICE-unix/1387,unix/modica:/tmp/.ICE-unix/1387"): initialization failed.
Jun 17 13:08:59 modica acpid: client connected from 1794[107:116]
Jun 17 13:08:59 modica acpid: 1 client rule loaded
Jun 17 13:09:01 modica CRON[1806]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jun 17 13:09:03 modica NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun 17 13:09:51 modica AptDaemon: INFO: Initializing daemon

The I turned on the printer, system configured automatically and said "ready to print", but I tried to print a line from gedit and it won't. It says "printer non connected?".

After that I get

$ tail -f /var/log/messages
Jun 17 13:08:27 modica kernel: [   19.044031] type=1505 audit(1276772907.684:12):  operation="profile_load" pid=989 name="/usr/bin/evince-previewer"
Jun 17 13:08:27 modica kernel: [   19.047639] type=1505 audit(1276772907.684:13):  operation="profile_load" pid=989 name="/usr/bin/evince-thumbnailer"
Jun 17 13:08:29 modica kernel: [   21.113194] type=1505 audit(1276772909.754:14):  operation="profile_load" pid=995 name="/usr/lib/cups/backend/cups-pdf"
Jun 17 13:08:29 modica kernel: [   21.332841] type=1505 audit(1276772909.974:15):  operation="profile_load" pid=995 name="/usr/sbin/cupsd"
Jun 17 13:12:30 modica kernel: [  261.770022] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jun 17 13:12:30 modica kernel: [  261.966266] usb 4-1: configuration #1 chosen from 1 choice
Jun 17 13:12:30 modica kernel: [  262.033266] usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1D17
Jun 17 13:12:30 modica kernel: [  262.033347] usbcore: registered new interface driver usblp
Jun 17 13:12:31 modica kernel: [  263.171727] usb 4-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
Jun 17 13:12:50 modica kernel: [  282.051031] usb 4-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

Can you help? 
Many many thanks
salvatore

Hi
First some more info please, what printer are you using and is it connected with a usb-parallel cable adapter? Now turn the printer on and then unplug and replug in the usb cable to your computer.

Then run the following commands one at a time;
```
lsusb
tail -n 20 /var/log/syslog
```

I found this [[COLOR="Red"]**troubleshooting**[/COLOR]]("https://wiki.ubuntu.com/DebuggingPrintingProblems#Troubleshooting%20Wizard") guide a useful source. Try the Troubleshooting Wizard near the bottom and post the results here. Remember to put long logs inside quote marks (use the # on the post toolbar)

---

### Post by mdcsvt on 2010-06-18
Thanks, 
I solved my problem. What I grasped from the information that it was a "CUPS back-end problem" led me to restart directly from cups, via localhost:631. 
And it worked.
Bye, 
salvatore modica

---

### Post by thodges999 on 2010-07-05
Hi jrd43
Have you made any more progress with your printer yet?

Sadly both our teams are out of the World Cup but yours played much better than ours so congratulations. Hope you had a great 4th July.

---

### Post by moth17 on 2010-07-24
I have made no progress on this issue. I had to put it down for a while while I dealt with some professional matters. It might take a while to figure out where I left it and where to jump back in...

---

### Post by sefs on 2010-12-06
Hey there,

There is no /dev/usb/lp0 on my system but there is a /dev/usb/hiddev0

Should I substitute this instead in the url thing?

Thanks.

---

### Post by moth17 on 2010-12-31
I'm wondering if anyone has made any progress with this? I'm no further from when I began.

---

### Post by jamillikan on 2011-01-04
The problem is the cable, not Ubuntu.  I tried with THREE different types of USB to Parallel cables with zilch for luck.  Only when I used a Belkin USB to parallel adapter is everything working perfectly.

What doesn't work is an Ultra USB 2.0 to Parallel Adapter which comes with a CD to install drivers.  The other two also had a small CD.  (I threw both of them in the trash I was so mad.)  

I'm suspecting they've done something to those USB to Parallel cables....but it matters not.  The Belkin version works flawlessly and Ubuntu found the printer automatically on 10.04 once I had a decent cable.

Hope this helps others struggling with this issue.  It was driving me nuts until today.

Joe

---

### Post by moth17 on 2011-01-04
> **jamillikan said:**
> The problem is the cable, not Ubuntu.  I tried with THREE different types of USB to Parallel cables with zilch for luck.  Only when I used a Belkin USB to parallel adapter is everything working perfectly.

What doesn't work is an Ultra USB 2.0 to Parallel Adapter which comes with a CD to install drivers.  The other two also had a small CD.  (I threw both of them in the trash I was so mad.)  

I'm suspecting they've done something to those USB to Parallel cables....but it matters not.  The Belkin version works flawlessly and Ubuntu found the printer automatically on 10.04 once I had a decent cable.

Hope this helps others struggling with this issue.  It was driving me nuts until today.

Joe

Thanks, Joe. It never occurred to me to change out the cable because it works with Windows Vista (dual boot). Where did you source that cable?

Sean

---

### Post by moth17 on 2011-01-04
> **moth17 said:**
> Thanks, Joe. It never occurred to me to change out the cable because it works with Windows Vista (dual boot). Where did you source that cable?

Sean

Yikes- I just looked one up online and it was $40. Maybe I should just think about getting a new printer...

[http://www.belkin.com/IWCatProductPage.process?Product_Id=20651](http://www.belkin.com/IWCatProductPage.process?Product_Id=20651)

S

---

### Post by moth17 on 2011-01-04
$28.50 on Amazon:

[http://www.amazon.com/Belkin-F5U002V1-Parallel-Printer-Adapter/dp/B000EANT40](http://www.amazon.com/Belkin-F5U002V1-Parallel-Printer-Adapter/dp/B000EANT40)

---

### Post by jamillikan on 2011-01-04
Amazon is the ticket.  Hope this helps others.  I was really furious about this issue until I discovered the problem...and spending God know how much for three USB to Serial cables from $12 to $19 that were worthless until the Belkin one.  It's worth its costs in headaches avoided IMO.  

Yes, I know the USB to Parallel cheap cables work in Windows but not Ubuntu.  I guess that's why they came with a CD with Windows drivers to make them work.

Anyway, the point I wanted to stress is purchasing the Belkin USB to Parallel Adapter is the solution to this "issue."  To avoid unnecessary frustration, purchase the Belkin product.

Joe

---

### Post by jrd43 on 2011-01-05
Yes, I resolved the issue.... by getting a new printer.  My apologies, thodges999, for not getting back to you sooner.  You were being very diligent in your attempts to help solve my problem and I suddenly flaked out.  I had gone out of town for a week and, when I got back, composed yet another long, detailed post for you when my monitor suddenly turned itself off (laptop), and I had to shut down, losing my work.  That was the straw that broke the camel's back, and I vowed that I would post here again only once I had some information you could actually use or I had resolved the issue.  

I partitioned my hard drive and installed XP, as my printer had always worked with XP on my previous two computers.  As much as it frustrated me, I resided to set 20 gigs of my hard drive aside just for print jobs.  But, alas, *it just wouldn't jive with this machine*.  The fact that not even XP would let me print was a big f**kitall, and I could only assume my Toshiba Satellite was at fault.  This all happened within the last few weeks, and the other day I scored a nice, six-year-old Samsung laser printer off craigslist and it installed instantly.  Why the hell did I beat my head against the wall for 6 months for a problem I solved with a $20 bill?... I thought I was up for the challenge.  I lost.

My NEC printer was about 14 years old and, with thodges help, I probably spent a good 40+ hours trying to get it to work.  That's a whole work week, and I wasn't getting paid!  So my only advice on the matter is that you know when to quit and go another route.  Good luck.

---

### Post by dudy'O on 2011-01-18
Tonight I spent several hours trying to get an HP LaserJet 6P to print correctly. It came down to a driver and connection settings issue.

Many thanks everyone and especially to thodges999 for all of his/her hard work and dedication to helping others.

Type of USB - Parallel Cable:
Monoprice - USB-CN36


From Cups Manager:
Description:	HP LaserJet 6p
Location:	
Driver:	HP LaserJet 6P - CUPS+Gutenprint v5.2.6 (grayscale, 2-sided printing)
Connection:	parallel:/dev/usb/lp0

```
 
~ $ lsusb 
Bus 003 Device 006: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
```

Thanks again!!:D

---

### Post by user_of_ubuntu on 2011-01-18
Now I have the problem.  When I initially hooked up the USB - paralell cable it worked great.  I went to bed and the next morning it had stopped.  Anyone have any ideas.  My head is reeling from reading all these posts.

---

### Post by dflora on 2011-03-06
I had a similar problem. I eventually got it working by using a generic printer,

Generic PCL Laser Printer

with device uri,

parallel:/dev/usb/lp0


However as my printer was working yesterday before I "recovered" my operating system, UBUNTU 10.10. So it is possible that it won't work tomorrow.

Peter

---

### Post by Fatty_Matty on 2011-04-16
Just started running Ubunutu 10.10 today for the first time - installed an old HP Laserjet 1100 with a Parallel to USB converter and it works a treat now.

Thank you!!!!

---

### Post by oojanen on 2011-11-06
This is what did the trick for me:

If you don't have the file /dev/usblp already, do 

1. Use "parallel:/dev/usb/lp0" as the printer URI

then 

2. do "sudo modprobe usblp" in the terminal. 

Voila.

I have Ubuntu 11.10 + HP Laserjet 6P conneted through usb-parallel cable "Prolific technology, Inc. PL2305 Parallel port".

PS. To load automatically at boot up, add a line with "usblp" into the file /etc/modules

---

### Post by gsa390 on 2011-11-14
> **dflora said:**
> I had a similar problem. I eventually got it working by using a generic printer,

Generic PCL Laser Printer

with device uri,

parallel:/dev/usb/lp0


However as my printer was working yesterday before I "recovered" my operating system, UBUNTU 10.10. So it is possible that it won't work tomorrow.

Peter
thank you!!!!!!

---

### Post by Handssolow on 2012-01-21
Thanks to those posting in this thread.
I bought a parallel-usb cable because my new motherboard doesn't have a parallel port for my printer. System Tools>System Settings>Printers doesn't detect my printer.
dmesg gave this-
lp: driver loaded but no devices found
lsusb gave this-
Bus 003 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port

I added Oneiric proposed packages but it didn't seem to made any difference.
In Firefox I entered [http://localhost:631/](http://localhost:631/) to configure CUPS then Administration>Add Printer
then I used "parallel:/dev/usb/lp0" as the device URL

It's working so I don't need to but a PC1 printer socket card after all.

---

