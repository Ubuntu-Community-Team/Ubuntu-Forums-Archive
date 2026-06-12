---
title: "Canon SELPHY Series to be suported in gutenprint"
date: 2012-10-28
forum: Hardware
---

### Post by aikishugyo on 2012-10-28
Hi,

My name is Gernot Hassenpflug, and I'm working as volunteer maintainer of the Canon backend of the gutenprint project.

The SELPHY series is now going to be officially supported in the next release of gutenprint (5.2.9 is the current release), because finally there is good news: the required intelligent spooler has been rewritten (by Solomon Peachy, to whom all this credit goes) to be compliant with CUPS. This means that the dye-sublimation backend of the gutenprint package will be able to support the entire SELPHY series---up to now only some printers would print without the intelligent spooler, so gutenprint could not officially support the series.

However, we desperately require information on the USB PID (product IDs) of the SELPHY series, which are not easy to find from the driver files (if they are even visible). It would be a shame to not be able to support some models simply because their USB PIDs are not yet known.

We would very much like to compile a list of the USB product IDs (usually it is available with the "lsusb" command if the printer is attached to the PC). I'm happy to read in this thread, but people can submit them to the gutenprint mailing list: [email]gimp-print-devel@lists.sourceforge.net[/email]

Else, directly to me at [email]aikishugyo@gmail.com[/email]

Note: some USB IDs are already known on the USB ID database ([http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)) and a couple of others are known to us at gutenprint from personal use. The completed list will be submitted back to the USB ID database.

Here is the---sadly short---list of known PIDs (the VID for Canon is 04a9):
[LIST=1][*]ES1 3141
[*]ES2 3185
[*]ES30 31b0
[*]ES40 31ee
[*]CP-10 304a
[*]CP-100 3063
[*]CP-220 30bd
[*]CP-300 307d
[*]CP-330 30be
[*]CP400 30f6
[*]CP600 310b
[*]CP800 3214[/LIST]
Best regards and thanks in advance for any USB PID information,
Gernot Hassenpflug

---

### Post by aikishugyo on 2012-11-21
**Update.**

_Status as of Nov 22, 2012:_
20 printers verified
10 printers unverified should work
4 printers unknown (missing PIDs and/or unknown readback codes since no testers)
[U]
The development code by Solomon Peachy is available at:[/U]
git://git.shaftnet.org/selphy_print

Integration into gutenprint is underway, so testers are welcome to try printing from gutenprint also.

**Reference (from README.TXT and code):**

1) _Verified supported printers:_
  
     ES1, ES2, ES30, ES40, CP-200, CP-300, CP-330, CP400, CP500, CP510,
     CP710, CP720, CP730, CP740, CP750, CP760, CP770, CP780, CP800, CP900

   Unverified/untested, but should work:

     ES20, ES3, CP-10, CP-100, CP-220, CP520, CP530, CP600, CP790, CP810

   NOT currently supported by libusb backend:  (USB PIDs unknown)
        
     ES3, CP520, CP530, CP790

2) _USB PIDs:_

#define USB_VID_CANON       0x04a9
#define USB_PID_CANON_ES1   0x3141
#define USB_PID_CANON_ES2   0x3185
#define USB_PID_CANON_ES20  0x3186
#define USB_PID_CANON_ES3   3   // XXX 31af? 31b1??
#define USB_PID_CANON_ES30  0x31B0
#define USB_PID_CANON_ES40  0x31EE
#define USB_PID_CANON_CP10  0x304A
#define USB_PID_CANON_CP100 0x3063
#define USB_PID_CANON_CP200 0x307C
#define USB_PID_CANON_CP220 0x30BD
#define USB_PID_CANON_CP300 0x307D
#define USB_PID_CANON_CP330 0x30BE
#define USB_PID_CANON_CP400 0x30F6
#define USB_PID_CANON_CP500 0x30F5
#define USB_PID_CANON_CP510 0x3128
#define USB_PID_CANON_CP520 520 // XXX 316f? 3172? (related to cp740/cp750)
#define USB_PID_CANON_CP530 530 // XXX
#define USB_PID_CANON_CP600 0x310B
#define USB_PID_CANON_CP710 0x3127
#define USB_PID_CANON_CP720 0x3143
#define USB_PID_CANON_CP730 0x3142
#define USB_PID_CANON_CP740 0x3171
#define USB_PID_CANON_CP750 0x3170
#define USB_PID_CANON_CP760 0x31AB
#define USB_PID_CANON_CP770 0x31AA
#define USB_PID_CANON_CP780 0x31DD
#define USB_PID_CANON_CP790 790 // XXX
#define USB_PID_CANON_CP800 0x3214
#define USB_PID_CANON_CP810 0x3256
#define USB_PID_CANON_CP900 0x3255

---

### Post by pdc on 2012-11-22
well done; great work; thanks for this; a huge contribution

---

### Post by aikishugyo on 2013-02-12
Happily, with lots of support from the Mac OSX user forums and postings on the gimp-print mailing list, support for almost all SELPHY models and their CUPS integration has been achieved in the CVS version of gutenprint (not the current 5.2.9 package).

The two devices for which USB PIDs are still missing, are as follows:
[list=1]
[*]CP520
[*]CP790
[/list]
If anyone has access to one of those devices and can post the USB PID, that would be most appreciated.

Many thanks,
Gernot Hassenpflug

---

### Post by broadstairs on 2013-06-11
Just wondering if anything has happened yet to update the packages for this new printer support? I'm not good at compiling stuff! I now have a CP900 printer and I am fed up with dual booting or using Virtualbox to print everytime.

Stuart

---

### Post by aikishugyo on 2013-06-11
Hi Stuart,
If you want to install, you'll have to compile from CVS.
Unfortunately, for some reason or other, the only contributions we have, and pretty many of them, are owing to the MacOSX community, which has really given sterling information on USB IDs and lately also the IEEE1284 device IDs which we are attempting to add to the gutenprint printer definitions to enable distributions to do automated printer driver detection.
So the situation regarding the 2 printer models above has not changed, but the spooler has been improved, based on some feedback to the gutenprint mailing list lately. In fact, this improvement related to the CP900, so you should have excellent support were you to compile the source code at this time.
There are no plans as yet to release a 5.2.10 version.
In my view, a lot of problems are a mixture of bugs in gutenprint and bugs in the CUPS USB backend, and I am spending many debugging hours working with a few users of Canon printers to find out if there are any bugs in the current code. I also need to finish support for different CD trays. After that, I will be ready to go forward with a release---whether the other backend maintainers will have similar schedules remains to be seen.

---

### Post by aikishugyo on 2013-06-11
Let me call out again for help: any users of CP and ES series printers, if you can post the USB PID ("lsusb -v <device>" command can be used to obtain it) and IEEE1284 device ID ("lpinfo -l -v" should be able to give it).

---

### Post by enthusi on 2013-06-21
HI,
Im very happy that I can use the Selphy CP900 via Gutenprint in Debian 7.0 using the CP 520 driver.
However it feels rather unsatisfactory and sometimes I have to send a print job twice for it to start.

What can I do to help and what can I expect when CP900 is suppored natively?
Progress in print quality?
I was just about to get my printer calibrated using the CP520 driver. Should I rather wait now?

On
[http://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/](http://sourceforge.net/projects/gimp-print/files/gutenprint-5.2/) 
the latest version is 5.2.9 and from 2012.

for the CVS I seem to need a password. Am I missing something?
Thanks for any help!

Cheers,
Martin

Here is the info for my CP900:
[ 3572.732024] usb 1-4: new high-speed USB device number 5 using ehci_hcd
[ 3572.870616] usb 1-4: New USB device found, idVendor=04a9, idProduct=3255
[ 3572.870621] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3572.870625] usb 1-4: Product: Canon SELPHY CP900
[ 3572.870628] usb 1-4: Manufacturer: Canon Inc.
[ 3572.870631] usb 1-4: SerialNumber: CA12112500004095
[ 3572.874687] usblp1: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04A9 pid 0x3255

---

### Post by aikishugyo on 2013-06-21
Hi, can you get the IEEE1284 information using lpinfo -v -l ?
For CVS, you need to read the gutenprint download page on how to retrieve the code
[http://gimp-print.sourceforge.net/p_Download.php](http://gimp-print.sourceforge.net/p_Download.php)

---

### Post by enthusi on 2013-06-21
Yay, 
I was able to retrieve it as tar ball and turns out it was 5.2.10 which included cp900.
Had to make some changes to the Makefile (mostly doc-related) but it compiled and showed up in GIMP 2.8 -> Gutenprint 
hooray.
Cant see any difference in the prints though, but still very nice.

lsub -v

Bus 001 Device 007: ID 04a9:3255 Canon, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04a9 Canon, Inc.
  idProduct          0x3255 
  bcdDevice            0.01
  iManufacturer           1 Canon Inc.
  iProduct                2 Canon SELPHY CP900
  iSerial                 3 CA12112500004095
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
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

---

### Post by aikishugyo on 2013-06-21
hmm, lsusb is not what gives the IEEE1284 information.
Here is the script that should return the values, I do not know how to do it with CUPS commands.
/usr/share/system-config-printer/check-device-ids.py

---

### Post by enthusi on 2013-06-22
Hm, ich have no such script. Neither lpinfo.
cand find it in the debian repository either Im afraid.

---

### Post by aikishugyo on 2013-06-22
Really? when I search for this I get several hits with apt-cache. I think it is the python one.
[COLOR="#AFFAAFF"]system-config-printer-kde - printer configuration utility
python-cupshelpers - Python utility modules around the CUPS printing system
system-config-printer - graphical interface to configure the printing system
system-config-printer-udev - Utilities to detect and configure printers automatically[/COLOR]

---

### Post by enthusi on 2013-06-22
Yeah, those exist. Didnt know they'd work as well.
system-config-printer doesnt show the selphy.
But it installed that check-device-ids.py and it yields the following
Skipping cnijusb:/dev/usb/lp1, insufficient data
Skipping parallel:/dev/lp0, insufficient data
Installing relevant drivers using session service
Ignoring exception: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.PackageKit was not provided by any .service files
Fetching driver list
&#9500;&#9472;&#9472; Canon CP900 (usb): MFG:Canon;MDL:CP900;CMD:Raster3;
&#9474;   (No drivers)
&#9492;&#9472;&#9472; Canon CP900 (tpu): MFG:Canon;MDL:CP900 TurboPrint;
    (No drivers)



No IEEE Im afraid?

---

### Post by aikishugyo on 2013-06-23
Hi, that looks fine. This is the abbreviated IEEE1284 device ID output by the script:
> Canon CP900 (usb): MFG:Canon;MDL:CP900;CMD:Raster3;
If you modify the script to output all the parameters, not just MFG, MDL, CMD you should get also CLS, DES, and VER.
Maybe:
CLS will be "PRINTER"
DES will be "Canon CP900"
VER will be "1.00"
If you could confirm that would be wonderful.

---

### Post by DryChili on 2014-05-17
Hey,
 I know this is an old thread. I still have a Selphy CP520. Its an amazing printer. Here is what lsusb -v says about it. Maybe its still of use:

```

Bus 002 Device 020: ID 04a9:3172 Canon, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04a9 Canon, Inc.
  idProduct          0x3172 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
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
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
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

```

---

### Post by aikishugyo on 2014-05-17
DryChili,
You are a saviour! Excellent information. Many thanks, that was a long-time missing USB ID for us at the gutenprint project.
Could you send also the output of
/usr/share/system-config-printer/check-device-ids.py
please.
And if possible, could you modify that script temporarily to output everything, so that we can get CLS, DES and VER information also? (if you prefer, you can add just those 3 items to the code output list). It does not matter if the output is messy, just let the program output everything.
Here is the line in the code (appears in two places, please edit only the first one) where the information is collated. As root, after this line

>   id_fields = cupshelpers.parseDeviceID (device_id)

add:

>   print "%s" % id_fields

Connect the CP520 to the PC with a USB cable, power it on, and run the script as root (or sudo):
You'll get an output (here for my MP450) like this, please post it:

> Examining connected devices
{u'DES': u'Canon MP450', u'VER': u'1.08', u'STA': u'10', u'MDL': u'MP450', u'MFG': u'Canon', 'J': '', u'CMD': [u'BJL', u'BJRaster3', u'BSCCe'], 'P': '', 'S': '', u'HRI': u'JP', 'SN': '', u'SOJ': u'TXT01', u'CLS': u'PRINTER'}

---

### Post by M3ta7h3ad on 2014-09-11
So latest 14.04 ubuntu with Gutenprint v5.2.10 gives me a selphy C910 that hangs after first print.

lsusb output
```

Bus 001 Device 014: ID 04a9:327a Canon, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04a9 Canon, Inc.
  idProduct          0x327a 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
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
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0

```

check-device-ids.py output
```

If you have not already done so, you may get more results
by temporarily disabling your firewall (or by allowing
incoming UDP packets on port 161).

Examining connected devices
Installing relevant drivers using session service
Fetching driver list
&#9492;&#9472;&#9472; Canon CP910 (usb): MFG:Canon;MDL:CP910;CMD:Raster3;
    (No drivers)

```

Do you need anything else for the project and this printer?

Would be awesome to get it up and running, currently using the Selphy CP900 Gutenprint driver but as I said, it hangs after 1 print with the photo paper hanging out its backside :)

---

### Post by aikishugyo on 2014-09-11
Hi, thank you for your support.
About the CP910, this is brand-new really, so any testing is appreciated. Support is basically there in 5.2.10 up to the CP900, but continuing in the development code as problems became apparent with later models (a new CUPS backend was developed specifically to support these devices).
There was a thread on the gimp-print-devel mailing list about the CP910 and its differing data format some time back, I doubt that the code is completed at this stage.
Please contact that mailing list for support and testing, this is not an Ubuntu-specific issue and there is no point in discussing development on this forum in detail.
To subscribe:
[https://lists.sourceforge.net/lists/listinfo/gimp-print-devel](https://lists.sourceforge.net/lists/listinfo/gimp-print-devel)

---

### Post by Chris_Nesbitt-Smit on 2015-05-01
Hey, see my post here [https://www.raspberrypi.org/forums/viewtopic.php?p=747363#p747363](https://www.raspberrypi.org/forums/viewtopic.php?p=747363#p747363) CP910 working in ubuntu on a pi, also works on desktops - avoids the 1 print issue and other usb madness
Should see us through until theres good gutenprint drivers

---

