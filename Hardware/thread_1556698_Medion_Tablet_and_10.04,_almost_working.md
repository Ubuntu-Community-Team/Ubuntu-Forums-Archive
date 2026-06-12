---
title: "Medion Tablet and 10.04, almost working"
date: 2010-08-19
forum: Hardware
---

### Post by _jay_ on 2010-08-19
Between these two threads:[http://ubuntuforums.org/showthread.php?t=1528329](http://ubuntuforums.org/showthread.php?t=1528329)     [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)                             
        I've almost got my medion tablet working- the only issue is that once I use the button suddenly things go weird- it switches functions, the tip stops writing but after clicking random times will work again, etc. I've had the most luck with the first thread, but I've tried seeming every combination of the two as well. I could really use some help, without my tablet my computer is basically a paperweight :) 

      I've tried uninstalling the wacom and aiptek drivers, this didn't help. In the second link I can't seem to bring up the button map dialogue, but at the same time they change while in use, don't know if that will help much. :-/                 

      I've tried both Ubuntu docs and here, to no avail. Granted, some things I just didn't get or didn't work as per the manual, but any help would be greatly appreciated. Thanks

---

### Post by _jay_ on 2010-08-20
When running Mypaint from the terminal this is what I get when clicking the pen's buttons:

```
device change: Core Pointer <enum GDK_SOURCE_MOUSE of type GdkInputSource>
device change: WALTOP International Corp. Slim Tablet <enum GDK_SOURCE_MOUSE of type GdkInputSource>

```same weirdness happens in Gimp. Thanks

* This is when I have the settings from here: [http://ubuntuforums.org/showthread.php?t=1528329](http://ubuntuforums.org/showthread.php?t=1528329)

Also get this:
```
/etc/init.d/rc.local start
Udev did NOT create /dev/tablet-event = tablet NOT present - Tablet-driver disabled

```

---

### Post by AlexDS on 2010-08-21
hey Jay, 
Unfortunately i can't say what it's wrong with the driver.
I'm not a linux or a tablet expert, i only use linux since the beginning of this summer, so i'm practically a noob:D so, i don't know what another advice to give you other than keep looking for answers, as i did, i could say i could manage to make my tablet work by chance, after reading the threads i wrote about in my tutorial. 
So, keep up and hope you'll find you answers that you're seeking ;)

---

### Post by Favux on 2010-08-21
Hi _jay_,

Not sure what I can do for you.

Let's try some diagnostics.  In a terminal enter:
```
xinput --list
```
then
```
dmesg | grep WALTOP
```
then
```
ls -l /dev/input/by-path
```

---

### Post by _jay_ on 2010-08-21
OK, here goes:

```
xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Kingsis Peripherals  Evoluent VerticalMouse 3     id=9    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet      id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Alps Electric M2452 
```

```
dmesg | grep WALTOP
[    3.610525] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.0/input/input4
[    3.610768] generic-usb 0003:172F:0034.0002: input,hidraw1: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:0b.0-7/input0

```


```
ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root 9 2010-08-21 16:48 pci-0000:00:0b.0-usb-0:3.1:1.0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 9 2010-08-21 08:00 pci-0000:00:0b.0-usb-0:4:1.0-event-mouse -> ../event3
lrwxrwxrwx 1 root root 9 2010-08-21 08:00 pci-0000:00:0b.0-usb-0:4:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2010-08-21 08:00 pci-0000:00:0b.0-usb-0:7:1.0-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2010-08-21 08:00 pci-0000:00:0b.0-usb-0:7:1.0-mouse -> ../mouse2

```

Thanks!

---

### Post by Favux on 2010-08-21
Looks good so far.  The tablet is recognized.  Now let's see if the WizarPen driver is attaching to it.  You want the file Xorg.0.log in /var/log.  Right click on it and compress it using Create Archive and then attach it to your next post using Manage Attachmenst below.

---

### Post by _jay_ on 2010-08-21
OK here it is...

---

### Post by Favux on 2010-08-21
The Xorg.0.log looks pretty good.  It looks like the WizardPen driver is picking up the tablet.  What happens if you change the 70-wizardpen.conf to?:
```
Section "InputClass"
	Identifier "wizardpen class"
	MatchIsTablet "on"
#	MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
	MatchProduct "WALTOP"
	MatchDevicePath "/dev/input/event*"
	Driver "wizardpen"
#[CALIBRATION] This data was taken from wizard-calibrate tool( the data from the yellow rectangle)
	Option "TopX" "716"
	Option "TopY" "349"
	Option "BottomX" "19870"
	Option "BottomY" "11631"
#[END CALIBRATION]
EndSection

Section "InputClass"
	Identifier "wizardpen ignore mouse dev"
	MatchIsTablet "on"
#	MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
	MatchProduct "WALTOP"
	MatchDevicePath "/dev/input/mouse*"
	Option "Ignore" "yes"
EndSection
```
Remember to back up your current working 70-wizardpen.conf and be prepared to restore it from the command line in case we break X.

---

### Post by _jay_ on 2010-08-21
Same behavior, the pen's button still acts randomly. Is there any way to tell what it is actually doing when pressed? 
    Just played in Blender a bit, seems as though now I have 2 button functionality, a Right and middle mouse button, where in 9.04 I didn't. The mappings keep changing though, on the fly as it were, sometimes disabling the tip, or left mouse button, which works until I use a pen button, then it all goes screwy.

---

### Post by Favux on 2010-08-21
Well the good news is we solved a couple of problems with the .conf, no need to hardcode path for example.

The actual driver we'd like to use is the wacom one but there is some problem with kernel driver (usb part) for Waltop.  I'm not sure if fixes have been submitted to the kernel or not or when to expect them.  Anyway if the wizardpen driver isn't a perfect fit I guess we shouldn't be too surprised.

Let's see if there is a manual for wizardpen and if so what it says.:
```
man wizardpen
```

For the stylus buttons have you run?:
```
xinput set-button-map "WALTOP International Corp. Slim Tablet" 1 3 2
```
There's probably several ways to look at the button map.  Try the xinput manual:
```
man xinput
```

---

### Post by _jay_ on 2010-08-22
I'm starting to think that this is a bug as well, I think I will look into software-related workarounds instead. 

I'm curious about using the wacom driver- is it supposed to work out of the box or are there config modifications to do as well? I think I will look into that a bit. Thanks for the help, it's really appreciated!

---

### Post by Favux on 2010-08-22
Hi _jay_,

With Lucid the xf86-input-wacom X driver wacom_drv.so is setup to support the Waltop out of the box.  At least I think the 0.10.5 version, which is default for Lucid. is.  Anyway they changed the 10-wacom.conf to comment out the Waltop because they discovered the hid (usb) part of the kernel for Waltop wasn't working correctly.  See the wacom.conf in Section 3 c) in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  There's a brief discussion of Waltop's near the top.

---

### Post by _jay_ on 2010-08-22
That didn't work either- luckily I am able to "borrow" (wink wink) an old graphire from a colleague, although 1/4 the size of my medion it works straight up, even with all the messing around I have done! I guess I will try again when 10.10 comes out, hopefully it is supported a bit better.

---

### Post by aust_paul on 2010-10-17
Hey sorry to jump in on this thread a little late - I hope you got something working for you in the end.

I have the same tablet and I'm using the Apitek driver and Ubuntu 10.04 - all works quite nicely, even pressure. I followed this info to get it going [https://help.ubuntu.com/community/AiptekTablet]("https://help.ubuntu.com/community/AiptekTablet")

The issue that I am having is that the tablet is only picking up the presence of the pen when it is really close ( < 5mm from surface). When I used this in wind0ws with ps/illustrator it allowed for the pen to hover around 2 cms from the surface and it would happily move the cursor around. When it is this close it makes drawing very uncomfortable.

Does anyone know of a way to calibrate this further?

Thanks for your time.

---

### Post by Favux on 2010-10-17
Hi aust_paul,

We figured out how to modify the 70-wizardpen.conf to support the Waltop.  See the Waltop HOW TO:  [http://ubuntuforums.org/showpost.php?p=9966110&postcount=1](http://ubuntuforums.org/showpost.php?p=9966110&postcount=1)  There's some Options described there.  Although you may be describing weak batteries in the stylus.  As far as the Aiptek driver goes we could try to play with the Zthreshold I suppose.

---

