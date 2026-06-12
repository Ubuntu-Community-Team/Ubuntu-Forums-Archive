---
title: "eGalaxTouch Y-Axis Issue"
date: 2011-12-16
forum: Hardware
---

### Post by deaths_eclipse on 2011-12-16
Hi, I'm new to this forum so forgive me if I'm posting this in the wrong section. Just recently I installed (again) Ubuntu on my tablet. I've managed to get multitouch working on my screen (eGalaxTouch Controller) however the Y-axis is inverted. I've tried editing xorg.conf, 99-calibration.conf & some other files that i can't even remember anymore. I would really appreciate the help because I don't want to have to switch back to Windows. Thanks.

(I'm running Ubuntu 11.10 on an Acer Iconia Tab W500)

---

### Post by Favux on 2011-12-16
Hi deaths_eclipse,

Welcome to Ubuntu forums!

It probably depends on which driver you are using.  But this option:
```
Option "InvertY"
```
added to the xorg.conf section or xorg.conf.d .conf file works for at least some drivers.

---

### Post by deaths_eclipse on 2011-12-16
That didn't work. Reinstalled Ubuntu twice. First try i completely messed up the touch driver and something must have gone wrong during the installation because xinput and xorg were throwing all sorts of random errors. Second time, i didn't mess with xinput or xorg but tried poking around the eGalax ini file in /etc and managed to get it fixed. Thanks for the reply anyway. :-D

---

### Post by dlinuxh on 2012-05-09
Hey guys, i am having similar issue with both axis being inverted. My situation is a bit different, i am running mini ISO on ubuntu 11.10. I can't find xorg.conf files... 

here is some info from lsusb and lsmod

xxxxxxx@ubuntu:/dev/input$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13b1:0026 Linksys WUSB54GSC v1 802.11g Adapter [Broadcom 4320 USB]
Bus 002 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen


lsmod
usbhid                 41905  0
hid                    77367  1 usbhid

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12   MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0eef ProdID=0001 Rev= 1.00
S:  Manufacturer=eGalax Inc.
S:  Product=USB TouchController
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=3ms

i found this link on setting up egalax, but afraid to proceed since kernel is 2.6 and i am 3.0 .. any feedback is helpfull... thanks in advance
[http://www.tuxum.org/browser/tuxum/non-free/egalax32](http://www.tuxum.org/browser/tuxum/non-free/egalax32)

---

### Post by Favux on 2012-05-09
Hi dlinuxh,

Let's see if a kernel driver is picking it up.  What is the output of this terminal command?
```
xinput list
```
If so we can use the output to see if it is on a X driver.

---

### Post by dlinuxh on 2012-05-10
> **Favux said:**
> Hi dlinuxh,

Let's see if a kernel driver is picking it up.  What is the output of this terminal command?
```
xinput list
```If so we can use the output to see if it is on a X driver.

Thanks Favux for reply, i am new at this...
this is what I get for xinput list

 xinput list
Unable to connect to X server

i am running 
Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux

after searching more, i found this link pointing to xorg
xxxxxxx@ubuntu:/etc/X11$ ls -ltr
total 64
-rw-r--r-- 1 root root   265 2008-07-01 12:41 Xsession.options
-rw-r--r-- 1 root root 17394 2009-12-03 04:56 rgb.txt
-rwxr-xr-x 1 root root   709 2010-04-01 06:19 Xreset
-rwxr-xr-x 1 root root  3730 2011-08-26 00:13 Xsession
drwxr-xr-x 2 root root  4096 2011-10-05 17:29 xkb
drwxr-xr-x 3 root root  4096 2012-04-03 23:26 fonts
drwxr-xr-x 2 root root  4096 2012-04-03 23:26 Xreset.d
drwxr-xr-x 2 root root  4096 2012-04-03 23:26 Xresources
drwxr-xr-x 2 root root  4096 2012-04-03 23:27 xinit
**lrwxrwxrwx 1 root root    13 2012-04-03 23:27 X -> /usr/bin/Xorg**
drwxr-xr-x 2 root root  4096 2012-04-03 23:27 fluxbox
-rw-r--r-- 1 root root   601 2012-04-03 23:31 Xwrapper.config
drwxr-xr-x 2 root root  4096 2012-04-08 22:46 Xsession.d

then the xinput is located in 
/usr/bin$ xinput list --long
Unable to connect to X server

---

### Post by dlinuxh on 2012-05-10
here is the xorg version
xxxxxxx@ubuntu:/usr/bin$ Xorg -version

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ubuntu 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=883a3506-980e-4925-a2f4-4d95ea6e6eb3 ro splash quiet vt.handoff=7
Build Date: 19 October 2011  05:09:41AM
xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
Current version of pixman: 0.22.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.

---

### Post by Favux on 2012-05-10
I'm a little confused.  With the 3.0 kernel you are on the Ubuntu Oneiric release?  X is the windowing system, you wouldn't have a gui without X.  Or are you using a Ubuntu variant?

Ah just spotted your second post there.  So X server 1.10.4.  So the:
```
xinput list
```
command run in a terminal is really saying?
> Unable to connect to X server

Are you using a regular terminal or ctrl-alt-F2?  The latter takes you out of X.

---

### Post by dlinuxh on 2012-05-10
i am running mini ISO, with no gui... the distro boots up right to full screen browser kiosk mode.... 
yes, i can go to console via ctrl f2, and back to browser

---

### Post by Favux on 2012-05-10
> i am running mini ISO, with no gui... the distro boots up right to full screen browser kiosk mode....
yes, i can go to console via ctrl f2, and back to browser 
Ahh.

So the browser is handling the windowing, i.e. the gui?  It may not even be using X.  From what you are saying it recognizes the eGalax TouchScreen and has some sort of driver handling touch it even if it isn't the evdev X driver.  So is there some setting somewhere in the browser preferences that let's you invert the axes for the touchscreen?

Given I don't know how the browser is handling the gui and the touchscreen can't be much help.  If an option isn't available then that would seem to leave either modifying the code or perhaps the kernel driver code for it.  Is this Chrome?

---

### Post by dlinuxh on 2012-05-11
Favux, 
 sorry for long post.... 
 i am using firefox to start in kiosk... just experimenting with touch  screen. the procedure i followed uses fluxbox for gui i think it is not  x11... it might have come with the mini ISO... i am not expert in it  yet.
 as for the browser it is firefox... 
  here is another screen shot for drivers... maybe it might help...
 
 this link [http://www.tuxum.org/browser/tuxum/non-free/egalax32](http://www.tuxum.org/browser/tuxum/non-free/egalax32)
 talks about how to create a driver for egalax screen, but i don't know if it applies to my kernel... 
 
 xxxxxx@ubuntu:~$  lsusb -v -d 0eef:0001
 
 Bus 002 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               1.10
   bDeviceClass            0 (Defined at Interface level)
   bDeviceSubClass         0
   bDeviceProtocol         0
   bMaxPacketSize0        64
   idVendor           0x0eef D-WAV Scientific Co., Ltd
   idProduct          0x0001 eGalax TouchScreen
   bcdDevice            1.00
   iManufacturer           1 eGalax Inc.
   iProduct                2 USB TouchController
   iSerial                 0
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength           34
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          1 eGalax Inc.
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
           bcdHID               2.10
           bCountryCode            0 Not supported
           bNumDescriptors         1
           bDescriptorType        34 Report
           wDescriptorLength     141
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
         bInterval               3
 Device Status:     0x0000
   (Bus Powered)
 xxxxxxx@ubuntu:~$
 
 i guess these point to drivers?
 xxxxxxx@ubuntu:/proc/bus/input$ cat devices
 I: Bus=0019 Vendor=0000 Product=0001 Version=0000
 N: Name="Power Button"
 P: Phys=PNP0C0C/button/input0
 S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
 U: Uniq=
 H: Handlers=kbd event0
 B: PROP=0
 B: EV=3
 B: KEY=100000 0 0 0
 
 I: Bus=0019 Vendor=0000 Product=0001 Version=0000
 N: Name="Power Button"
 P: Phys=LNXPWRBN/button/input0
 S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
 U: Uniq=
 H: Handlers=kbd event1
 B: PROP=0
 B: EV=3
 B: KEY=100000 0 0 0
 
 I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
 N: Name="AT Translated Set 2 keyboard"
 P: Phys=isa0060/serio0/input0
 S: Sysfs=/devices/platform/i8042/serio0/input/input2
 U: Uniq=
 H: Handlers=sysrq kbd event2
 B: PROP=0
 B: EV=120013
 B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
 B: MSC=10
 B: LED=7
 
 I: Bus=0003 Vendor=0eef Product=0001 Version=0210
 N: Name="eGalax Inc. USB TouchController"
 P: Phys=usb-0000:00:1d.0-1/input0
 S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
 U: Uniq=
 H: Handlers=mouse0 event3 js0
 B: PROP=0
 B: EV=1b
 B: KEY=30000 0 0 0 0 0 0 0 0
 B: ABS=3
 B: MSC=10
 
 I: Bus=0003 Vendor=0eef Product=0001 Version=0210
 N: Name="eGalax Inc. USB TouchController"
 P: Phys=usb-0000:00:1d.0-1/input0
 S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
 U: Uniq=
 H: Handlers=mouse1 event4
 B: PROP=0
 B: EV=1b
 B: KEY=401 0 0 0 0 0 0 0 0 0 0
 B: ABS=3
 B: MSC=10
 
 I: Bus=0011 Vendor=0002 Product=0005 Version=0000
 N: Name="ImPS/2 Generic Wheel Mouse"
 P: Phys=isa0060/serio1/input0
 S: Sysfs=/devices/platform/i8042/serio1/input/input5
 U: Uniq=
 H: Handlers=mouse2 event5
 B: PROP=0
 B: EV=7
 B: KEY=70000 0 0 0 0 0 0 0 0
 B: REL=103
 
 xxxxxx@ubuntu:/proc/bus/input$
 
 is there a way to verify if it is the driver that is bad?
 In my case i can see the axis being inverted... 
 and i am trying to understan if i can callibrate the screen with no X, xorg.conf
 from what i read, the points and axis are in xorg.conf.... right?
 
 thanks for your feedback

---

### Post by Favux on 2012-05-11
The way a usb device works is that there are usually two drivers for it.

There is the kernel driver that converts the raw usb data into data that a X driver can handle.  The X driver then processes it into something the X Server can use to draw on your monitor.

Often touch screens are handled by the HID section of the kernel.  Or if they have their own kernel driver often they need to be black listed in hid-core.c so the generic HID driver doesn't pick them up.

Then many touch screens now days use the evdev X driver.  And the evdev driver is configured by the 10-evdev.conf in /usr/share/X11/xorg.conf.d.

I haven't checked that eGalax link you gave in detail but I presume it is too old.  It probably/may have a kernel driver and a X driver for the eGalax touchscreen.  But if everything in there is at least two years old like it says the question is do they work with the current kernels and X Servers.  Maybe it does, but then what?

The point is apparently you don't have a X Server running and so aren't using a X driver or able to.  At least that is what that error message "unable to connect to X server" seems to be telling us.

Since configuration options I'm familiar with are for X drivers through xorg.conf.d or xorg.conf or xinput I have now clue how to invert axes for you.  At least without a much better understanding of how things work on the setup you are using.

The /proc/bus/input stuff is more the udev description of the devices.  You could use udevadm info to get maybe a better picture of that if you needed to write a udev rule.  The lsusb stuff is the kind of thing you'd want to know to write or modify a usb kernel driver.

---

### Post by dlinuxh on 2012-05-17
Thanks Favux for your feedback. I will keep researching it. I have another question, what package i can use to set up evdev stuff? do you know?

---

### Post by dlinuxh on 2012-06-04
Hi Favux,
I reinstalled the drivers and got same thing of swapped x and y axis.... While reinstalling it , i came accross black lists... have no ide what those are or how to ad it. I will keep on reading...
Do you know where to add the black list info (i hope i phrased the question right)
Here is what i see while installing it
 Note that it is highly recommended that add inbuilt kernel module
    "usbtouchscreen" or "touchkitusb" into blacklist to avoid conflict
   if the touch controller is HID compliant device.Thanks for your time and help...

---

### Post by NigO on 2012-06-12
> **dlinuxh said:**
> Hi Favux,
I reinstalled the drivers and got same thing of swapped x and y axis.... 

Hi, I used the info at [Samiux]("http://samiux.blogspot.co.uk/2011/04/howto-ubuntu-1104-on-gigabyte-touchnote.html") to get mine working (it was auto-detected OK during install, then unresponsive on the installed system), but my X and Y axes are swapped with each other, as they were during the install.

Can I just check if your fault is the same as mine, where touching lower right moves the cursor to upper left and vice versa, but touching upper right or lower left is OK?

If that is the case, then the X and Y co-ordinates have been swapped with each other.  The suggested solutions of InvertX and InvertY won't help, they just change direction of the X or Y axes.

To put it another way, touching 500,0 moves to 0,500 and vice versa, but 0,0 or 500,500 are correct.

If your fault isn't the same, I'll start another thread, if it is the same, please post here when you find a fix! :)

---

### Post by NigO on 2012-06-12
> **NigO said:**
> Hi, I used the info at [Samiux]("http://samiux.blogspot.co.uk/2011/04/howto-ubuntu-1104-on-gigabyte-touchnote.html") to get mine working (it was auto-detected OK during install, then unresponsive on the installed system), but my X and Y axes are swapped with each other, as they were during the install.

Can I just check if your fault is the same as mine, where touching lower right moves the cursor to upper left and vice versa, but touching upper right or lower left is OK?

If that is the case, then the X and Y co-ordinates have been swapped with each other.  The suggested solutions of InvertX and InvertY won't help, they just change direction of the X or Y axes.

To put it another way, touching 500,0 moves to 0,500 and vice versa, but 0,0 or 500,500 are correct.

If your fault isn't the same, I'll start another thread, if it is the same, please post here when you find a fix! :)

OK, that was a bit easier than expected, so here's what worked for me with an eGalax touchscreen on ubuntu 12.04:

```
xinput
```
Lists the available devices which included 2 (?) eGalax touchscreens:
```

eGalax Inc. USB TouchController          id=8    [slave  pointer  (2)]
eGalax Inc. USB TouchController          id=9    [slave  pointer  (2)]

```

As there were two, I had to use their id numbers to change them.  In each case, I did the same command for id 8 and id 9, not sure if id 8 had any effect, behaviour only changed after I changed the second one as well.

```
xinput list-props 8
``` showed the available properties and in my case, I needed to swap everything:
```
xinput set-prop 8 "Evdev Axes Swap" 1
xinput set-prop 9 "Evdev Axes Swap" 1
xinput set-prop 8 "Evdev Axis Inversion" 1 1
xinput set-prop 9 "Evdev Axis Inversion" 1 1

```

To save these settings, according to [the evdev manpage]("http://manpages.ubuntu.com/manpages/precise/man4/evdev.4.html") and [this calibration example]("http://www.thefanclub.co.za/how-to/how-ubuntu-1204-touchscreen-calibration"), I should just have to change my /usr/share/X11/xorg.conf.d/10-evdev.conf file touchscreen section to 
```

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "SwapAxes" "on"
        Option "InvertX" "on"
        Option "InvertY" "on"
EndSection

```

That doesn't work, so reverted that section and made a new one specially for the eGalaxy, which does work

```

Section "InputClass"
        Identifier "eGalaxy touchscreen"
        MatchVendor "eGalax"
        Option "SwapAxes" "on"
        Option "InvertX" "on"
        Option "InvertY" "on"
EndSection

```

Now the touchscreen axes are in the right order and direction.  I'm guessing that MatchIsTouchscreen isn't matching on the eGalaxy, but I could be wrong.

---

### Post by dlinuxh on 2012-07-04
> **NigO said:**
> OK, that was a bit easier than expected, so here's what worked for me with an eGalax touchscreen on ubuntu 12.04:

```
xinput
```Lists the available devices which included 2 (?) eGalax touchscreens:
```

eGalax Inc. USB TouchController          id=8    [slave  pointer  (2)]
eGalax Inc. USB TouchController          id=9    [slave  pointer  (2)]

```As there were two, I had to use their id numbers to change them.  In each case, I did the same command for id 8 and id 9, not sure if id 8 had any effect, behaviour only changed after I changed the second one as well.

```
xinput list-props 8
``` showed the available properties and in my case, I needed to swap everything:
```
xinput set-prop 8 "Evdev Axes Swap" 1
xinput set-prop 9 "Evdev Axes Swap" 1
xinput set-prop 8 "Evdev Axis Inversion" 1 1
xinput set-prop 9 "Evdev Axis Inversion" 1 1

```To save these settings, according to [the evdev manpage]("http://manpages.ubuntu.com/manpages/precise/man4/evdev.4.html") and [this calibration example]("http://www.thefanclub.co.za/how-to/how-ubuntu-1204-touchscreen-calibration"), I should just have to change my /usr/share/X11/xorg.conf.d/10-evdev.conf file touchscreen section to 
```

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "SwapAxes" "on"
        Option "InvertX" "on"
        Option "InvertY" "on"
EndSection

```That doesn't work, so reverted that section and made a new one specially for the eGalaxy, which does work

```

Section "InputClass"
        Identifier "eGalaxy touchscreen"
        MatchVendor "eGalax"
        Option "SwapAxes" "on"
        Option "InvertX" "on"
        Option "InvertY" "on"
EndSection

```Now the touchscreen axes are in the right order and direction.  I'm guessing that MatchIsTouchscreen isn't matching on the eGalaxy, but I could be wrong.


Nigel, 
Thank you for your feedback, I am sorry for late reply. I am using no gui, no desktop distro, Upon typing xinput i get 
[email]dan@ubuntu:/usr/share/X11/xorg.conf[/email].d$ xinput list --short
Unable to connect to X server

I am checking the /usr/share/X11/xorg.conf.d$ ls
[email]dan@ubuntu:/usr/share/X11/xorg.conf[/email].d$ ls
11-evdev-quirks.conf      50-vmmouse.conf           52-egalax.conf
11-evdev-trackpoint.conf  50-wacom.conf
50-synaptics.conf         51-synaptics-quirks.conf

If i cat 52-egalax.conf I get:
[email]dan@ubuntu:/usr/share/X11/xorg.conf[/email].d$ cat 52-egalax.conf | more
Section "InputClass"
        Identifier "eGalax pointer class"
        MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
EndSection

Section "InputClass"
        Identifier "eGalax keyboard class"
        MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "void"
EndSection

Section "InputClass"
        Identifier "eGalax touchpad class"
        MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "void"
EndSection

Section "InputClass"
        Identifier "eGalax tablet class"
        MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "void"
EndSection

Section "InputClass"
        Identifier "eGalax touchscreen class"
        MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc."
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "void"
EndSection

Section "InputClass"
        Identifier "eGalax mouse class"
        MatchProduct "eGalax Inc.|Touchkit|eGalax_eMPIA Technology Inc.|eGalaxTo
uch Virtual Device"
        MatchDevicePath "/dev/input/mouse*"
        Driver "void"
EndSection

Section "InputClass"
        Identifier "eGalax joystick class"
        MatchProduct "eGalax Inc.|Touchkit|eGalaxTouch Virtual Device"
        MatchDevicePath "/dev/input/js*"
        Driver "void"
EndSection

Can I just add these pcs from your post to that file?
Once again, thank you for your time.
den

---

### Post by joaoramos69 on 2012-07-23
Greating this is my first post, also with a problem with a egalaxy touch it works as a mouse, when i toch the screen, it doesnt click im using ubunto 12 lts, Apreciated for the Help

---

### Post by dlinuxh on 2012-08-03
I am still struggling, with this... Should we reopen this thread since we're still having issues.?
:confused::confused::confused::confused::confused::confused::confused:

---

