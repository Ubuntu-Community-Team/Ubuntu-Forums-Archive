---
title: "Touchscreen  problems"
date: 2012-05-14
forum: Hardware
---

### Post by kjartani on 2012-05-14
Hello.
Running 10.04lts on Asus eeetop et2203t.
Should this be configured as Tablet, Touchscreen, Mouse, Pointer in X?
It seems that when pressing the touchscreen it is giving click before move. How should I configure this to be shure that the software receives position before the click command.
Is it possible to configure the touchscreen to produce both position and click after a single tap?

Regards
Kjartan Iversen

---

### Post by Favux on 2012-05-14
Hi kjartani,

It sounds like you want it as a touchscreen in Absolute mode.

With Lucid (10.04) that will depend on what X driver it is suppose to be using.  Do you know who makes the resistive 1FGT screen?  Enter the following command:
```
lsusb
```
and post the touch screen line in the output.  That should give you the name and PID to google with.  Also go ahead and post the output of:
```
xinput list
```

The click problem may be due to the kernel driver for it.  Presumambly in the 2.6.32 kernel's HID section.  If so you are likely to see more support in Precise's (12.04) 3.02 kernel for it.  Plus with 12.04 it is probably suppose to be on the evdev X driver which has been improved considerably.

---

### Post by kjartani on 2012-05-15
Hi.
lsusb - Bus 004 Cevice 002: ID 04f2:0860 Chicony Electronics Co

Xinput list - 

&#9121; Virtual core pointer               id=2[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer    id=4[slave  pointer  (2)]
&#9116;   &#8627; Chicony 2.4G Multimedia Wireless Kit id=11[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation id=13[slave  pointer  (2)]
&#9116;   &#8627; IDEACO  IDC 6681             id=8	[slave  pointer  (2)]
&#9116;   &#8627; IDEACO  IDC 6681             id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard            id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard  id=5	[slave  keyboard (3)]
    &#8627; Power Button                 id=6	[slave  keyboard (3)]
    &#8627; Power Button                 id=7	[slave  keyboard (3)]
    &#8627; Chicony 2.4G Multimedia Wireless Kit id=10[slave  keyboard (3)]
    &#8627; ASUS USB2.0 Webcam      id=12	[slave  keyboard (3)]

---

### Post by Favux on 2012-05-15
Hi kjartani,

Thanks for posting the output.  It looks like you have an **IDEACO IDC 6681 touchscreen (1FGT)**.  Please post the ***lsusb*** output for that.  The 'xinput list' output indicates that the IDEACO is supported by your Lucid kernel.

We got lucky and there is a Launchpad bug report on it:  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/378357](https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/378357)  Which has an evtouch .fdi configuration information for it in a patch submitted by Jérôme Pouiller:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="IDEACO"> 
      <match key="info.product" contains="IDC 6681"> 
        <match key="info.capabilities" contains="input.touchpad">
          <merge key="input.x11_driver" type="string">evtouch</merge>
          <merge key="input.x11_options.reportingmode" type="string">raw</merge>
          <merge key="input.x11_options.taptimer" type="string">50</merge>
          <merge key="input.x11_options.longtouchtimer" type="string">30</merge>
          <merge key="input.x11_options.movelimit" type="string">15</merge>
          <merge key="input.x11_options.emulate3buttons" type="string">true</merge>
          <merge key="input.x11_options.emulate3timeout" type="string">50</merge>
          <merge key="input.x11_options.maxx" type="string">1100</merge>
          <merge key="input.x11_options.maxy" type="string">1650</merge>
          <merge key="input.x11_options.minx" type="string">7220</merge>
          <merge key="input.x11_options.miny" type="string">6560</merge>
        </match>
      </match> 
    </match>
  </device>
</deviceinfo>
```
So we have something to work with if need be.

Please post the output of:
```
cat /proc/bus/input/devices
```
We just need the section(s) with the IDEACO IDC 6681 touchscreen.  By the way you can "box" the output by Copying and Pasting it between the code tags which you get from the hash '#' on the upper right.  The quote tags are just to the left of it.

Do you have the evtouch X driver installed?  The package name is **xserver-xorg-input-evtouch**.  According to the bug report you need at least version 0.8.8-0ubuntu4 to get the fix.  Package search for Lucid says the current version is xserver-xorg-input-evtouch 0.8.8-3build1 so you should be good.

If evtouch isn't installed install it and restart.  The touchscreen should be working.  If it isn't or has the same clicking problem then check in /usr/lib/X11/xorg.conf.d for an evtouch .conf file.  It may not come with the package and we'll need to make one.

Evtouch goes away, by Natty(?) and certainly with Precise (12.04), and is replaced with evdev.  So if you upgrade from Lucid and there is a problem this will all be useful information.

---

### Post by kjartani on 2012-05-16
Thanks for putting so much effort in my problem. :o)

output of "lsusb -s 003:002 -v"

> Bus 003 Device 002: ID 1cb6:6681  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1cb6 
  idProduct          0x6681 
  bcdDevice            1.00
  iManufacturer           1 IDEACO 
  iProduct                2 IDC 6681
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
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     254
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
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      71
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
Device Status:     0x0000
  (Bus Powered)


output of "cat /proc/bus/input/devices"

> I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=mouse0 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=1cb6 Product=6681 Version=0110
N: Name="IDEACO  IDC 6681"
P: Phys=usb-0000:00:1a.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input3
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=1b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=100000f
B: MSC=10

I: Bus=0003 Vendor=1cb6 Product=6681 Version=0110
N: Name="IDEACO  IDC 6681"
P: Phys=usb-0000:00:1a.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input4
U: Uniq=
H: Handlers=mouse2 event4 js0 
B: EV=1b
B: KEY=30000 0 0 0 0 0 0 0 0
B: ABS=3
B: MSC=10

I: Bus=0003 Vendor=04f2 Product=0860 Version=0111
N: Name="Chicony 2.4G Multimedia Wireless Kit"
P: Phys=usb-0000:00:1a.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=04f2 Product=0860 Version=0111
N: Name="Chicony 2.4G Multimedia Wireless Kit"
P: Phys=usb-0000:00:1a.1-2/input1
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input6
U: Uniq=
H: Handlers=kbd mouse3 event6 
B: EV=17
B: KEY=70000 0 2000000 387a d801d001 1e0000 0 0 0
B: REL=103
B: MSC=10

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=04fc Product=2080 Version=1515
N: Name="ASUS USB2.0 Webcam"
P: Phys=usb-0000:00:1a.7-3/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0001 Vendor=10ec Product=0887 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card1/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: EV=40001
B: SND=6

regards

Kjartan

---

### Post by kjartani on 2012-05-16
hi again.

When using "xinput list-props 8" I get this output:

> IDEACO  IDC 6681                       	id=8	[slave  pointer  (2)]
	Reporting 6 classes:
		Class originated from: 8
		Buttons supported: 5
		Button labels: Button Left Button Unknown Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 8
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 6946.000000
		Class originated from: 8
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 8191.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 2833.000000
		Class originated from: 8
		Detail for Valuator 2:
		  Label: Abs Z
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 8
		Detail for Valuator 3:
		  Label: Abs Rotary X
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000
		Class originated from: 8
		Detail for Valuator 4:
		  Label: Abs Pressure
		  Range: 0.000000 - 1.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 0.000000


And when using "xinput list-props 9" I get this output:

> IDEACO  IDC 6681                       	id=9	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 9
		Buttons supported: 5
		Button labels: Button Left Button Unknown Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 9
		Detail for Valuator 0:
		  Label: Abs X
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 960.000000
		Class originated from: 9
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: 0.000000 - 65535.000000
		  Resolution: 10000 units/m
		  Mode: absolute
		  Current value: 540.000000

I have checked by disabling id 8 that this is the input "beeing used".

From the output it seems that the touchscreen is acting as a mouse.

I have installed the evtouch driver but when checking Xorg.0.log and lsmod it dont seem that the driver is loaded.

Kjartan

---

### Post by Favux on 2012-05-16
Alright.  At a guess the evdev driver is what is picking the touchscreen up currently.  You can determine that by looking in the Xorg.0.log where the snippet identifier will tell you what snippet is picking it up.  Or use:
```
xinput list-props 8
```
I think you said ID #8 is the one being used.  Remember though the ID# can change, which is why <device name> is preferred if possible.

My guess is currently there is no evtouch.conf in xorg.conf.d to match the touchscreen to the evtouch driver and take it away from evdev.  Can you check in /usr/lib/X11/xorg.conf.d for something like evtouch.conf?  It will have a number in front of it.  If there isn't one we'll have to make one.  Is is sounding like the evtouch package doesn't include one.  It may have a .fdi but that doesn't do you any good.

Or I suppose we could try to make a udev rule that makes the touchscreen show up as IsTouchscreen so the evdev touchscreen snippet picks it.  I doubt that the touchscreen will work with that version of evdev.  I'm not even sure if the Lucid 05-evdev.conf had a touchscreen snippet.  Would have to check that.

---

### Post by kjartani on 2012-05-18
Hello again.
Earlier I have made the xinput list-props for device 8 and 9 but there where nothing there telling evdev driver beeing used.
But examining Xorg.0.log tells that evdev driver is beeing used.

There is no evtouch.conf in xorg.conf.d.
Nor a udev rule for Touchscreen with evtouch driver.

Is it so that either there must be  a "evtouch.conf" in xorg.conf.d or a udev rule for a device to connect to a driver?

I find it confusing with all these elements beeing used with xserver. There must be a sort of proiority so that the use of one option override another. I have tried to find a tutorial about xserver explaning this but with no success.

Kjartan

---

### Post by Favux on 2012-05-18
Evdev does show up in list-props if the device is on it.  I'd need to see the commands you used.

The rule is what runs last controls.  See:  [http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html#contenttoc8](http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html#contenttoc8)  Haven't checked if the ***man xorg.con.d*** can be called in a terminal in Lucid.

In Lucid xorg.conf starts but doesn't run instead it runs xorg.conf.d and then xorg.conf runs.  The .conf files in xorg.conf.d are numbered because the lowest number runs first.

So let's call our first attempt 70-evtouch.conf.  I don't remember the Lucid numbers and haven't checked.  05 for evdev and 20 for wacom?  Anyway 70 should be safe.  It goes in /usr/lib/X11/xorg.conf.d.
```
Section "InputClass"
        Identifier "evtouch class"
#        MatchIsTouchscreen "on"
	MatchProduct "IDEACO"
        MatchDevicePath "/dev/input/event*"
        Driver "evtouch"
EndSection
```
Use:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/70-evtouch.conf
```
Then restart.

The .fdi file gives us some configuration Options we can try adding.  Plus check in a terminal if there is a ***man evtouch***.

---

### Post by kjartani on 2012-05-24
Hello again.
Im smiling the touchscreen is working perfect.
As you proposed i made this evtouch.conf file.
First it did not work but I saw in Xorg.0.log that evdev still was the driver so I disabled touchscreen, tablet, pointer device in evdev.conf file.......
Than it worked so nice, thanks to your help. :)

Regards

Kjartan

---

### Post by Favux on 2012-05-24
Hi Kjartan,

Your welcome.  Glad it is working now!  :)


You likely don't need to disable all 3 of those evdev snippets.  There should be an Identifier for the evdev snippet that is causing the problem in Xorg.0.log and that is the one to disable.  Maybe the evdev touchscreen snippet.  Your custom evtouch snippet should override that anyway.  Not sure why it isn't.

It's just disabling the pointer snippet might affect a mouse.

---

