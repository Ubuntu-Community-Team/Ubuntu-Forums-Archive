---
title: "Genius Mouspen 8x6 under Jaunty Jackalope"
date: 2009-05-06
forum: Hardware
---

### Post by xSxTxOxRxMx on 2009-05-06
Hi, I'm new to Ubuntu and the version I'm using is 9.04 Jaunty Jackalope.
I'd love to get my tablet, a Genius Mousepen 8x6 working on it!

I have already tried using wizardpen:
[http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)

I patched the code for the driver myself referring to this:

[http://code.google.com/p/linuxgenius/issues/detail?id=1](http://code.google.com/p/linuxgenius/issues/detail?id=1)

I got the driver to compile! YAY! I thought. But wait, it's still not working..

As I got to the calibration step, I realized that my tablet was not showing up at all when I executed the command **lshal | less**

And from there, I don't know how to go about setting up my tablet any further and getting it working.

My tablet's name showed up as UC-LOGIC Tablet WP8060U when I executed **[FONT=monospace]grep -i name /proc/bus/input/devices[/FONT]**

It's important to me to get this figured out as soon as possible, and I'd greatly appreciate any help. Thanks for listening.

---

### Post by Favux on 2009-05-07
Hi xSxTxOxRxMx,

Since in Jaunty you are suppose to configure through a .fdi file rather than xorg.conf maybe the .fdi file isn't picking up your tablet.  I think your Genius tablet is basically a Waltop tablet and the entry is in the 10-wacom.fdi in /usr/share/hal/fdi/.  Take a look at that Waltop subsection.  Do you see an identifier like "WP8060U" in the first line or two of it?

Also do you see anything with "xsetwacom list"?  How about "xinput --list"?

---

### Post by xSxTxOxRxMx on 2009-05-09
I didn't find that file. I checked that directory and then did a search, to no avail.

If there is a seperate way to install wizardpen for Jaunty, perhaps I went about it the wrong way using that tutorial. Although, it did state that it currently works with Jaunty. 

I'm very new to Linux, so if I get something wrong, please have patience with me. :]

---

### Post by Favux on 2009-05-09
Hi xSxTxOxRxMx,

I'm sorry, I wasn't clear.  It should be in /usr/share/hal/fdi/policy/20thirdparty/.  In the folder 20thirdparty should be 10-wacom.fdi.  Either way check Synaptics Package Manager and see if you have the 0.8.2-2 linuxwacom packages installed.  xserver-xorg-input-wacom and wacom-tools.  If not install them.

I didn't see the reference to Jaunty you mentioned.  Your tablet is basically the same as a Genius WizardPen, correct?

---

### Post by xSxTxOxRxMx on 2009-05-09
I found the file now, but it makes no reference to my device's name (UC-LOGIC Tablet WP8060U) or any part of its name. It does list what seems to be the device names for several tablets, but not mine. Also, my tablet is not a Wacom tablet, the brand isn't the same, although WizardPen is supposed to work with my model.

It seems it would be considered a Genius Wizardpen device, since its brand is Genius.

---

### Post by Favux on 2009-05-09
Hi xSxTxOxRxMx,

OK, the thing is that Waltop is the underlying manufacturer for a bunch of tablets.  One of them being the Genius WizardPen.  And Waltop manufactured tablets will work with the linuxwacom driver.  That's why the Waltop entry is in the 10-wacom.fdi.  So the question is is your tablet manufactured by Waltop, and rebranded by Genius like the WizardPen.

Given that it is saying it is a UC-LOGIC Tablet WP8060U that doesn't sound likely.  It sounds like Genius has rebranded a UC-LOGIC tablet.  But to confirm that you can look in:
```
lshal>lshal.txt
```
There should be one or more sections dealing with the tablet.  Be patient, it will be a huge output.  I've done it several times already so it's doable.  We want those section(s).  If you're lucky in that section it will mention Waltop somewhere.

Otherwise we have to figure out if UC-LOGIC tablets have a linux driver.  Or if we're lucky the linuxwacom drivers might also work.  Or there is kernel support (driver built into the kernel) that we could hook into.

---

### Post by Favux on 2009-05-09
Hi xSxTxOxRxMx,

I did a google search with "UC-LOGIC Tablet WP8060U" and found some stuff.

There's .fdi named 99-geniuspen.fdi instead of 10-wacom.fdi:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
	    <merge key="input.x11_driver" type="string">wizardpen</merge>
	    <merge key="input.x11_options.TopX" type="string">695</merge>
	    <merge key="input.x11_options.TopY" type="string">2320</merge>
	    <merge key="input.x11_options.BottomX" type="string">32747</merge>
	    <merge key="input.x11_options.BottomY" type="string">32762</merge>
    </match>
  </device>
</deviceinfo>
```
I changed the header:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
```
to
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
```
So if you can find a .fdi like this then Jaunty is supporting your tablet.  But since you aren't getting any activity...  Along with the .fdi is other information at:  [http://aur.archlinux.org/packages.php?ID=18158](http://aur.archlinux.org/packages.php?ID=18158)

And the updated driver he refers to is at:  [http://digitalbluewave.blogspot.com/2008/11/updated-wizardpen-driver-070-alpha1-p.html](http://digitalbluewave.blogspot.com/2008/11/updated-wizardpen-driver-070-alpha1-p.html)  along with a link to installation instructions.   It's not clear to me if it works for the Xserver 1.6 in Jaunty or if you have to make the changes in the src code he talks about.  If you're lucky Jaunty already has this.  There also appear to be some Ubuntu threads in the google results.

Ah ha.  Here's the Ubuntu wiki for it:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)  And for Intrepid install it links to the Blue Wave site like the other Blue Wave page links to.

---

### Post by xSxTxOxRxMx on 2009-05-10
Thanks for looking into this for me.

I have already tried to use the updated drivers also, from Blue Wave.

I looked for the file 99-geniuspen.fdi but it wasn't there.

Could this be my problem?


Once again if I'm a bit slow to catch on to this, my apologies.

---

### Post by Favux on 2009-05-10
Hi xSxTxOxRxMx,

To get the tablet working you'll need both the driver and the .fdi.  If after checking around in the .fdi's you don't see one for your tablet like the 99-geniuspen.fdi (ie with WP8060U in it) it shouldn't hurt to install the .fdi where they tell you to.  Like I said maybe you'll get real lucky and Jaunty will already have some driver installed.  You reboot and bam.  Highly unlikely.

Also we had to fix our .fdi for our usb tablet pc's.  The default Jaunty .fdi didn't have touch which our tablets do.  Using the HAL sections for our tablet and the HAL spec. we figured it out.  Also the default 10-wacom.fdi isn't parsing the returned HAL names into linuxwacom names so nothing worked.  And we figured that out too.

It doesn't look the driver is packaged to automatically install a .fdi so you should be OK.  But watch out for that.  The way I read it is if you take the November alpha driver and make the change the Arch site guy recommends you should be able to successfully patch and install the driver with Jaunty's Xserver 1.6.  But you could contact either the Arch site guy or the Blue Wave guy and see what they recommend.  Probably the smart move.  And you should probably find the place where they're getting the original driver.  I can't remember was it Xorg?  Anyway the Arch site guy said he was going to update in a few days and it's been two already.

So while you're waiting you could read things through once or twice and do some more research and try to contact them.

Good luck!

---

### Post by xSxTxOxRxMx on 2009-05-11
Thanks for the help. :)

At this point I haven't gotten my tablet working yet.

I will keep trying, and when I do get it working I will post here again with the news and how I got it working.

---

### Post by practic on 2009-05-14
xSx,

I just spent over a day striking around in the dark trying to follow all the different tutorials to get my Genius G-Pen 560 working, only to find in the end that I had been sent on a wild goose chase, and the answer was much simpler than expected. 

From what I had read, I expected my Genius to use the Wizardpen driver, but I was wrong...it was an Aiptek unit inside, and I just needed to go to synaptic and install the xserver-xorg-input-aiptek driver, then create one small FDI file in the /etc/hal/fdi/policy/ directory, and it was working beautifully.

If I understand correctly, any Ubuntu system with 8.10 or 9.04 does not need to (and should not) edit xorg.conf for tablet parameters.  All of these go into an FDI file that the hardware abstraction layer handles directly. Some people try to blacklist the Hal rules and go to xorg.conf, but this is beyond my realm.

And, again if I understand right, there are three things we want: first, that the kernel has support for the tablet, second that there is a xorg-xserver driver, and third that there is a proper FDI file setup for HAL to use.

So, let's take these in order. First, when you plug in the tablet and after you restart your computer, is there any indication that the tablet is recognized? Does it move the mouse around on the screen when you move the stylus, or is there a light blinking on the tablet? Even before I had the driver and FDI setup, I was getting movement of the mouse cursor when I drew on the tablet...only it would not actually draw anything in an art program, and the button and tablet click wouldn't work either. But at least there was some kind of recognition that the device was there, which indicated to me that the kernel supported it.

To help identify your device, can you give us the output of the following commands?:

ls -la /dev/tablet-event

cat /sys/bus/usb/devices/*/product

grep -i name /proc/bus/input/devices

lsusb -v

lshal | less 

NOTE: It is best to pipe this command into a text file, such as: 

lshal | less > /home/owner/Desktop/x.txt 

...where "owner" is your username.  Then open the text file in GEdit and search for sections relating to your tablet device.  They may be lower down in the file, near where the keyboard and mouse are listed. If you find them, cut them out and save them in a separate file for future easy reference.

Secondly, we want the proper xorg-server driver for your device. There seem to be a few common ones in use: wacom, wizardpen, and aiptek. You've already tried the wizardpen driver, perhaps you can make sure that wacom and aiptek are installed from synaptic. As far as I know, they won't conflict with each other.

Please note that the xorg driver can be in a few places:
/usr/lib/xorg/modules/input
/usr/local/lib/xorg/modules/input

I think that the proper place is /usr/lib/xorg/modules/input, but one of the wizardpen sources I compiled ended up in /usr/local.  See what you can find.  The three drivers are called: aiptek_drv.so, wacom_drv.so, and wizardpen_drv.so.

Also, after your computer starts up, check your Xorg.0.log for errors relating to the loading of the tablet drivers.  You can find the error log at /var/log/Xorg.0.log.  The errors will have "(EE)" on the far left (beginning) of the text line, so they are fairly easy to spot.

When I initially tried the wizardpen driver, I found that the recent alpha 7 versions gave an error when trying to run with Ubuntu 8.10...I guess there was a Xorg mismatch.  They seemed to load fine in Ubuntu 9.04 (even though they were not the right drivers for my tablet).

And the last part of the setup is the FDI file. These can also be found in a few different places (and I'm not sure if one of these locations is prefered over the other):

/etc/hal/fdi/policy/
/usr/share/hal/fdi/policy/20thirdparty

You should create the file if it doesn't exist already.

a) for the Wizardpen, the file should be called 99-x11-wizardpen.fdi and should look something like this:

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<!-- This MUST match with the name of your tablet -->
<match key="info.product" contains="NAME OF YOUR TABLET">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
<merge key="input.x11_options.TopX" type="string">200</merge>
<merge key="input.x11_options.TopY" type="string">200</merge>
<merge key="input.x11_options.BottomX" type="string">18800</merge>
<merge key="input.x11_options.BottomY" type="string">12000</merge>
<merge key="input.x11_options.MaxX" type="string">18800</merge>
<merge key="input.x11_options.MaxY" type="string">12000</merge>
</match>
</device>
</deviceinfo>

Some people gained touch sensitivity by adding the following lines into the middle of the file:

<merge key="input.x11_options.topZ" type="string">5</merge>
<merge key="input.x11_options.bottomZ" type="string">511</merge>
<merge key="input.x11_options.maxZ" type="string">511</merge>

Note that some tablets have more levels of sensitivity and so 1023 might be better than 511 for the bottomZ and maxZ values.

b) for the Wacom the file should be called 10-wacom.fdi (mine is located in /usr/share/hal/fdi/policy/20thirdparty/). It is quite lengthy and probably already exists on your system, so I won't list it here.

c) for the Aiptek the file should be called 10-aiptek.fdi (mine is located in /etc/hal/fdi/policy/)and should look something like this:

<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<match key="info.product" contains="Aiptek">
<merge key="input.x11_driver" type="string">aiptek </merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
<merge key="input.x11_options.Type" type="string">stylus </merge>
<merge key="input.x11_options.Mode" type="string">absolute </merge>
<merge key="input.x11_options.zMin" type="string">0</merge>
<merge key="input.x11_options.zMax" type="string">1024</merge>
</match>
</device>
</deviceinfo>

There. That's about all I know about the subject. It cost some grief for me to get mine working, but in the end, the steps were quite simple and it works wonderfully even as a replacement mouse, but especially well in graphics programs like Gimp, Inkscape, Krita and MyPaint. Wish you the best...it is worth it when it finally works!

---

### Post by xSxTxOxRxMx on 2009-05-17
When I have my tablet plugged in, the only recognition I get is that when I tap the pen to the tablet, the light turns on. The cursor doesn't respond whatsoever to the pen movement.

Here are the outputs you requested:

**ls -la /dev/tablet-event**

lrwxrwxrwx 1 root root 12 2009-05-16 20:55 /dev/tablet-event -> input/event4



**cat /sys/bus/usb/devices/*/product**

Mass Storage Device
USB Receiver
Kensington USB/PS2 Orbit
Tablet WP8060U
EHCI Host Controller
EHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller



**grep -i name /proc/bus/input/devices**

```
N: Name="Power Button (FF)"
N: Name="Power Button (CM)"
N: Name="Macintosh mouse button emulation"
N: Name="Kensington      Kensington USB/PS2 Orbit"
N: Name="UC-LOGIC Tablet WP8060U"
N: Name="Logitech USB Receiver"
N: Name="Logitech USB Receiver"
N: Name="PC Speaker"



**lsusb -v**

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 006 Device 003: ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x5543 UC-Logic Technology Corp.
  idProduct          0x0005 Genius MousePen 8x6 Tablet
  bcdDevice            0.00
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
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              2 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     212
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
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 006 Device 002: ID 047d:1022 Kensington Orbit Optical
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x047d Kensington
  idProduct          0x1022 Orbit Optical
  bcdDevice            4.00
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
    MaxPower              100mA
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
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      50
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
        wMaxPacketSize     0x0003  1x 3 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 004 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc512 LX-700 Cordless Desktop Receiver
  bcdDevice           30.07
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
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
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
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
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     201
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
can't get hub descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```



**lshal | less**

```
Dumping 128 device(s) from the Global Device List:
-------------------------------------------------
udi = '/org/freedesktop/Hal/devices/computer'
  info.addons = {'hald-addon-cpufreq', 'hald-addon-acpi'} (string list)
  info.callouts.add = {'hal-acl-tool --remove-all', 'hal-storage-cleanup-all-mountpoints'} (string list)
  info.callouts.session_active = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_add = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_inactive = {'hal-acl-tool --reconfigure'} (string list)
  info.callouts.session_remove = {'hal-acl-tool --reconfigure'} (string list)
  info.capabilities = {'cpufreq_control'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq'} (string list)
  info.product = 'Computer'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer'  (string)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = {'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = {'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = {'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave'} (string list)
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = {'i', 'i', '', '', '', 'b'} (string list)
  power_management.acpi.linux.version = '20080926'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = true  (bool)
  power_management.type = 'acpi'  (string)
  system.board.product = 'M3A78-EM'  (string)
  system.board.serial = 'MS1C91BJ8H01110'  (string)
  system.board.vendor = 'ASUSTeK Computer INC.'  (string)
  system.board.version = 'Rev X.0x'  (string)
  system.chassis.manufacturer = 'Chassis Manufacture'  (string)
  system.chassis.type = 'Desktop'  (string)
  system.firmware.release_date = '01/09/2009'  (string)
  system.firmware.vendor = 'American Megatrends Inc.'  (string)
  system.firmware.version = '1401'  (string)
  system.formfactor = 'desktop'  (string)
  system.hardware.primary_video.product = 1555  (0x613)  (int)
  system.hardware.primary_video.vendor = 4318  (0x10de)  (int)
  system.hardware.product = 'System Product Name'  (string)
  system.hardware.serial = 'System Serial Number'  (string)
  system.hardware.uuid = '203D001E-8C00-01C3-09DF-00248C2E5194'  (string)
  system.hardware.vendor = 'System manufacturer'  (string)
  system.hardware.version = 'System Version'  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.28-11-generic'  (string)
  system.kernel.version.major = 2  (0x2)  (int)
  system.kernel.version.micro = 28  (0x1c)  (int)
  system.kernel.version.minor = 6  (0x6)  (int)

udi = '/org/freedesktop/Hal/devices/net_4a_ac_1e_b5_d6_6a'
  info.capabilities = {'net', 'net.bridge'} (string list)
  info.category = 'net.bridge'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Bridge Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_4a_ac_1e_b5_d6_6a'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/pan0'  (string)
  net.address = '4a:ac:1e:b5:d6:6a'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.bridge.mac_address = 82103110063722  (0x4aac1eb5d66a)  (uint64)
  net.interface = 'pan0'  (string)
  net.linux.ifindex = 5  (0x5)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  access_control.file = '/dev/snd/timer'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/timer'  (string)
  alsa.type = 'timer'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Timer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'  (string)
  linux.device_file = '/dev/snd/timer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'
  access_control.file = '/dev/sequencer2'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'  (string)
  linux.device_file = '/dev/sequencer2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer2'  (string)
  oss.device_file = '/dev/sequencer2'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'
  access_control.file = '/dev/sequencer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'OSS Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_oss_sequencer'  (string)
  linux.device_file = '/dev/sequencer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/sequencer'  (string)
  oss.device_file = '/dev/sequencer'  (string)
  oss.type = 'sequencer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  access_control.file = '/dev/snd/seq'  (string)
  access_control.type = 'sound'  (string)
  alsa.device_file = '/dev/snd/seq'  (string)
  alsa.type = 'sequencer'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'ALSA Sequencer Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'  (string)
  linux.device_file = '/dev/snd/seq'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  access_control.file = '/dev/input/event2'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Macintosh mouse button emulation'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'  (string)
  input.device = '/dev/input/event2'  (string)
  input.product = 'Macintosh mouse button emulation'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/virtual/input/input2/event2'  (string)

udi = '/org/freedesktop/Hal/devices/acpi_P001'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AMD Athlon(tm) 64 X2 Dual Core Processor 5200+'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_P001'  (string)
  linux.acpi_path = '/proc/acpi/processor/P001'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = true  (bool)
  processor.number = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/acpi_P002'
  info.capabilities = {'processor'} (string list)
  info.category = 'processor'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AMD Athlon(tm) 64 X2 Dual Core Processor 5200+'  (string)
  info.udi = '/org/freedesktop/Hal/devices/acpi_P002'  (string)
  linux.acpi_path = '/proc/acpi/processor/P002'  (string)
  linux.acpi_type = 1  (0x1)  (int)
  linux.hotplug_type = 4  (0x4)  (int)
  processor.can_throttle = false  (bool)
  processor.number = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.capabilities = {'net', 'net.loopback'} (string list)
  info.category = 'net.loopback'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Loopback device Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/virtual/net/lo'  (string)
  net.address = '00:00:00:00:00:00'  (string)
  net.arp_proto_hw_id = 772  (0x304)  (int)
  net.interface = 'lo'  (string)
  net.linux.ifindex = 1  (0x1)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button (CM)'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'  (string)
  input.device = '/dev/input/event1'  (string)
  input.product = 'Power Button (CM)'  (string)
  linux.device_file = '/dev/input/event1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1'  (string)

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  button.has_state = false  (bool)
  button.type = 'power'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.capabilities = {'input', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Power Button (FF)'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)
  input.device = '/dev/input/event0'  (string)
  input.product = 'Power Button (FF)'  (string)
  linux.device_file = '/dev/input/event0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'System Board'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0e'  (string)
  pnp.description = 'System Board'  (string)
  pnp.id = 'PNP0c01'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0d'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:09/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (PNP0103)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.id = 'PNP0103'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0400'
  info.linux.driver = 'parport_pc'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Standard LPT printer port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0400'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = 'Standard LPT printer port'  (string)
  pnp.id = 'PNP0400'  (string)

udi = '/org/freedesktop/Hal/devices/ppdev_parport0'
  access_control.file = '/dev/parport0'  (string)
  access_control.type = 'ppdev'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'ppdev', 'access_control'} (string list)
  info.category = 'ppdev'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0400'  (string)
  info.product = 'Parallel Port Device'  (string)
  info.subsystem = 'ppdev'  (string)
  info.udi = '/org/freedesktop/Hal/devices/ppdev_parport0'  (string)
  linux.device_file = '/dev/parport0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'ppdev'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07/ppdev/parport0'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PC standard floppy disk controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0700'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:06'  (string)
  pnp.description = 'PC standard floppy disk controller'  (string)
  pnp.id = 'PNP0700'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Math Coprocessor'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.description = 'Math Coprocessor'  (string)
  pnp.id = 'PNP0c04'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT-style speaker sound'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:04'  (string)
  pnp.description = 'AT-style speaker sound'  (string)
  pnp.id = 'PNP0800'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  info.linux.driver = 'rtc_cmos'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT Real-Time Clock'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:03'  (string)
  pnp.description = 'AT Real-Time Clock'  (string)
  pnp.id = 'PNP0b00'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'AT DMA Controller'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.description = 'AT DMA Controller'  (string)
  pnp.id = 'PNP0200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  info.linux.driver = 'system'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:01'  (string)
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'  (string)
  pnp.id = 'PNP0c02'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PCI Bus'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a03'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:00'  (string)
  pnp.description = 'PCI Bus'  (string)
  pnp.id = 'PNP0a03'  (string)

udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'
  info.linux.driver = 'vboxdrv'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (vboxdrv.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_vboxdrv_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/vboxdrv.0'  (string)
  platform.id = 'vboxdrv.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)

udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (regulatory.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/regulatory.0'  (string)
  platform.id = 'regulatory.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  info.linux.driver = 'pcspkr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (pcspkr)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr'  (string)
  platform.id = 'pcspkr'  (string)

udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'
  info.capabilities = {'input'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  info.product = 'PC Speaker'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'  (string)
  input.device = '/dev/input/event7'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_pcspkr'  (string)
  input.product = 'PC Speaker'  (string)
  linux.device_file = '/dev/input/event7'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/pcspkr/input/input7/event7'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042'
  info.linux.driver = 'i8042'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (i8042)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042'  (string)
  platform.id = 'i8042'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX port'  (string)
  serio.id = 'serio1'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 KBD port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'  (string)
  serio.description = 'i8042 KBD port'  (string)
  serio.id = 'serio0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_floppy_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (floppy.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_floppy_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/floppy.0'  (string)
  platform.id = 'floppy.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (eisa.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/eisa.0'  (string)
  platform.id = 'eisa.0'  (string)

udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (Fixed MDIO bus.0)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'  (string)
  platform.id = 'Fixed MDIO bus.0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1022_1103'
  info.linux.driver = 'k8temp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K8 [Athlon64/Opteron] Miscellaneous Control'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1103'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'  (string)
  pci.product = 'K8 [Athlon64/Opteron] Miscellaneous Control'  (string)
  pci.product_id = 4355  (0x1103)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_1102'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K8 [Athlon64/Opteron] DRAM Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1102'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'  (string)
  pci.product = 'K8 [Athlon64/Opteron] DRAM Controller'  (string)
  pci.product_id = 4354  (0x1102)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_1101'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K8 [Athlon64/Opteron] Address Map'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1101'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'  (string)
  pci.product = 'K8 [Athlon64/Opteron] Address Map'  (string)
  pci.product_id = 4353  (0x1101)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_1100'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'K8 [Athlon64/Opteron] HyperTransport Technology Configuration'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1100'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'  (string)
  pci.product = 'K8 [Athlon64/Opteron] HyperTransport Technology Configuration'  (string)
  pci.product_id = 4352  (0x1100)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4399'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB OHCI2 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4399'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5'  (string)
  pci.product = 'SB700/SB800 USB OHCI2 Controller'  (string)
  pci.product_id = 17305  (0x4399)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4399'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/007/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7'  (string)
  usb_device.bus_number = 7  (0x7)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:14.5'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_14_5_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0'  (string)
  usb.bus_number = 7  (0x7)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.5/usb7/7-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:14.5'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4384'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SBx00 PCI to PCI Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4384'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4'  (string)
  pci.product = 'SBx00 PCI to PCI Bridge'  (string)
  pci.product_id = 17284  (0x4384)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1814_301'
  info.linux.driver = 'rt61pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4384'  (string)
  info.product = 'RT2561/RT61 802.11g PCI'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)
  info.vendor = 'RaLink'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:04:07.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:04:07.0'  (string)
  pci.product = 'RT2561/RT61 802.11g PCI'  (string)
  pci.product_id = 769  (0x301)  (int)
  pci.subsys_product_id = 9569  (0x2561)  (int)
  pci.subsys_vendor = 'RaLink'  (string)
  pci.subsys_vendor_id = 6164  (0x1814)  (int)
  pci.vendor = 'RaLink'  (string)
  pci.vendor_id = 6164  (0x1814)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1814_301_rfkill_rt61pci_wlan'
  info.addons.singleton = {'hald-addon-rfkill-killswitch'} (string list)
  info.capabilities = {'killswitch'} (string list)
  info.category = 'killswitch'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.KillSwitch'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)
  info.product = 'rt61pci wlan Killswitch'  (string)
  info.subsystem = 'rfkill'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1814_301_rfkill_rt61pci_wlan'  (string)
  info.vendor = 'RaLink'  (string)
  killswitch.access_method = 'rfkill'  (string)
  killswitch.name = 'rt61pci'  (string)
  killswitch.state = 1  (0x1)  (int)
  killswitch.type = 'wlan'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'rfkill'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:04:07.0/rfkill/rfkill0'  (string)

udi = '/org/freedesktop/Hal/devices/net_00_1f_1f_3b_42_b6_0'
  info.capabilities = {'net', 'net.80211control'} (string list)
  info.category = 'net.80211control'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)
  info.product = 'Networking Wireless Control Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_1f_1f_3b_42_b6_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:04:07.0/net/wmaster0'  (string)
  net.address = '00:1f:1f:3b:42:b6'  (string)
  net.arp_proto_hw_id = 801  (0x321)  (int)
  net.interface = 'wmaster0'  (string)
  net.linux.ifindex = 3  (0x3)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)

udi = '/org/freedesktop/Hal/devices/net_00_1f_1f_3b_42_b6'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)
  info.product = 'WLAN Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_1f_1f_3b_42_b6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:04:07.0/net/wlan0'  (string)
  net.80211.mac_address = 133667963574  (0x1f1f3b42b6)  (uint64)
  net.address = '00:1f:1f:3b:42:b6'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'wlan0'  (string)
  net.linux.ifindex = 4  (0x4)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)

udi = '/org/freedesktop/Hal/devices/leds_rt61pci_phy0_0'
  info.capabilities = {'leds'} (string list)
  info.category = 'leds'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_rt61pci_phy0_0'  (string)
  leds.colour = 'radio'  (string)
  leds.device_name = 'rt61pci-phy0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:04:07.0/leds/rt61pci-phy0:radio'  (string)

udi = '/org/freedesktop/Hal/devices/leds_rt61pci_phy0'
  info.capabilities = {'leds'} (string list)
  info.category = 'leds'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1814_301'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_rt61pci_phy0'  (string)
  leds.colour = 'assoc'  (string)
  leds.device_name = 'rt61pci-phy0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.4/0000:04:07.0/leds/rt61pci-phy0:assoc'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_439d'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 LPC host controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439d'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.3'  (string)
  pci.product = 'SB700/SB800 LPC host controller'  (string)
  pci.product_id = 17309  (0x439d)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383'
  info.linux.driver = 'HDA Intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SBx00 Azalia (Intel HDA)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2'  (string)
  pci.product = 'SBx00 Azalia (Intel HDA)'  (string)
  pci.product_id = 17283  (0x4383)  (int)
  pci.subsys_product_id = 33534  (0x82fe)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)
  info.product = 'HDA ATI SB Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'HDA ATI SB'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_2'
  access_control.file = '/dev/snd/pcmC0D2c'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 2  (0x2)  (int)
  alsa.device_file = '/dev/snd/pcmC0D2c'  (string)
  alsa.device_id = 'ALC1200 Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_2'  (string)
  linux.device_file = '/dev/snd/pcmC0D2c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D2c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_1'
  access_control.file = '/dev/snd/pcmC0D1p'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1p'  (string)
  alsa.device_id = 'ALC1200 Digital'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Digital ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D1p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_1'
  access_control.file = '/dev/snd/pcmC0D1c'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 1  (0x1)  (int)
  alsa.device_file = '/dev/snd/pcmC0D1c'  (string)
  alsa.device_id = 'ALC1200 Digital'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Digital ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_1'  (string)
  linux.device_file = '/dev/snd/pcmC0D1c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_0'
  access_control.file = '/dev/snd/pcmC0D0p'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'ALC1200 Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Analog ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_0'
  access_control.file = '/dev/snd/pcmC0D0c'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'ALC1200 Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_mixer__1'
  access_control.file = '/dev/mixer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Analog OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'ALC1200 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0_0'
  access_control.file = '/dev/dsp'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'ALC1200 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1'
  access_control.file = '/dev/snd/controlC0'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA ATI SB'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'HDA ATI SB ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0'
  access_control.file = '/dev/audio'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'ALC1200 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_1'
  access_control.file = '/dev/adsp'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  info.product = 'ALC1200 Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0_oss_pcm_1'  (string)
  linux.device_file = '/dev/adsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.2/sound/card0/adsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA ATI SB'  (string)
  oss.device = 1  (0x1)  (int)
  oss.device_file = '/dev/adsp'  (string)
  oss.device_id = 'ALC1200 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_1002_4383_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c'
  info.linux.driver = 'pata_atiixp'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 IDE Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 138  (0x8a)  (int)
  pci.device_subclass = 1  (0x1)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1'  (string)
  pci.product = 'SB700/SB800 IDE Controller'  (string)
  pci.product_id = 17308  (0x439c)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host5/scsi_host/host5'  (string)
  scsi_host.host = 5  (0x5)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_439c'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_439c_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.1/host4/scsi_host/host4'  (string)
  scsi_host.host = 4  (0x4)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4385'
  info.linux.driver = 'piix4_smbus'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SBx00 SMBus Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4385'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 5  (0x5)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:14.0'  (string)
  pci.product = 'SBx00 SMBus Controller'  (string)
  pci.product_id = 17285  (0x4385)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4396_0'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4396_0'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2'  (string)
  pci.product = 'SB700/SB800 USB EHCI Controller'  (string)
  pci.product_id = 17302  (0x4396)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4396_0'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/002/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 6  (0x6)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:13.2'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_58f_6362_058F312D81B'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'  (string)
  info.product = 'Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_58f_6362_058F312D81B'  (string)
  info.vendor = 'Alcor Micro Corp.'  (string)
  linux.device_file = '/dev/bus/usb/002/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3'  (string)
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = false  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 297  (0x129)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3'  (string)
  usb_device.max_power = 250  (0xfa)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)'  (string)
  usb_device.product_id = 25442  (0x6362)  (int)
  usb_device.serial = '058F312D81B'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Alcor Micro Corp.'  (string)
  usb_device.vendor_id = 1423  (0x58f)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_58f_6362_058F312D81B_if0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_58f_6362_058F312D81B'  (string)
  info.product = 'USB Mass Storage Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_58f_6362_058F312D81B_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = false  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 297  (0x129)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 8  (0x8)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 80  (0x50)  (int)
  usb.interface.subclass = 6  (0x6)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-3/2-3:1.0'  (string)
  usb.max_power = 250  (0xfa)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB Mass Storage Interface'  (string)
  usb.product_id = 25442  (0x6362)  (int)
  usb.serial = '058F312D81B'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Alcor Micro Corp.'  (string)
  usb.vendor_id = 1423  (0x58f)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_13_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.2/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 6  (0x6)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:13.2'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4398_0'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700 USB OHCI1 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4398_0'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1'  (string)
  pci.product = 'SB700 USB OHCI1 Controller'  (string)
  pci.product_id = 17304  (0x4398)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4398_0'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/006/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6'  (string)
  usb_device.bus_number = 6  (0x6)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:13.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'  (string)
  info.product = 'Genius MousePen 8x6 Tablet'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial'  (string)
  info.vendor = 'UC-Logic Technology Corp.'  (string)
  linux.device_file = '/dev/bus/usb/006/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-3'  (string)
  usb_device.bus_number = 6  (0x6)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 0  (0x0)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-3'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Genius MousePen 8x6 Tablet'  (string)
  usb_device.product_id = 5  (0x5)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'UC-Logic Technology Corp.'  (string)
  usb_device.vendor_id = 21827  (0x5543)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-3/6-3:1.0'  (string)
  usb.bus_number = 6  (0x6)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 0  (0x0)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.description = 'Tablet WP8060U'  (string)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 3  (0x3)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-3/6-3:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 5  (0x5)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'UC-Logic Technology Corp.'  (string)
  usb.vendor_id = 21827  (0x5543)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0_logicaldev_input'
  access_control.file = '/dev/input/event4'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.mouse', 'input.tablet', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0'  (string)
  info.product = 'UC-LOGIC Tablet WP8060U'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event4'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_5543_5_noserial_if0'  (string)
  input.product = 'UC-LOGIC Tablet WP8060U'  (string)
  input.x11_driver = 'wizardpen'  (string)
  input.x11_options.BottomX = '29405'  (string)
  input.x11_options.BottomY = '29671'  (string)
  input.x11_options.MaxX = '29405'  (string)
  input.x11_options.MaxY = '29671'  (string)
  input.x11_options.SendCoreEvents = 'true'  (string)
  input.x11_options.TopX = '5619'  (string)
  input.x11_options.TopY = '6554'  (string)
  linux.device_file = '/dev/input/event4'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-3/6-3:1.0/input/input4/event4'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'  (string)
  info.product = 'Orbit Optical'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial'  (string)
  info.vendor = 'Kensington'  (string)
  linux.device_file = '/dev/bus/usb/006/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2'  (string)
  usb_device.bus_number = 6  (0x6)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 1024  (0x400)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Orbit Optical'  (string)
  usb_device.product_id = 4130  (0x1022)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Kensington'  (string)
  usb_device.vendor_id = 1149  (0x47d)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0'  (string)
  usb.bus_number = 6  (0x6)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 1024  (0x400)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0'  (string)
  usb.max_power = 100  (0x64)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 4130  (0x1022)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Kensington'  (string)
  usb.vendor_id = 1149  (0x47d)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial_if0_logicaldev_input'
  access_control.file = '/dev/input/event3'  (string)
  access_control.type = 'mouse'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.mouse', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial_if0'  (string)
  info.product = 'Kensington      Kensington USB/PS2 Orbit'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_47d_1022_noserial_if0'  (string)
  input.product = 'Kensington      Kensington USB/PS2 Orbit'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-2/6-2:1.0/input/input3/event3'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0'  (string)
  usb.bus_number = 6  (0x6)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.1/usb6/6-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:13.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4397_0'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4397_0'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0'  (string)
  pci.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  pci.product_id = 17303  (0x4397)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4397_0'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/005/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5'  (string)
  usb_device.bus_number = 5  (0x5)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:13.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_13_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0'  (string)
  usb.bus_number = 5  (0x5)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:13.0/usb5/5-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:13.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4396'
  info.linux.driver = 'ehci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB EHCI Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4396'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 32  (0x20)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2'  (string)
  pci.product = 'SB700/SB800 USB EHCI Controller'  (string)
  pci.product_id = 17302  (0x4396)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4396'  (string)
  info.product = '2.0 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/001/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1'  (string)
  usb_device.bus_number = 1  (0x1)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 6  (0x6)  (int)
  usb_device.product = '2.0 root hub'  (string)
  usb_device.product_id = 2  (0x2)  (int)
  usb_device.serial = '0000:00:12.2'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_12_2_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0'  (string)
  usb.bus_number = 1  (0x1)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 6  (0x6)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 2  (0x2)  (int)
  usb.serial = '0000:00:12.2'  (string)
  usb.speed = 480.0 (480) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 2.0 (2) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4398'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700 USB OHCI1 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4398'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1'  (string)
  pci.product = 'SB700 USB OHCI1 Controller'  (string)
  pci.product_id = 17304  (0x4398)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4398'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/004/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:12.1'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial'
  battery.csr.has_res = false  (bool)
  battery.csr.has_sms = false  (bool)
  battery.csr.is_dual = false  (bool)
  battery.type = 'keyboard'  (string)
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'  (string)
  info.product = 'Cordless Keyboard+Mouse Receiver'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial'  (string)
  info.vendor = 'Logitech, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/004/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1'  (string)
  usb_device.bus_number = 4  (0x4)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 12295  (0x3007)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = false  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1'  (string)
  usb_device.max_power = 98  (0x62)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 2  (0x2)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'LX-700 Cordless Desktop Receiver'  (string)
  usb_device.product_id = 50450  (0xc512)  (int)
  usb_device.speed = 1.5 (1.5) (double)
  usb_device.vendor = 'Logitech, Inc.'  (string)
  usb_device.vendor_id = 1133  (0x46d)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if1'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 12295  (0x3007)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 1  (0x1)  (int)
  usb.interface.protocol = 2  (0x2)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 50450  (0xc512)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if1_logicaldev_input'
  access_control.file = '/dev/input/event6'  (string)
  access_control.type = 'mouse'  (string)
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard', 'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'input', 'input.keys', 'input.mouse', 'button', 'access_control'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if1'  (string)
  info.product = 'Logitech USB Receiver'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if1_logicaldev_input'  (string)
  input.device = '/dev/input/event6'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if1'  (string)
  input.product = 'Logitech USB Receiver'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event6'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.1/input/input6/event6'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if0'
  info.linux.driver = 'usbhid'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 12295  (0x3007)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 1  (0x1)  (int)
  usb.interface.subclass = 1  (0x1)  (int)
  usb.is_self_powered = false  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0'  (string)
  usb.max_power = 98  (0x62)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 2  (0x2)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 50450  (0xc512)  (int)
  usb.speed = 1.5 (1.5) (double)
  usb.vendor = 'Logitech, Inc.'  (string)
  usb.vendor_id = 1133  (0x46d)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if0_logicaldev_input'
  info.addons.singleton = {'hald-addon-input'} (string list)
  info.callouts.add = {'debian-setup-keyboard'} (string list)
  info.capabilities = {'input', 'input.keyboard', 'input.keypad', 'input.keys', 'button'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if0'  (string)
  info.product = 'Logitech USB Receiver'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event5'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_46d_c512_noserial_if0'  (string)
  input.product = 'Logitech USB Receiver'  (string)
  input.x11_driver = 'evdev'  (string)
  input.xkb.layout = 'us'  (string)
  input.xkb.model = 'pc105'  (string)
  input.xkb.rules = 'evdev'  (string)
  linux.device_file = '/dev/input/event5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input5/event5'  (string)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_1_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0'  (string)
  usb.bus_number = 4  (0x4)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.1/usb4/4-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:12.1'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4397'
  info.linux.driver = 'ohci_hcd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4397'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'  (string)
  pci.product = 'SB700/SB800 USB OHCI0 Controller'  (string)
  pci.product_id = 17303  (0x4397)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4397'  (string)
  info.product = '1.1 root hub'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'  (string)
  info.vendor = 'Linux Foundation'  (string)
  linux.device_file = '/dev/bus/usb/003/001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3'  (string)
  usb_device.bus_number = 3  (0x3)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 3  (0x3)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:12.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_12_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0'  (string)
  usb.bus_number = 3  (0x3)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0/usb3/3-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 3  (0x3)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:12.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390'
  info.linux.driver = 'ahci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'SB700/SB800 SATA Controller [IDE mode]'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.vendor = 'ATI Technologies Inc'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0'  (string)
  pci.device_class = 1  (0x1)  (int)
  pci.device_protocol = 1  (0x1)  (int)
  pci.device_subclass = 6  (0x6)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0'  (string)
  pci.product = 'SB700/SB800 SATA Controller [IDE mode]'  (string)
  pci.product_id = 17296  (0x4390)  (int)
  pci.subsys_product_id = 33519  (0x82ef)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'ATI Technologies Inc'  (string)
  pci.vendor_id = 4098  (0x1002)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_2'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host3/scsi_host/host3'  (string)
  scsi_host.host = 3  (0x3)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_1'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host1/scsi_host/host1'  (string)
  scsi_host.host = 1  (0x1)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host2/scsi_host/host2'  (string)
  scsi_host.host = 2  (0x2)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'
  info.linux.driver = 'sr'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host2/target2:0:0/2:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 2  (0x2)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'CDDVDW SH-S223Q'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'cdrom'  (string)
  scsi.vendor = 'TSSTcorp'  (string)

udi = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223Q'
  access_control.file = '/dev/sr0'  (string)
  access_control.type = 'cdrom'  (string)
  block.device = '/dev/sr0'  (string)
  block.is_volume = false  (bool)
  block.major = 11  (0xb)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223Q'  (string)
  info.addons = {'hald-addon-storage'} (string list)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'storage', 'block', 'storage.cdrom', 'access_control'} (string list)
  info.category = 'storage'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'CDDVDW SH-S223Q'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_CDDVDW_SH_S223Q'  (string)
  info.vendor = 'TSSTcorp'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host2/target2:0:0/2:0:0:0/block/sr0'  (string)
  org.freedesktop.Hal.Device.Storage.method_argnames = {'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Storage.method_execpaths = {'hal-storage-eject', 'hal-storage-closetray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_names = {'Eject', 'CloseTray'} (string list)
  org.freedesktop.Hal.Device.Storage.method_signatures = {'as', 'as'} (string list)
  storage.automount_enabled_hint = true  (bool)
  storage.bus = 'pci'  (string)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.dvdplusr = true  (bool)
  storage.cdrom.dvdplusrdl = true  (bool)
  storage.cdrom.dvdplusrw = true  (bool)
  storage.cdrom.dvdplusrwdl = false  (bool)
  storage.cdrom.dvdr = true  (bool)
  storage.cdrom.dvdram = true  (bool)
  storage.cdrom.dvdrdl = true  (bool)
  storage.cdrom.dvdrw = true  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.mo = false  (bool)
  storage.cdrom.mrw = true  (bool)
  storage.cdrom.mrw_w = true  (bool)
  storage.cdrom.read_speed = 8468  (0x2114)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.support_multisession = true  (bool)
  storage.cdrom.write_speed = 8468  (0x2114)  (int)
  storage.drive_type = 'cdrom'  (string)
  storage.firmware_version = 'SB03'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = true  (bool)
  storage.model = 'CDDVDW SH-S223Q'  (string)
  storage.no_partitions_hint = true  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = ''  (string)
  storage.removable = true  (bool)
  storage.removable.media_available = false  (bool)
  storage.removable.support_async_notification = false  (bool)
  storage.requires_eject = true  (bool)
  storage.size = 0  (0x0)  (uint64)
  storage.vendor = 'TSSTcorp'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0_scsi_generic'
  access_control.file = '/dev/sg1'  (string)
  access_control.type = 'cdrom'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'scsi_generic', 'access_control'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_0_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg1'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg1'  (string)
  scsi_generic.device = '/dev/sg1'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_host'
  info.capabilities = {'scsi_host'} (string list)
  info.category = 'scsi_host'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'  (string)
  info.product = 'SCSI Host Adapter'  (string)
  info.subsystem = 'scsi_host'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_host'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_host'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/scsi_host/host0'  (string)
  scsi_host.host = 0  (0x0)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'
  info.linux.driver = 'sd'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host'  (string)
  info.product = 'SCSI Device'  (string)
  info.subsystem = 'scsi'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0'  (string)
  scsi.bus = 0  (0x0)  (int)
  scsi.host = 0  (0x0)  (int)
  scsi.lun = 0  (0x0)  (int)
  scsi.model = 'WDC WD5000AAKS-0'  (string)
  scsi.target = 0  (0x0)  (int)
  scsi.type = 'disk'  (string)
  scsi.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'
  block.device = '/dev/sda'  (string)
  block.is_volume = false  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 0  (0x0)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.capabilities = {'storage', 'block'} (string list)
  info.category = 'storage'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'  (string)
  info.product = 'WDC WD5000AAKS-0'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.vendor = 'ATA'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda'  (string)
  storage.automount_enabled_hint = false  (bool)
  storage.bus = 'pci'  (string)
  storage.drive_type = 'disk'  (string)
  storage.firmware_version = '07.0'  (string)
  storage.hotpluggable = false  (bool)
  storage.lun = 0  (0x0)  (int)
  storage.media_check_enabled = false  (bool)
  storage.model = 'WDC WD5000AAKS-0'  (string)
  storage.no_partitions_hint = false  (bool)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'  (string)
  storage.partitioning_scheme = 'mbr'  (string)
  storage.removable = false  (bool)
  storage.removable.media_available = true  (bool)
  storage.removable.media_size = 500107862016  (0x7470c06000)  (uint64)
  storage.requires_eject = false  (bool)
  storage.serial = 'SATA_WDC_WD5000AAKS-_WD-WMASY7142397'  (string)
  storage.size = 500107862016  (0x7470c06000)  (uint64)
  storage.vendor = 'ATA'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_9d1b7a57_4c93_4fa0_80d9_7062e950fa41'
  block.device = '/dev/sda6'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 6  (0x6)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.product = 'Volume (swap)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_9d1b7a57_4c93_4fa0_80d9_7062e950fa41'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda6'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'swap'  (string)
  volume.fsusage = 'other'  (string)
  volume.fsversion = '2'  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 12080817  (0xb856b1)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 6  (0x6)  (int)
  volume.partition.start = 493919870976  (0x72ffeb2000)  (uint64)
  volume.size = 6185378304  (0x170ad6200)  (uint64)
  volume.uuid = '9d1b7a57-4c93-4fa0-80d9-7062e950fa41'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_C8FC8B36FC8B1E36'
  block.device = '/dev/sda1'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 1  (0x1)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.product = 'Volume (ntfs)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_C8FC8B36FC8B1E36'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda1'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ntfs-3g'  (string)
  volume.fstype.alternative = 'ntfs'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '3.1'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.ntfs.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'uid=', 'gid=', 'umask=', 'utf8'} (string list)
  volume.mount.valid_options = {'ro', 'atime', 'noatime', 'relatime', 'fake_rw', 'no_def_opts', 'default_permissions', 'umask=', 'fmask=', 'dmask=', 'uid=', 'gid=', 'show_sys_files', 'silent', 'force', 'remove_hiberfile', 'locale=', 'streams_interface=', 'debug', 'no_detatch', 'sync', 'dirsync', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'recover', 'norecover'} (string list)
  volume.mount_point = ''  (string)
  volume.num_blocks = 209760642  (0xc80b182)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 1  (0x1)  (int)
  volume.partition.start = 32256  (0x7e00)  (uint64)
  volume.policy.mount_filesystem = 'ntfs-3g'  (string)
  volume.size = 107397448704  (0x1901630400)  (uint64)
  volume.unmount.ntfs.valid_options = {'lazy'} (string list)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = 'C8FC8B36FC8B1E36'  (string)

udi = '/org/freedesktop/Hal/devices/volume_uuid_2d1b5c37_cd23_4362_8322_0c3b30acfe04'
  block.device = '/dev/sda5'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 5  (0x5)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Volume'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.product = 'Volume (ext3)'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_2d1b5c37_cd23_4362_8322_0c3b30acfe04'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda5'  (string)
  org.freedesktop.Hal.Device.Volume.method_argnames = {'mount_point fstype extra_options', 'extra_options', 'extra_options'} (string list)
  org.freedesktop.Hal.Device.Volume.method_execpaths = {'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_names = {'Mount', 'Unmount', 'Eject'} (string list)
  org.freedesktop.Hal.Device.Volume.method_signatures = {'ssas', 'as', 'as'} (string list)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = 'ext3'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fsversion = '1.0'  (string)
  volume.ignore = false  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = true  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount.valid_options = {'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'noexec', 'quiet', 'remount', 'exec', 'acl', 'user_xattr', 'data='} (string list)
  volume.mount_point = '/'  (string)
  volume.num_blocks = 754926417  (0x2cff4351)  (uint64)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 5  (0x5)  (int)
  volume.partition.start = 107397513216  (0x1901640000)  (uint64)
  volume.size = 386522325504  (0x59fe86a200)  (uint64)
  volume.unmount.valid_options = {'lazy'} (string list)
  volume.uuid = '2d1b5c37-cd23-4362-8322-0c3b30acfe04'  (string)

udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.device = '/dev/sda2'  (string)
  block.is_volume = true  (bool)
  block.major = 8  (0x8)  (int)
  block.minor = 2  (0x2)  (int)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SATA_WDC_WD5000AAKS__WD_WMASY7142397'  (string)
  info.product = 'Volume'  (string)
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/block/sda/sda2'  (string)
  volume.block_size = 512  (0x200)  (int)
  volume.fstype = ''  (string)
  volume.fsusage = 'partitiontable'  (string)
  volume.fsversion = ''  (string)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.is_mounted_read_only = false  (bool)
  volume.is_partition = true  (bool)
  volume.label = ''  (string)
  volume.linux.is_device_mapper = false  (bool)
  volume.mount_point = ''  (string)
  volume.num_blocks = 2  (0x2)  (uint64)
  volume.partition.flags = {} (string list)
  volume.partition.label = ''  (string)
  volume.partition.media_size = 500107862016  (0x7470c06000)  (uint64)
  volume.partition.number = 2  (0x2)  (int)
  volume.partition.scheme = 'mbr'  (string)
  volume.partition.start = 107397480960  (0x1901638200)  (uint64)
  volume.partition.type = '0x05'  (string)
  volume.partition.uuid = ''  (string)
  volume.size = 1024  (0x400)  (uint64)
  volume.uuid = ''  (string)

udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0_scsi_generic'
  info.capabilities = {'scsi_generic'} (string list)
  info.category = 'scsi_generic'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0'  (string)
  info.product = 'SCSI Generic Interface'  (string)
  info.subsystem = 'scsi_generic'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1002_4390_scsi_host_scsi_device_lun0_scsi_generic'  (string)
  linux.device_file = '/dev/sg0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'scsi_generic'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:11.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'  (string)
  scsi_generic.device = '/dev/sg0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_1022_9606'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RS780 PCI to PCI bridge (PCIE port 2)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9606'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0'  (string)
  pci.product = 'RS780 PCI to PCI bridge (PCIE port 2)'  (string)
  pci.product_id = 38406  (0x9606)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10ec_8168'
  info.linux.driver = 'r8169'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9606'  (string)
  info.product = 'RTL8111/8168B PCI Express Gigabit Ethernet controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10ec_8168'  (string)
  info.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/0000:03:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/0000:03:00.0'  (string)
  pci.product = 'RTL8111/8168B PCI Express Gigabit Ethernet controller'  (string)
  pci.product_id = 33128  (0x8168)  (int)
  pci.subsys_product_id = 33478  (0x82c6)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  pci.vendor_id = 4332  (0x10ec)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_24_8c_2e_51_94'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_10ec_8168'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_24_8c_2e_51_94'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/0000:03:00.0/net/eth0'  (string)
  net.80203.mac_address = 156970668436  (0x248c2e5194)  (uint64)
  net.address = '00:24:8c:2e:51:94'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10ec_8168'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_1022_9605'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RS780 PCI to PCI bridge (PCIE port 1)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9605'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0'  (string)
  pci.product = 'RS780 PCI to PCI bridge (PCIE port 1)'  (string)
  pci.product_id = 38405  (0x9605)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_197b_2380'
  info.linux.driver = 'ohci1394'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9605'  (string)
  info.product = 'IEEE 1394 Host Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_197b_2380'  (string)
  info.vendor = 'JMicron Technologies, Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0'  (string)
  pci.device_class = 12  (0xc)  (int)
  pci.device_protocol = 16  (0x10)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0'  (string)
  pci.product = 'IEEE 1394 Host Controller'  (string)
  pci.product_id = 9088  (0x2380)  (int)
  pci.subsys_product_id = 33555  (0x8313)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'JMicron Technologies, Inc.'  (string)
  pci.vendor_id = 6523  (0x197b)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_9603'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RS780 PCI to PCI bridge (ext gfx port 0)'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9603'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.product = 'RS780 PCI to PCI bridge (ext gfx port 0)'  (string)
  pci.product_id = 38403  (0x9603)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10de_613'
  info.linux.driver = 'nvidia'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9603'  (string)
  info.product = 'GeForce 9800 GTX+'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_613'  (string)
  info.vendor = 'nVidia Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0'  (string)
  pci.product = 'GeForce 9800 GTX+'  (string)
  pci.product_id = 1555  (0x613)  (int)
  pci.subsys_product_id = 51321  (0xc879)  (int)
  pci.subsys_vendor = 'eVga.com. Corp.'  (string)
  pci.subsys_vendor_id = 14402  (0x3842)  (int)
  pci.vendor = 'nVidia Corporation'  (string)
  pci.vendor_id = 4318  (0x10de)  (int)

udi = '/org/freedesktop/Hal/devices/pci_1022_9600'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'RS780 Host Bridge'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_9600'  (string)
  info.vendor = 'Advanced Micro Devices [AMD]'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = 'RS780 Host Bridge'  (string)
  pci.product_id = 38400  (0x9600)  (int)
  pci.subsys_product_id = 33521  (0x82f1)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'Advanced Micro Devices [AMD]'  (string)
  pci.vendor_id = 4130  (0x1022)  (int)

udi = '/org/freedesktop/Hal/devices/fuse'
  access_control.file = '/dev/fuse'  (string)
  access_control.type = 'camera'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'access_control'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_1022_9600'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/fuse'  (string)


Dumped 128 device(s) from the Global Device List.
------------------------------------------------
```


Here is the Xorg.0.log

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Abarillious-III 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 17 01:58:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 9800 GTX+ rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.64.00.74
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9800 GTX+ at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     ACI VW192 (DFP-0)
(--) NVIDIA(0): ACI VW192 (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): ACI VW192 (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (104, 102); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 32 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device UC-LOGIC Tablet WP8060U
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input//wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(EE) module ABI major version (2) doesn't match the server's version (4)
(II) UnloadModule: "wizardpen"
(II) Unloading /usr/lib/xorg/modules/input//wizardpen_drv.so
(EE) Failed to load module "wizardpen" (module requirement mismatch, 0)
(EE) No input driver matching `wizardpen'
(EE) config/hal: NewInputDeviceRequest failed (15)
(II) config/hal: Adding input device Kensington      Kensington USB/PS2 Orbit
(**) Kensington      Kensington USB/PS2 Orbit: always reports core events
(**) Kensington      Kensington USB/PS2 Orbit: Device: "/dev/input/event3"
(II) Kensington      Kensington USB/PS2 Orbit: Found 2 mouse buttons
(II) Kensington      Kensington USB/PS2 Orbit: Found x and y relative axes
(II) Kensington      Kensington USB/PS2 Orbit: Configuring as mouse
(**) Kensington      Kensington USB/PS2 Orbit: YAxisMapping: buttons 4 and 5
(**) Kensington      Kensington USB/PS2 Orbit: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Kensington      Kensington USB/PS2 Orbit" (type: MOUSE)
(**) Kensington      Kensington USB/PS2 Orbit: (accel) keeping acceleration scheme 1
(**) Kensington      Kensington USB/PS2 Orbit: (accel) filter chain progression: 2.00
(**) Kensington      Kensington USB/PS2 Orbit: (accel) filter stage 0: 20.00 ms
(**) Kensington      Kensington USB/PS2 Orbit: (accel) set acceleration profile 0
```

I got the aiptek driver from synaptic.
I found the wacom .fdi file, but I couldn't find the wizardpen one, which is strange because I was sure I had that. I added it and the aiptek .fdi files.

With the new changes, I restarted but there is no improvement, the tablet still has no effect on the cursor.

I appreciate the help :) I'm glad you got yours working. :D
I noticed some errors regarding wizardpen in the xorg log, maybe that's my problem? I hope the outputs can help shed some light on my issue.

---

### Post by fugo on 2009-05-21
You can try this link : [[COLOR="Navy"]http://www.jpbouza.com.ar/ESP2/tutoriales/linux/genius-tablet/id/en[/COLOR]]("http://www.jpbouza.com.ar/ESP2/tutoriales/linux/genius-tablet/id/en")
It worked for me but without pressure sensitivity. 
hope you find it helpful :)

---

### Post by fugo on 2009-05-29
The pressure sensitivity seems to be working well after all :p, but i can't figure how to make it work with gimp though it works with another painting software.

---

### Post by jpbouza on 2009-06-08
Fugo! I´m glad that the tutorials I gathered from the web let you use the Tablet!!

Did you select the right device in the ¨input device¨ menu in Gimp?

If you have pressure working in Blender, you should be able to select ¨stylus¨ in the gimp input device properties.

---

### Post by BCtom on 2009-07-05
I just wanted to let you all that I have the exact same tablet, a WP8060U, and reading what Favux posted here on this thread, it worked right off the bat from the first try following his words, and the aid of this link: 

[http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en](http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en)

I personally think that because I had messed with the xorg.config file so badly trying in vein to get my tablet working that I basicly did a fresh install of Jaunty. (Yes, I know, why was I editing the Xorg.Config file????) I just followed the steps and Voilá, it worked. I did spend a lot of time trying to get it to work, and I must have edited that Xorg file a 100 times. Even the FDI files were messed up from me editing them so much once I figured out that those were the files to edit. 

In hindsight, I think is was easyer installing for Jaunty than is was for Hardy. 

One day I would like to see LINUX, or Ubuntu, have plug and play for all such devices. But of course, they would start charging money for it....

---

### Post by Silvenium on 2009-07-07
> **BCtom said:**
> I just wanted to let you all that I have the exact same tablet, a WP8060U, and reading what Favux posted here on this thread, it worked right off the bat from the first try following his words, and the aid of this link: 

[http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en](http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en)

I personally think that because I had messed with the xorg.config file so badly trying in vein to get my tablet working that I basicly did a fresh install of Jaunty. (Yes, I know, why was I editing the Xorg.Config file????) I just followed the steps and Voilá, it worked. I did spend a lot of time trying to get it to work, and I must have edited that Xorg file a 100 times. Even the FDI files were messed up from me editing them so much once I figured out that those were the files to edit. 

In hindsight, I think is was easyer installing for Jaunty than is was for Hardy. 

One day I would like to see LINUX, or Ubuntu, have plug and play for all such devices. But of course, they would start charging money for it....


Hey, I've done everything on the Juan Pablo page right, but... On your link's 'compiling driver' chapter, number 5... it gives the error 'bash: ./configure: No such file or directory'. What's the deal with that? Everything's installed properly so far on the page; I've been following the rules.

However, when I do the next command (step 6) it shows the .la and .so files. 

I tried to go to the next step, but it won't show my MousePen. It just shows the devices 'Power Button (FF)', 'Power Button (CM)', 'Macintosh mouse button emulation', 'Logitech Logitech USB Keyboard', and 'ImExPS/2 Generic Explorer Mouse'.

---

### Post by coCoKNIght on 2009-07-13
I already had my g-pen 560 working quiet well with the wizardpen driver, but the two extra buttons on the stylus didn't work, that's why I kept searching. I was surprised to hear about the aiptek driver, tryed it and it works, and one of the two extra buttons act as right mouse button, but the mapping and pressure sensitivity is better with the wizardpen driver.
Does anybody know how to make the buttons work with the wizardpen driver, or else how to finetune the aiptek driver? thanks.

---

### Post by Favux on 2009-07-13
Hi coCoKNIght,

We took a crack at it on this thread:  [http://ubuntuforums.org/showthread.php?t=1191826](http://ubuntuforums.org/showthread.php?t=1191826) with inconclusive results.  You might want to look through the thread.  Maybe you could come up with something we missed.  It should give you some ideas for tuning anyway.  The "current" aiptek.fdi we produced is in post #50.

Good luck!

---

### Post by coCoKNIght on 2009-07-13
Thanks Favux, I tried some settings for the aiptek driver but with no improvement. Also, using the aiptek driver when unplugging the tablet (for the .fdi changes to take effect) X restarts. This does not happen with the wizardpen driver.
So I'm back with the wizardpen driver and still looking for some options to make the stylus buttons work...

---

### Post by Favux on 2009-07-13
Hi coCoKNIght,

Yes, we found the X breakage when uplugging also.  Does wizardpen have a manual like the aiptek?

"man wizardpen" instead of "man aiptek"

---

### Post by coCoKNIght on 2009-07-13
yes, wizardpen has a man entry, the only driver specific options described there are: TopX, TopY, TopZ, BottomX, BottomY, BottomZ
If you're interested on the wizardpen driver I'd recomend you to read my post about it on my website: [G-Pen 560 on Jaunty]("http://cocoknight.com/g-pen-560-on-jaunty/")

---

### Post by coCoKNIght on 2009-07-13
```
xinput list
``` tells me that my tablet has 6 buttons.
with ```
xinput query-state 6
``` where 6 is the id of my tablet I can check that only button one ever changes state to down (when I press the stylus against the tablet). When I press any of the two extra buttons on the stylus, the state of none of the 6 buttons from the xinput output changes.
Does this mean that with the driver I'm using (Wizardpen) these buttons are not suported?

---

### Post by Favux on 2009-07-13
Hi coCoKNIght,

A Wacom stylus has two options.  Stylus tip + stylus button (for a button click), or hover mode where it's just the stylus button as long as it's in close enough proximity to the tablet.  It looks like the Aiptek driver has the first option for one button hard coded.

But since Xinput sees the tablet as a "mouse"  (ExtensionPointer) could something like this have any relevance?:  [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)  I have no idea.

And the Ubuntu X input wiki:  [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

And the HAL version:  [http://people.freedesktop.org/~hughsient/quirk/](http://people.freedesktop.org/~hughsient/quirk/)

---

### Post by coCoKNIght on 2009-07-14
For buttons configuration I think **input.x11_options.ButtonMapping** looks interesting. See [Logitech Marblemouse USB]("https://help.ubuntu.com/community/Logitech_Marblemouse_USB"). However with the Wizardpen driver I see nothing happening at all when I press one of the two extra buttons on the stylus.

With the Aiptek and the Wacom driver I'm happy that one button works as right click "out of the box", but pressure sensitivity doesn't work well with the Aiptek driver and with both of these drivers I got difficulties reaching the corners of the screen with the cursor (I've 'scale:initiate window picker' on the top left corner).

I think I'll have a look at the wacom options next to see If I can get rid of the corner problem.

---

### Post by Favux on 2009-07-15
Hi coCoKNIght,

Marc found a good reference to X ButtonEvents on post #59 in this thread here:  [http://ubuntuforums.org/showthread.php?t=1191826&page=6](http://ubuntuforums.org/showthread.php?t=1191826&page=6)  It's the xlib manual.

---

### Post by DoctorMO on 2009-07-18
Can you guys with wizardpen tablets try my ppa:

[https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

And report bugs as required:

[https://bugs.launchpad.net/wizardpen](https://bugs.launchpad.net/wizardpen)

Hopefully this deals with all fdi requirements as well as building on all platforms.

---

### Post by minimala on 2009-09-10
Hello, I'm running 9.04 Jaunty amd64 on an Intel Pentium D 820 2.8GHz 945G PC. I'm a newbie in Ubuntu and Linux, but I slowly get better. I have it as my primary, and only for now, OS for two weeks now and I have got working printer and file sharing accross my network, joysticks and everything else but I can't install my Genius MousePen 8x6 Tablet. The $ lsusb command returns it as:
```

$ lsusb
Bus 001 Device 005: ID 04e8:341b Samsung Electronics Co., Ltd SCX-4200 Series
Bus 001 Device 004: ID 0dda:2001 Integrated Circuit Solution, Inc. Multi-Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 5543:0005 **UC-Logic Technology Corp. Genius MousePen 8x6 Tablet**
Bus 004 Device 003: ID 12bd:a02f  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```It's obviously found by the system, but every guide on how to install it ends for me on "Install wizardpen", because the .deb package provided is i386. I have the i386.deb package and the tar.gz. I don't know how to compile the tar.gz for amd64, and I don't even know if it is possible... Every time I can't find a program with synaptic or aptitude or apt-get and have to download it as a tar.gz or tar.bz2, I just do not install it, because I cannot understand how it is done. Can somebody help me, I'll appreciate :)

---

### Post by Favux on 2009-09-10
Hi minimala,

DoctorMo has an amd64 deb for you in the link he gives in the post above yours.  When you are at the launchpad site you'll see "xserver-xorg-input-wizardpen - 0.7.1-0ubuntu3" under Source at the bottom left.  Click on the little triangle to the left of it and the deb packages and source file will appear.  Download the amd64 deb.

If you want to compile the source see:  [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)  Option 2.  Substitute in the numbers of the source code package you have into the commands.

I hope this helps.

---

### Post by Oriana on 2009-09-10
[http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en](http://www.jpbouza.com.ar/ESP2/472/genius-tablet-jaunty-and-blender/id/en)

Try this site - not only does it give you a precompiled driver, it walks you through creating the fdi file. I was having trouble compiling, so that was handy.

Use Terminal:
gksudo gedit /etc/hal/fdi/policy/10-aiptek.fdi
to create the .fdi file.

Rebooting now, so I'll check back in if successful.

EDIT: Mrph, so much for that. It works for some people. Referring back to the original ubuntuhelp page. Still, precompiled truly was helpful.

---

### Post by negora on 2009-10-02
Hello to you all:

I just wanted to share my very recent experience configuring my pen tablet in order to help others who suffer from the same problems which I suffered from. I use Ubuntu v. 9.04 (Jaunty Jackalope) and own a model of tablet called "Manhattan Graphic Tablet USB 8 x 6 Mouse & Pen", like the one shown below:

[IMG]http://images.smarter.com/180x180x15/2/01/1555901.jpg[/IMG]

My device is identified by "lsusb" as:

> ID 5543:0005 UC-Logic Technology Corp. Genius MousePen 8x6 Tablet

Because of a failure of my Windows XP installation some days ago, I decided to move to Ubuntu definitively. However I had been preparing in the background my ideal Ubuntu environment for 3-4 years, since earlier versions. If my memory serves me right, my tablet worked "out of the box" with one of that versions (not calibrated, right). But it didn't when I just installed 9.04. Maybe I remember wrong, but...

Anyway, let's focus on the important matter: Making the tablet work on 9.04. The first helpful information which I found on Google came from the documents of the Ubuntu Community Documentation. As it stated, I installed a package called:

> GeniusMousePen-Driver_0.7.0_i386.deb

The pointer moved OK and it worked even without restarting Xorg. Problem? It didn't covered all the area of my tablet (I still didn't know about HAL, FDIs and that stuff). Since I was used to play with the "/etc/X11/xorg.conf" file in past versions of Xorg, I tried to set a new device into it and put several options related to the working area. It didn't work (obviously).

After this semi-success, I started reading lots of (more confusing) stuff on the Internet and chose to look for "wizardpen" drivers, compile them and see what happened. I think that I compiled 3:

> 
wizardpen-0.5.tgz
wizardpen-0.6.tgz
wizardpen-0.7.0-alpha2.tgz


Everything was set properly. However the tablet seemed not to work. I discovered just by chance that it did really, but in a weird way: I had to press the tip of the pen to move the cursor and it only worked in the most left side of the tablet. I tested other 2 pre-compiled packages and the result was identical:

> 
wizardpen_0.7.0-alpha2_i386.deb
xserver-xorg-input-wizardpen.deb (from DoctorMo)


After editing the file "xorg.conf" several times and getting desperate, I read about the interaction of the HAL with FDI files in this thread (I had no idea of this). Again, I decided to play with them and the drivers which I had compiled, restoring the "xorg.conf" file to its original state. No success. Same weird behaviour.

Since I've several USB devices plugged, just to prevent, I removed some, moved others, plugged and unplugged an external USB HUB, copied and pasted different FDI configurations from the Internet... A big mess! But no result :( .

Today at noon I've stopped every test and taken a time to think carefully: "Only the first driver from that DEB package seemed to work, but not calibrated. Let's re-install it and try to calibrate it by hand, searching and editing the corresponding FDI which it includes by default instead of adding one bymyself". This FDI file was located at:

> /etc/hal/fdi/policy/99-x11-wizardpen.fdi

After another "bunch" of crazy tests and discoveries, I got success, coming to some interesting conclusions (some of them already stated by other users):

[LIST=1]
[*] Only the driver in **GeniusMousePen-Driver_0.7.0_i386.deb** worked for me.

[*] The edition of **/etc/X11/xorg.conf has no effect.**

[*] Instead of adding an arbitrary FDI file, it's better to **check if there's already another FDI** which might overwrite our own calibration (it happened to me). Possible locations:

[LIST]
[*]/etc/hal/fdi/
[*]/usr/share/hal/fdi/
[/LIST]


[*] **Connect the pen tablet directly to one of the main-board connectors.** I was using a WiFi device in the same HUB (model "D-Link System DWA-140 802.11n Adapter [ralink rt2870]") and it prevented the tablet to work OK.

[*] **Be extra-careful about copying and pasting FDI configurations from websites.** Try to re-write them by hand or examine if an invisible Unicode character exist. This simple and absurd thing made me waste hours (when you're in a hurry you forget basic things like this).

[/LIST]

I tend to be a jinx and this is the proof: All these variables came together.

Salutes and apologizes for such a long and boring message.


PD: Ops, I forgot to show my FDI configuration. I had to calibrate this by hand, as I said, because the program "wizardpen-calibrate" didn't work for me either. That's why the figures are so rounded. By the way, being it an UTF-8 file I don't understand why we're forced to put that it uses a ISO-8859-1 encoding. Anyway, here it is:

> 
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
	<device>
		<match key="info.product" contains="UC-LOGIC Tablet WP8060U">
			<merge key="input.x11_driver" type="string">wizardpen</merge>
			<merge key="input.product" type="string">stylus</merge>
			<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
			<merge key="input.x11_options.TopX" type="string">2400</merge>
			<merge key="input.x11_options.TopY" type="string">3000</merge>
			<merge key="input.x11_options.BottomX" type="string">31150</merge>
			<merge key="input.x11_options.BottomY" type="string">30350</merge>
			<merge key="input.x11_options.MaxX" type="string">31150</merge>
			<merge key="input.x11_options.MaxY" type="string">30350</merge>
		</match>
	</device>
</deviceinfo>


---

### Post by dylbud on 2009-10-09
There is now a .deb package available on the ubuntu tablet help page here:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

The .deb is designed and tested for 9.10 Karmic Koala. I went ahead and upgraded to the beta version of Koala, and then installed the .deb package. A couple of clicks, a reboot, and voila! my mousepen is working!

But...when using brushes in GIMP, the tablet doesn't seem to be detecting changes in pressure -- which it does do on a windows machine. If I could figure the pressure issue out, my satisfaction would be complete!

---

### Post by negora on 2009-10-09
**dylbud:** I forgot to mention that I suffered from the same problem in v. 9.04 Jaunty Jackalope. Try to "play" with the GIMP option:

> Edit > Preferences > Input Devices > Configure Extended Input Devices... 

Once I opened that menu, I remember that I chose my table in the Device list and then Window or Screen in the Mode list. And voilá: The pressure of the pen started to being recognized (very well by the way :) ). The only problem was that I wasn't able to paint with the mouse any more (it's like if its pressure had set to 0).

I've never tried GIMP in depth so I'm sorry that I can't guide you better. I still don't know what every option means.

---

### Post by dylbud on 2009-10-10
Thanks, negora!!  That worked!  Pressure sensitivity is on. And by the way, nice touch with the acute accent mark on your voila!

---

### Post by BCtom on 2009-10-10
I just wanted to add that my tablet works, with all the settings intact from Jaunty, after upgrading to the Bata-test version of Koala too. I think wizardpen is relatively bug free, even with the GIMP in 9.10, but I have noticed intermittent freezing that lasts for five to ten seconds though--but I can deal with that--it is a pre-release.

I haven't tried a clean install yet with my tablet in 9.10 though?

---

### Post by negora on 2009-10-11
By the way, Does anyone know how to invert the function of the pen buttons. I've tried to apply this configuration in the corresponding FDI file:

> <merge key="input.x11_options.ButtonMapping" type="string">1 3 2</merge>

It hasn't worked.

PS 1: Finally it has been SOLVED using the "xinput" application, as stated in [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) . I didn't want to run one more program in the background, but HAL seems to ignore the button mapping from the FDI file. I've used the command:

> xinput set-button-map "UC-LOGIC Tablet WP8060U" 1 3 2


PS 2: I thought that "xinput" was another program running in the background. But after reading its manual I guess that's just a program which modifies a concrete X11 configuration file.

---

### Post by jhb1608 on 2009-10-19
Will it work in Ubuntu 9.10 also? I have Genius Mousepen too...

---

### Post by negora on 2009-10-19
**jhb1608:** I don't know about other's solutions, but the driver used by me is made for 9.10 instead of 9.04 (the one which I use). So it should work...

---

### Post by jhb1608 on 2009-10-19
> **negora said:**
> **jhb1608:** I don't know about other's solutions, but the driver used by me is made for 9.10 instead of 9.04 (the one which I use). So it should work...

oh yes, what is the link for your driver you made into a link? Thanks!

---

### Post by negora on 2009-10-19
**jhb1608:** No, no, I didn't made any driver. I just mentioned that the one which I'm using is supposed to be made for v. 9.10 but I'm employing it on 9.04. Check the first paragraph on: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) .

The driver is located at: [http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb](http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb) .

---

### Post by jhb1608 on 2009-10-19
> **negora said:**
> **jhb1608:** No, no, I didn't made any driver. I just mentioned that the one which I'm using is supposed to be made for v. 9.10 but I'm employing it on 9.04. Check the first paragraph on: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) .

The driver is located at: [http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb](http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb) .


oh sorry for misunderstanding :).

---

### Post by jhb1608 on 2009-10-19
wow it really works! Thanks for the .deb file! now myl ife is easier, plus it works with pressure, too! :).

Now, I think I need to clean up on my ubuntu programs a bit...

---

### Post by negora on 2009-10-19
**jhb1608:** Don't worry. I just hope that it works for you as it did for me. Good luck! ;)

---

### Post by coCoKNIght on 2009-11-02
Has anybody figured out yet where to tweak eighter the aiptek, wizardpen or wacom drivers in Karmic? Where are the equivalents to the 9.04 .fdi files?

---

### Post by negora on 2009-11-05
**coCoKNIght:** I've upgraded from 9.04 to 9.10 and my tablet, which uses the wizardpen driver, works smoothly. I kept the FDI file in the same place where it was before (just in case).

By the way, I read that version 9.10 was going to use DeviceKit instead of HAL, so I thought that this FDI file was useless... But typing "lshal" it seems to work and list hardware, so I guess that Ubuntu is using an hybrid solution maybe? No idea.

---

### Post by coCoKNIght on 2009-11-05
My tablet identifies as Aiptek so the other drivers won't claim it by default, although it works with all 3 drivers... I don't think the .fdi files do anything anymore because as you said Karmic is using Device-Kit instead of Hal...

---

### Post by mephisto123 on 2009-11-07
I am using Ubuntu 9.10 and tablet Trust TB-6300 (UC-LOGIC Tablet WP8060U).
I have installed the wizardpen driver and created .fdi file.
Restarted PC and my tablet still not working =(

In /var/log/Xorg.0.log I've found the problem:
default driver (evdev) is loaded for the tablet instead of wizardpen one.

The .fdi file is located at /etc/hal/fdi/policy/99-x11-wizardpen.fdi and contains all required lines (I've tried .fdi from  [here](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html) and the one installed with new 9.10 [package](http://www.tecnicoslinux.com.ar/livecd/GeniusMousePen-Driver_0.7.0_i386.deb)). Both of them aint working.

As I understand the problem, HAL doesnt see .fdi file, ignoring it or interpreting it wrong for some reason. Because I dont see any errors or warnings regarding wizardpen driver in Xorg.0.log file (grep wizardpen /var/log/Xorg.0.log gives nothing), instead I just see the line LoadModule "evdev" right before lines about my tablet.

Is there any place where I can find HAL log file or something?
How do I investigate my problem further ?

---

### Post by coCoKNIght on 2009-11-11
mephisto123: The .fdi files still work and are necessary to get any tablet working in Karmic. Are you sure you've followed the steps described at [The Digital Blue Wave]("http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html") to find out the name of your tablet and include it in the .fdi file? The driver will claim control of your tablet only if the name from the .fdi file matches the name with which your tablet identifies itself.

---

### Post by mephisto123 on 2009-11-22
I have triple-checked the names, tried different variants with no effect =(
Only thing what helped me was to put tablet device configuration options to xorg.conf. However, it requires me to relog each time i plug my tablet to the PC.

So I`m still looking for better solution.

---

### Post by negora on 2010-05-04
Ops, I've moved to Ubuntu 10.04, installed the last drivers from the Ubuntu repository (xserver-xorg-input-wizardpen) and my tablet has stopped working again. Well, it works, but once that you do one click, you've to drag the pen over the tablet in order to move the pointer. Horrible, this Ubuntu 10.04 is becoming the release of the "steps-back".

UPDATE: I solved it. Here it's the solution: [https://bugs.launchpad.net/wizardpen/+bug/576610](https://bugs.launchpad.net/wizardpen/+bug/576610) .

---

