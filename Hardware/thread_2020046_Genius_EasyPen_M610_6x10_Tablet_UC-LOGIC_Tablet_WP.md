---
title: "Genius EasyPen M610/ 6x10 Tablet/ UC-LOGIC Tablet WP1700U various problems"
date: 2012-07-07
forum: Hardware
---

### Post by LannaD on 2012-07-07
Hello, everyone. I'm really sorry my first post is a whine about my tablet not working, but I wouldn't be writing this, if I hadn't read similar topics here #-o .

Anyway, this is my problem:

1. Back when I got this tablet, over a year ago, I only had Windows XP installed on my machine, and it worked just fine, all I had to do is install the drivers from the CD I got with the tablet. It was recognized right away, and it was perfectly calibrated.

2. I installed Ubuntu 10.04 Lucid Lynx a few months later, side by side with Windows, on the same partition, and while it did recognize the tablet (as "6x10 Tablet"), the pointer was stuck in the upper left corner. I manually installed "wizardpen" (from source, since it wasn't available from Ubuntu Software Center), and the cursor did move, but the axes were inverted, and only about two lower thirds of the surface were detectable. After some calibration, I managed to get the entire surface to respond, but I rotated the tablet by 180 degrees (physically, on my desk), since I had no idea how to invert the axes.

3. Windows XP crashed a month, or two later, but Ubuntu was still working well. However, once I reinstalled Windows XP, I didn't get the list of operating systems to choose from upon starting my PC, rather XP always started by default. I decided to reinstall Ubuntu, and once I did it, I noticed a horrible decrease in sound quality, and decided to erase PulseAudio (since no amount of tweaking would improve the sound), and install ALSA. After a week enjoying flawless audio, the sound system bleeped at random, and eventually died. I reinstalled Ubuntu alongside Windows XP several times, until my hard drive started looking like a shredded paper (I had about seven partitions, and Windows could only recognize two), and then decided to format it completely.

4. After several attempts to install Windows XP (I had trouble getting it to download updates, so I suppose I caught a virus), I tried to install my tablet, and while the driver setup would finish without reporting errors, upon plugging the tablet in, the driver wouldn't start, and I'd get no notification on the taskbar. I installed Ubuntu, this time on a separate hard drive(not just partition), but this time I couldn't get through the installation. I got to this part:

```
make && sudo make install
```

and I was notified that there was an error (something about versions of a program not matching, version a, and version b, sorry I can't be any more precise, I am not getting any error reports when I repeat the command now, but it still doesn't work). After typing:

```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
```

I got the expected output:

```
/usr/lib/xorg/modules/input/wizardpen_drv.la
```
```
/usr/lib/xorg/modules/input/wizardpen_drv.so
```

but the command to list input devices recognized mt tablet as "UC-LOGIC_Tablet_WP1700U". Calibration worked, and I got very similar values, as the time I successfully installed the tablet. However, "xorg.conf" didn't have an "Input device" section this time(just my graphic card, and my monitor), and I had nowhere to paste these values. Also, I noticed that "70-wizardpen" was located in "/usr/share/X11/xorg.conf.d", while all other input related .conf files, including the wacom tablet driver that came with the distribution, were in "usr/lib/X11/xorg.conf.d".

5. I deleted both Windows XP, and Ubuntu 10, and replaced them with Windows 7, and Ubuntu 12, bu this didn't help at all, in fact, Ubuntu 12 gave me even less freedom to poke around (plus the interface was totally eye-squint inducing), and Windows 7 recognized my tablet as a mouse. So I reinstalled Ubuntu 10.04, and now I'm back to square 4.

I'd like to add that I am using a USB mouse (A4-techOscar X-738K), and that it's working perfectly. I've attached a screenshot of my "dev/input/by-id" directory to this message.


Is there any hope, or did all this reinstalling damage my tablet's firmware, and now I should just get a new one?

---

### Post by Favux on 2012-07-07
Hi LannaD,

Welcome to Ubuntu forums!


Wow, that is quite a story and I'm not sure I followed everything.  I hope you didn't damage anything.

So where are you at?  Win7 and Lucid in dual boot?  Is that right?

Let's get the Product ID (PID) on your tablet so we know for sure what you have.  Enter in a terminal:
```
lsusb
```
What is the output?

---

### Post by LannaD on 2012-07-07
> **Favux said:**
> Hi LannaD,

Welcome to Ubuntu forums!


Wow, that is quite a story and I'm not sure I followed everything.  I hope you didn't damage anything.

So where are you at?  Win7 and Lucid in dual boot?  Is that right?

Let's get the Product ID (PID) on your tablet so we know for sure what you have.  Enter in a terminal:
```
lsusb
```
What is the output?
@Favux: Thanks for replying so quickly. I am currently running both Windows 7, and Ubuntu 10, on separate hard drives. Here is the output (I replaced the USB mouse with a PS2 mouse, but that didn't change a thing)

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 5543:000d UC-Logic Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Also, I tried plugging in a different tablet in both Windows, and Linux (Genius G-Pen 450), and Windows 7 detected it right away (as a single tablet device), while Ubuntu acted the same as it did with M610 (pointer jumping into the corner, and staying there). Also, once I plugged M610 in Windows 7, it was listed three times on the "New Hardware" list(as three separate devices).

---

### Post by Favux on 2012-07-07
Good, from:
```
Bus 002 Device 002: ID 5543:000d UC-Logic Technology Corp. 
```
Vendor ID = 5543 = UC-Logic
Product ID = 000d

Unfortunately I do not recognize the PID and it doesn't seem to be in the list of supported tablets:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

But you say it is over a year old and you did have it working, so that is encouraging.
> Also, I noticed that "70-wizardpen" was located in "/usr/share/X11/xorg.conf.d", while all other input related .conf files, including the wacom tablet driver that came with the distribution, were in "usr/lib/X11/xorg.conf.d".
The first thing you have to know is that a vanilla X Server 1.7 is still using HAL, not xorg.conf.d.  What happened is Debian/Ubuntu were in a hurry to get rid of HAL and go to .conf files in xorg.conf.d so they backported an earlier version of X Server 1.8.  The "X Server 1.7" in Lucid is actually a hybrid.  And that's why it has a weird path.  A normal xorg.conf.d setup should have two xorg.conf.d's:
```
/usr/share/X11/xorg.conf.d
/etc/X11/xorg.conf.d
```
The first one is for the Distro and the second location is for users to add their custom modifications.  But in the Lucid hybrid there is only one location:
```
/usr/lib/X11/xorg.conf.d
```
Actually I'm sort of surprised the 70-wizardpen.conf in /usr/share/X11/xorg.conf.d didn't break your X.

Rather than compiling the driver you should consider DoctorMO's PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)

Did you already recompile the driver?

---

### Post by LannaD on 2012-07-07
> **Favux said:**
> Good, from:
```
Bus 002 Device 002: ID 5543:000d UC-Logic Technology Corp. 
```
Vendor ID = 5543 = UC-Logic
Product ID = 000d

Unfortunately I do not recognize the PID and it doesn't seem to be in the list of supported tablets:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

But you say it is over a year old and you did have it working, so that is encouraging.

The first thing you have to know is that a vanilla X Server 1.7 is still using HAL, not xorg.conf.d.  What happened is Debian/Ubuntu were in a hurry to get rid of HAL and go to .conf files in xorg.conf.d so they backported an earlier version of X Server 1.8.  The "X Server 1.7" in Lucid is actually a hybrid.  And that's why it has a weird path.  A normal xorg.conf.d setup should have two xorg.conf.d's:
```
/usr/share/X11/xorg.conf.d
/etc/X11/xorg.conf.d
```
The first one is for the Distro and the second location is for users to add their custom modifications.  But in the Lucid hybrid there is only one location:
```
/usr/lib/X11/xorg.conf.d
```
Actually I'm sort of surprised the 70-wizardpen.conf in /usr/share/X11/xorg.conf.d didn't break your X.

Rather than compiling the driver you should consider DoctorMO's PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)

Did you already recompile the driver?
Okay, I managed to set up DoctorMo's PPA, and I used the first method to set up my tablet(from [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) ). What should I try next?

---

### Post by Favux on 2012-07-07
So the .conf file template was?
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/___COPY HERE___"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/___COPY HERE TOO___"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver ""
EndSection
```
Post what you're using and also the results of:
```
xinput list
```

---

### Post by LannaD on 2012-07-08
> **Favux said:**
> So the .conf file template was?
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/___COPY HERE___"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/___COPY HERE TOO___"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop"
   Driver ""
EndSection
```
Post what you're using and also the results of:
```
xinput list
```
```
xiunput list
```
gave me the following output:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP1700U                     id=8    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP1700U                     id=9    [slave  pointer  (2)]
&#9116;   &#8627; A4Tech USB Full Speed                       id=10    [slave  pointer  (2)]
&#9116;   &#8627; A4Tech USB Full Speed                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```

and the conf file looks like this:

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
    Option        "TopX"        "649"
    Option        "TopY"        "18545"
    Option        "BottomX"    "2012"
    Option        "BottomY"    "20058"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
    Option        "TopX"        "649"
    Option        "TopY"        "18545"
    Option        "BottomX"    "2012"
    Option        "BottomY"    "20058"
EndSection
```

I'm surprised it became responsive, again (about two thirds of the surface, and the axes are inverted, again), but I can't seem to calibrate it from the .conf file (I used the same values from the time it last worked). Also, now that I've installed the driver from a PPA, where can I find the "calibrate" directory?

Thank you so much for your time.

---

### Post by Favux on 2012-07-08
First let's try to find out what driver the tablet is actually on.  Run this command in a terminal and post the output:
```
xinput list-props "UC-LOGIC Tablet WP1700U"
```
Another way to figure out what driver it is on is to look in Xorg.0.log in /var/log.

Part of the problem is the the WizardPen driver changes and Martin also changes the package.  Later including udev rules with the package which changes how the .conf file reads.  Don't really have those straight so I try to make the .conf file so I don't have to worry about that stuff.  Let's see how this one works for you.
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "WP1700U"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
#    Option    "TopX"       "649"
#    Option    "TopY"       "18545"
#    Option    "BottomX"    "2012"
#    Option    "BottomY"    "20058"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "WP1700U"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
Also I'd appreciate it if you could tell me what name your model was sold as.  As complete a name as possible.

---

### Post by LannaD on 2012-07-08
> **Favux said:**
> First let's try to find out what driver the tablet is actually on.  Run this command in a terminal and post the output:
```
xinput list-props "UC-LOGIC Tablet WP1700U"
```
Another way to figure out what driver it is on is to look in Xorg.0.log in /var/log.

Part of the problem is the the WizardPen driver changes and Martin also changes the package.  Later including udev rules with the package which changes how the .conf file reads.  Don't really have those straight so I try to make the .conf file so I don't have to worry about that stuff.  Let's see how this one works for you.
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "WP1700U"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
#    Option    "TopX"       "649"
#    Option    "TopY"       "18545"
#    Option    "BottomX"    "2012"
#    Option    "BottomY"    "20058"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "WP1700U"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
Also I'd appreciate it if you could tell me what name your model was sold as.  As complete a name as possible.
Here's the result of

```
xinput list-props "UC-LOGIC Tablet WP1700U"
```

```
Warning: There are multiple devices matching 'UC-LOGIC Tablet WP1700U'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device UC-LOGIC Tablet WP1700U
```

Also, I had to reinstall Ubuntu (I used version 12.04 LTS) since yesterday, since attempting to calibrate the tablet in .conf file resulted in a logout, every time I'd touch the tablet with the pen, and the system wouldn't load after I restarted my PC. The tablet is now recognized, but  it's miscalibrated. Also, the only tablet driver I have installed now (it came with the distribution) is the one for Wacom tablets (usr/share/X11/xorg.conf.d/50-wacom.conf). Is there a way to calibrate it under Ubuntu 12?

Again, thanks for taking the time to help me set this up.

---

### Post by LannaD on 2012-07-08
Okay, I managed to calibrate the tablet by hand (at first I tried to use "Calibrate Touchscreen", but I would only get a small part of the tablet's surface i the middle), using this command ```
xinput set-prop 8 "Evdev Axis Calibration" 40000 0 42000 20000
```, and a lot of trial and error.

I apologize for wasting everyone's time, and thanks for the help.

---

### Post by Favux on 2012-07-08
We still need to determine the driver the tablet is on especially given the calibration difficulty you're having.

I thought the tablet might be on the evdev driver (matching the "evdev tablet catchall" snippet probably).  That's why I wanted to work on the wizardpen.conf to get the matching right.  Since you haven't re-installed WizardPen I'm pretty sure that you're on evdev.  It being on evdev would explain what you've been seeing I think.  Also I gather you didn't install the 70-wizardpen.conf I posted?

Sorry it was late.  When you have two entries with the same name you can use the ID number.  We'll have to check both.  Remember ID numbers can change with restarts and hotplugging.  Considering you reinstalled (ouch!) you for sure should rerun **xinput list** to find the current ID numbers.  Then:
```
xinput list-props 8

xinput list-props 9
```
I'm using your old numbers so change them if you need to.  Again you can also check in Xorg.0.log.  Just bring it up in gedit and use find and match to 'tablet' or 'UC-Logic, etc.

---

### Post by LannaD on 2012-07-08
Thanks for being interested in this topic, since the tablet stopped responding completely after I restarted my PC. running "xinput list" tells me that the new IDs are 11, and 12, but the method of calibration that worked before does nothing.

Here's the output of the "xinput list-props 11"

```
Device 'UC-LOGIC Tablet WP1700U':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (251):    1.000000
    Device Accel Velocity Scaling (252):    10.000000
    Device Product ID (238):    21827, 13
    Device Node (239):    "/dev/input/event6"
    Evdev Axis Inversion (253):    0, 0
    Evdev Axes Swap (255):    0
    Axis Labels (256):    "Rel X" (131), "Rel Y" (132), "Rel Vert Wheel" (248), "Rel Misc" (470)
    Button Labels (257):    "Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130)
    Evdev Middle Button Emulation (258):    0
    Evdev Middle Button Timeout (259):    50
    Evdev Third Button Emulation (260):    0
    Evdev Third Button Emulation Timeout (261):    1000
    Evdev Third Button Emulation Button (262):    3
    Evdev Third Button Emulation Threshold (263):    20
    Evdev Wheel Emulation (264):    0
    Evdev Wheel Emulation Axes (265):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (266):    10
    Evdev Wheel Emulation Timeout (267):    200
    Evdev Wheel Emulation Button (268):    4
    Evdev Drag Lock Buttons (269):    0

```and the "xinput list-props 12":

```
Device 'UC-LOGIC Tablet WP1700U':
    Device Enabled (121):    1
    Coordinate Transformation Matrix (123):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (251):    1.000000
    Device Accel Velocity Scaling (252):    10.000000
    Device Product ID (238):    21827, 13
    Device Node (239):    "/dev/input/event5"
    Evdev Axis Inversion (253):    0, 0
    Evdev Axis Calibration (254):    <no items>
    Evdev Axes Swap (255):    0
    Axis Labels (256):    "Abs X" (315), "Abs Y" (316), "Abs Z" (471), "Abs Rotary X" (472), "Abs Pressure" (317)
    Button Labels (257):    "Button Left" (124), "Button Middle" (125), "Button Right" (126), "Button Wheel Up" (127), "Button Wheel Down" (128), "Button Horiz Wheel Left" (129), "Button Horiz Wheel Right" (130), "Button Side" (242), "Button Extra" (243), "Button Forward" (244), "Button Unknown" (241), "Button Unknown" (241), "Button Unknown" (241), "Button Unknown" (241)
    Evdev Middle Button Emulation (258):    0
    Evdev Middle Button Timeout (259):    50
    Evdev Third Button Emulation (260):    0
    Evdev Third Button Emulation Timeout (261):    1000
    Evdev Third Button Emulation Button (262):    3
    Evdev Third Button Emulation Threshold (263):    20
    Evdev Wheel Emulation (264):    0
    Evdev Wheel Emulation Axes (265):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (266):    10
    Evdev Wheel Emulation Timeout (267):    200
    Evdev Wheel Emulation Button (268):    4
    Evdev Drag Lock Buttons (269):    0
```For comparison purposes, I hotplugged the other tablet (Genius G-Pen 450), and it was instantly recognized, and calibrated.

After checking the "Xorg.0.log" file, I found the following lines rather interesting:

Using input driver 'evdev' for 'UC-LOGIC Tablet WP1700U'
[    65.158] (--) evdev: UC-LOGIC Tablet WP1700U: Found relative axes (the tablet doesn't support relative axes)

[    65.158] (II) evdev: UC-LOGIC Tablet WP1700U: Configuring as mouse
[    65.158] (II) evdev: UC-LOGIC Tablet WP1700U: Configuring as keyboard

[    65.182] (II) No input driver specified, ignoring this device.
[    65.182] (II) This device may have been added with another device file.

[    65.185] (--) evdev: UC-LOGIC Tablet WP1700U: Vendor 0x5543 Product 0xd
[    65.185] (--) evdev: UC-LOGIC Tablet WP1700U: Found 10 mouse buttons (WHAT?)
[    65.185] (--) evdev: UC-LOGIC Tablet WP1700U: Found scroll wheel(s) (WHAT?)
[    65.185] (--) evdev: UC-LOGIC Tablet WP1700U: Found relative axes (again, they're not supported by my tablet)

Again, thanks for helping me with this. Setting up this tablet is such a nightmare.

---

### Post by Favux on 2012-07-08
Right.  The tablet is on the evdev driver and it doesn't know how to handle it.  Basically the evdev driver isn't really able to handle UC-Logic tablets until it is version 2.5.99.  Which is the Maverick release because that has evdev 2.6 I think.  Also you need the usb descriptor in the HID part of the kernel to be correct for evdev to work.  Basically what I'm saying amounts to a kernel driver/module for the tablet.

That's what I was trying to tell you when I said I didn't recognize the PID and your tablet didn't appear to be supported.  What you do with a new tablet is run through the steps in "Collecting tablet diagnostics" here on:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  And then submitt the information to [email]DIGmend-devel@lists.sourceforge.net[/email].  We've made it a simple as possible, even including videos on what to do.  Then Nick can fix the descriptor and get a working kernel driver for the tablet.  You test it and if it is good he submits it to the kernel.

But since you said you got it working I'm hoping the WizardPen driver can handle whatever the generic usb HID drivers are doing well enough to get you something in Lucid.  But at this point I'm not sure you were ever on the WizardPen driver.  You may have been on evdev all along.  Although if the wizardpen calibrator worked for you in the initial go around it must have been on WizardPen.

Do you want to install WizardPen and continue trying?  I'm not sure if we should go back to the Lucid PPA or maybe download the 8.1 tar from the Natty part of the PPA and have you compile it.

Are you able to follow what I just said?

---

### Post by LannaD on 2012-07-08
I'm fairly new to Ubuntu, but I think I understood what I need to do.

First of all, I tried to install Wizardpen from the DoctorMo's PPA, but I got this error:

```
E: Unable to locate package xserver-xorg-input-wizardpen
```

Are there perhaps any "remains" of it now on my system I should worry about?

I'll try to "Collecting tablet diagnostics". I'm just surprised that my other tablet got recognized with no problems whatsoever, despite being from the same manufacturer.

---

### Post by LannaD on 2012-07-08
Okay, I tried sending the data to [email]DIGmend-devel@lists.sourceforge.net[/email] from my gmail account, but I didn't work. Excuse my inexperience, but is it even possible to send an e-mail from a regular address to a mailing list?

---

### Post by Favux on 2012-07-08
Do you already have a WizardPen driver installed.  Check in Synaptic Package Manager for **xserver-xorg-input-wizardpen**.

Your Genius G-Pen 450 may just have a better usb descriptor that works with evdev if it isn't on WizardPen.  If on WizardPen the match to the driver may have worked with it.  The manufacturers don't necessarily ship the tablets with the descriptors correct, often they are broken.  They just deal with that in their Windows or OSX driver.  WizardPen supports more tablets than evdev does right now.  WizardPen is a specialist driver so it has a bunch of if/thens and try/excepts and so on to deal with the idiosyncracies of different models.

Evdev is a generalist driver.  To keep the code clean without all the if/thens and so ons so it is maintainable it expects the data coming from the kernel to be correct.  So that is what Nick does.  He fixes the broken usb descriptors in the kernel so they send "correct" data that evdev can handle.  Follow?  That's why the new system of using evdev doesn't support as many models yet.  Nick is sort of alone in fixing the descriptors.

So we may be able to get it working on a WizardPen version.  Or even shoehorn it into evdev.  WizardPen seems more likely to me, but no guarantee either way.

Well Nick says you can.  I've always signed up for the mailing list so I've never tested it.

---

### Post by LannaD on 2012-07-08
Okay, I got the following messages, after starting synaptic:

```
Failed to fetch http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/precise/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
```

I do have some other packages installed, like **xserver-xorg-input-all, ****xserver-xorg-input-wacom, ****xserver-xorg-input-mouse, ****xserver-xorg-input-evdev, ****xserver-xorg-input-vmmouse, ****xserver-xorg-input-geode, and **[B]xserver-xorg-input-synaptics.

[/B]I think I understand that evdev isn't as general as wizardpen, and that it supports only tablets that have their drivers tailor-made.
I signed up for the mailing list, but I still get this error:

```
Technical details of permanent failure:
Google tried to deliver your message, but it was rejected by the  recipient domain. We recommend contacting the other email provider for  further information about the cause of this error. The error that the  other server returned was: 550 550 unknown user (state 13).
```

---

### Post by Favux on 2012-07-08
I'm not sure what you mean by the Synaptic error message.  You have Lucid installed correct?  Because the error message is about Precise.  And the PPA doesn't have a WizardPen driver for Precise.  Or Oneiric for that matter.  So could you maybe clarify for me what's going on.  Did you maybe edit your software sources to add the PPA and try to direct it to a Precise version?

The e-mail message I'm also not sure of.  Maybe you just didn't fill out the your e-mail address correctly?  Did you try some of the extra options there or just left it to default?

---

### Post by LannaD on 2012-07-08
I now have Ubuntu 12.04 LTS, codename: "precise", now (Ubuntu 10.04 I used to have was Lucid). I suppose I won't be getting wizardpen for this version, after all, since the repository doesn't offer one. I tried adding the deb, and deb-src manually, but got a parsing error, and had to delete them.

As for the e-mail, the developers blog seems to be down for he last 8 hours, so maybe that's the problem? I didn't tweak anything, just sent the e-mail, like I always do.

---

### Post by Favux on 2012-07-08
OK, now I gotcha.  On Precise.  Right no more WizardPen and you are suppose to use evdev.  So we really need to get the descriptor fixed.  We can try working with what is there and see if that gets us anywhere if you would like to.

Actually I haven't tried compiling WizardPen on Precise yet to find out what if anything is broken.  There is a remote possibility if it was really simple I could figure it out.

The blog is another thing.  SourceForge had its hosted apps go down about 2 months ago.  They brought most of them back but Wordpress (the blog) wasn't one of them.  Now they've announced they are dropping the hosted apps in September.  To hard to maintain apparently.  This is a crying shame because we just finished getting the mediawiki for DIGI*mend* up!

So in addition to migrating Wordpress to our own implementation we'll have to do the same thing for the MediaWiki.  And I'm already suppose to be looking into migrating the MediaWiki for the LWP.  How do I get myself talked into these things?

I just got e-mail from Nick "through" the devel list this morning.  Although I am probably a cc so it may actually be direct.  But I'd think Nick would have noticed and commented on a bounceback.  So I don't know what to tell you.  It could be some sort of IP or POP setting you need to make or change but I'm no expert on that.  It just worked for me, like you expected.  Frustrating, I know.  Did you try user instead?

---

### Post by Favux on 2012-07-08
We need to find the tablet's coordinates by using xinput_calibrator.  In the Software Center enter Calibrate Touchscreen to find it and install it.  In the meantime I took a wild guess from what you've already posted.

Sometimes evdev just needs the coordinates and then it can handle things.  So that's what we're checking.

First check if you have an /etc/X11/xorg.conf.d directory.  If not make it:
```
sudo mkdir /etc/X11/xorg.conf.d
```
Then we'll create a 52-evdev.conf:
```
gksudo gedit /etc/X11/xorg.conf.d/52-evdev.conf
```
Then for the contents copy and paste the following:
```
Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "WP1700U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "0 25000 0 20000"
EndSection
```
Save and restart.  The WP1700U match may not work in which case we'll need to come up with something else.

---

### Post by LannaD on 2012-07-09
Okay, this is getting really ridiculous. This morning, I plugged the tablet, and it worked (it was miscalibrated, but all I had to do is apply the

```
xinput set-prop 9 "Evdev Axis Calibration" 40000 0 42000 20000
```

but once I unplugged it, and plugged it back in, it became non-responsive. It is still recognized in the xinput list (under the same id, even), but there doesn't seem to be any pattern in it's recognition.

I'm so sorry to hear about sourcefrge not hosting apps anymore. Does this mean that EVERYTHING they had uploaded so far will be gone?

I tried sending the mail, again, this morning, but I got the exact same error. Yesterday I also sent a message to Nick on his personal address, but got no reply.

---

### Post by Favux on 2012-07-09
No just the hosted apps like the MediaWiki and Wordpress.  The basic stuff like the files and bug reports and so on for project hosting remains.

Nick's been on a "vacation" because he got a bit burnt out.  He's liking it so much he's going to go another week or so.  So response might be slow.  Usually he's pretty fast.  I wish I had a clue to the e-mail problem.  Its just right now I have nothing to post to the lists.  Maybe I should just call it a test post.

I do not see how the coordinates you are running with that xinput command can be valid.  The origin, or 0,0 is the top left of the screen or tablet and that's the min x and min y.  You have your min y at 42000 which is twice as big as your max y of 20000.

---

### Post by LannaD on 2012-07-09
> **Favux said:**
> We need to find the tablet's coordinates by using xinput_calibrator.  In the Software Center enter Calibrate Touchscreen to find it and install it.  In the meantime I took a wild guess from what you've already posted.

Sometimes evdev just needs the coordinates and then it can handle things.  So that's what we're checking.

First check if you have an /etc/X11/xorg.conf.d directory.  If not make it:
```
sudo mkdir /etc/X11/xorg.conf.d
```
Then we'll create a 52-evdev.conf:
```
gksudo gedit /etc/X11/xorg.conf.d/52-evdev.conf
```
Then for the contents copy and paste the following:
```
Section "InputClass"
        Identifier "evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "WP1700U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "0 25000 0 20000"
EndSection
```
Save and restart.  The WP1700U match may not work in which case we'll need to come up with something else.
Okay, I did this, and the result is still the same.

I did discover one thing, though. Most of the time, the tablet seems to be misrecognized as a five button mouse. When I move the pen near the surface, the LED lights on, but the cursor does not move. When I touch the surface area with the tip of the pen, it has the same effect as the "back" button on my mouse, while one of the buttons on the pen (the lower one) acts as a "forward" button, and the third button does nothing. I don't know what made it work half an hour ago, but I bet it has something to do with what I found in the Xorg.0.log.

Also, I tried installing the tablet on Windows 7, but the driver icon doesn't appear when I plug it in, and the behavior is similar to the one I experienced on Ubuntu 10 (pointer stuck in the upper left corner). EasyPen M610 is using a driver from UC-Logic's site directly, while the other tablet (G-Pen 450) seems to be using some Genius original drivers, and it must be why it's recognized.

---

### Post by Favux on 2012-07-09
Alright, you want to check for the match in Xorg.0.log.  Using find do you see the human readable text from our new snippet:  evdev tablet options

That should be the last snippet identifier before it starts trying to set up the tablet.  That whole section is what we want to look at.

---

### Post by LannaD on 2012-07-09
> **Favux said:**
> No just the hosted apps like the MediaWiki and Wordpress.  The basic stuff like the files and bug reports and so on for project hosting remains.

Nick's been on a "vacation" because he got a bit burnt out.  He's liking it so much he's going to go another week or so.  So response might be slow.  Usually he's pretty fast.  I wish I had a clue to the e-mail problem.  Its just right now I have nothing to post to the lists.  Maybe I should just call it a test post.

I do not see how the coordinates you are running with that xinput command can be valid.  The origin, or 0,0 is the top left of the screen or tablet and that's the min x and min y.  You have your min y at 42000 which is twice as big as your max y of 20000.

Bummer about the Wiki. It looks rather cool.

I attached the raw data in a zip archive, so, if you're not too busy, could you try sending it to the developers mailing list?

I have no idea how I ended with such ridiculous numbers. Sticking the upper left corner on (0, 0) was a huge mismatch, and it inverted the  axes.

---

### Post by Favux on 2012-07-09
Assuming you see we are getting a match in Xorg.0.log lets try this then:
```
Section "InputClass"
        Identifier "Custom evdev tablet options"
#	MatchIsTablet "on"
        MatchProduct "WP1700U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
	Option "SwapAxes" "on"
        Option "Calibration" "0 25000 0 20000"
EndSection
```
I'm hoping by now they have fixed the swap axes for evdev.  Ubuntu broke it a while ago.  I guess for Natty and we had to scramble to replace swap axes with CTM (coordinate transform matrix) for our little Magick Rotation applet.

Sure I'll try to send that for you.  PM me your e-mail address so I can cc you when I send and then you should see any reply and be able to join in.

---

### Post by LannaD on 2012-07-09
> **LannaD said:**
> Okay, I did this, and the result is still the same.

I did discover one thing, though. Most of the time, the tablet seems to be misrecognized as a five button mouse. When I move the pen near the surface, the LED lights on, but the cursor does not move. When I touch the surface area with the tip of the pen, it has the same effect as the "back" button on my mouse, while one of the buttons on the pen (the lower one) acts as a "forward" button, and the third button does nothing. I don't know what made it work half an hour ago, but I bet it has something to do with what I found in the Xorg.0.log.

Also, I tried installing the tablet on Windows 7, but the driver icon doesn't appear when I plug it in, and the behavior is similar to the one I experienced on Ubuntu 10 (pointer stuck in the upper left corner). EasyPen M610 is using a driver from UC-Logic's site directly, while the other tablet (G-Pen 450) seems to be using some Genius original drivers, and it must be why it's recognized.

Okay, I attached the whole section in a .TXT file, and here are a few lines that got my attention:

[    17.818] (--) evdev: UC-LOGIC Tablet WP1700U: Found 10 mouse buttons (there are 3 on the pen, and four on the tablet itself)
[    17.818] (--) evdev: UC-LOGIC Tablet WP1700U: Found scroll wheel(s) (no scrollwheels)
[    17.818] (--) evdev: UC-LOGIC Tablet WP1700U: Found relative axes (the tablet only supposrts absolute axes)
[    17.818] (--) evdev: UC-LOGIC Tablet WP1700U: Found x and y relative axes

---

### Post by Favux on 2012-07-09
Actually I think we are good with the match!  There are two event nodes which is why you are seeing two entries in **xinput list**.  One is the pen and the other the tablet buttons.  For the pen we're seeing both the right identifier and:
```
[    17.819] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP1700U" (type: TABLET, id 8)
```
and for the buttons again the identifier and:
```
[    17.821] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP1700U" (type: KEYBOARD, id 9)
```
Do the ID numbers match to what you are currently getting with **xinput list**?

---

### Post by Favux on 2012-07-09
The e-mail went through to devel.  So since it is morning in Finland there's a chance Nick might see it shortly.  :)

Don't know what to tell you about your problem with the list.

---

### Post by LannaD on 2012-07-09
UC-LOGIC Tablet WP1700U                     id=8    [slave  pointer  (2)]
UC-LOGIC Tablet WP1700U                     id=9    [slave  pointer  (2)]

---

### Post by LannaD on 2012-07-09
> **Favux said:**
> The e-mail went through to devel.  So since it is morning in Finland there's a chance Nick might see it shortly.  :)

Don't know what to tell you about your problem with the list.
Thank you so much. I don't want to bug Nick on his vacation, so I'll wait.

---

### Post by Favux on 2012-07-09
Did you get a copy of the e-mail.

Unless you got lucky I don't expect the 4 tablet buttons to work without Nick fixing the descriptor.

Anything going on with the pen?  Have you installed and tried xinput_calibrator yet?

Up past my bedtime again.  Got to sack out.  Good night.

---

### Post by LannaD on 2012-07-09
I did get a copy of the e-mail. Thank you.

I can't remember whether or not the buttons worked before, but I never used them, anyway.

I did, but the device is still being misrecognized, and the pointer refuses to move.

Good night, then.

---

### Post by Favux on 2012-07-09
I don't believe the buttons ever worked with the WizardPen driver.  That's because the tablets with currently working buttons use the evdev keyboard snippet.

Actually we do not want to match the button event node in our custom .conf.  Although the names are the same in **xinput list** if things aren't too broken one should be identifying itself as a tablet and the other as a keyboard.  Since we only want to apply the coordinates to the tablet remove the comment from in front of MatchIsTablet and see if the match is maintained in Xorg.0.log for the tablet:
```
Section "InputClass"
        Identifier "Custom evdev tablet options"
	MatchIsTablet "on"
        MatchProduct "WP1700U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
	Option "SwapAxes" "on"
        Option "Calibration" "0 25000 0 20000"
EndSection
```
That should leave the keyboard event untouched and still with its original match and setup by the 10-evdev.conf keyboard snippet.  See if that gets us anything.

So are you able to get any coordinates from xinput_calibrator?  You maybe would want to comment out the calibration line in the custom .conf when using it.  Not sure.  You know with your min y being twice the size of the max y it seems like you maybe came up with a new way to swap axes.  :)

---

### Post by LannaD on 2012-07-09
I can't even use xinput_calibrator, since the cursor refuses to move (the tablet is, again, recognized as a 10 button mouse). Using the calibration values you wrote makes my cursor move up and down the left edge of the screen when I move my pen left, or right.

One time after a restart, I had to use the "Swap Axes" feature, because my tablet got them in reverse, but after another restart they were back to (almost) normal. Also, I checked Windows forums, and it seems that this tablet is causing Windows users a headache, too, and that their drivers are quite lousy.

---

### Post by Favux on 2012-07-09
> Also, I checked Windows forums, and it seems that this tablet is causing Windows users a headache, too, and that their drivers are quite lousy.
That's interesting.  Really sounds like the descriptors might need fixing.


I had a few minutes so I tried to compile WizardPen in Precise to give us an alternative.  I thought I had it but wizardpen_drv.so apparently didn't build, even though the output claims it did.  There was an error message just before that seemed to be more of a warning.  So not sure what's going on.  Anyway here's what I have so far.

Download and extract xserver-xorg-input-wizardpen_0.8.1-0ubuntu3.tar.gz from the Natty xserver-xorg-input-wizardpen-0.8.1-0ubuntu3 at Martin Owen's (DoctorMO) PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages](https://launchpad.net/~doctormo/+archive/xorg-wizardpen/+packages)
```
cd Desktop

sudo apt-get install xutils-dev xutils libx11-dev libxext-dev build-essential xautomation xinput xserver-xorg-dev autoconf libtool pkg-config

cd xserver-xorg-input-wizardpen-0.8.1

aclocal && automake && autoconf

./configure --prefix=/usr

make

sudo make install
```
I'd hold off on the 'sudo make install' until we put some thought into it.  Although the only thing to be concerned with should just be the 70-wizardpen.conf and what kind of match we want to set up.  I suppose MatchIsTablet and could then just comment out the match in 52-evdev.conf.  That may give us an alternative if we can't get anything out of evdev.  Although I have no idea if WizardPen works in Precise even though it maybe compiled.

---

### Post by LannaD on 2012-07-09
I got the following output:

```
The program 'aclocal' can be found in the following packages:
 * automake
 * automake1.10
 * automake1.4
 * automake1.9
 * automake1.7
Try: sudo apt-get install <selected package>

```

after typing:

```
aclocal && automake && autoconf
```

---

### Post by Favux on 2012-07-09
> I can't even use xinput_calibrator, since the cursor refuses to move (the tablet is, again, recognized as a 10 button mouse).
Does it say the tablet is in Absolute mode, i.e. it is using Absolute axes?  That's the main thing we care about.
> Using the calibration values you wrote makes my cursor move up and down the left edge of the screen when I move my pen left, or right.

So it is actually "working" on evdev and the problem does appear to be evdev doesn't have the coordinates for it.  What happens if you comment out the axes swap option we put in?


Edit:  I think that means we need to add **autoconf** to the dependency line.  I'll do that.

---

### Post by LannaD on 2012-07-09
I installed automake1.10, and got this :

```
configure.ac:130: required file `./config.guess' not found
configure.ac:130:   `automake --add-missing' can install `config.guess'
configure.ac:130: required file `./config.sub' not found
configure.ac:130:   `automake --add-missing' can install `config.sub'
src/Makefile.am:27: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:27:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/Makefile.am:27:   to `configure.ac' and run `aclocal' and `autoconf' again.
src/Makefile.am:27:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
src/Makefile.am:27:   its definition is in aclocal's search path.
```

---

### Post by Favux on 2012-07-09
Hmm.  I thought automake was included in build-essential.  Let's try adding **libtool** and **pkg-config**.  Maybe we need to add **automake** too.

---

### Post by LannaD on 2012-07-09
> **Favux said:**
> Hmm.  I thought automake was included in build-essential.  Let's try adding **libtool** and **pkg-config**.  Maybe we need to add **automake** too.
Sorry I didn't respond. I was digging around geniusnet.com for info about my tablet, M610X, and M610XA. I am trying to download the divers for the newer versions to see if they'll work on Windows (I want to be sure my tablet isn't at fault).

So, where do I type those lines?

---

### Post by Favux on 2012-07-09
I added them to the dependency line or just run:
```
sudo apt-get libtool pkg-config
```

---

### Post by LannaD on 2012-07-09
Something completely crazy happened. The tablet started working perfectly on Ubuntu, after I installed M610X drivers on Windows  (it doesn't work on Windows though). I fear that once I shut my PC down, it will stop working, again. I'll let you know how it went in the morning.

Thanks.

---

### Post by LannaD on 2012-07-09
I just tried drawing a few lines in GIMP, experienced a lot of lag (nothing like before), and GIMP recognized the tablet as having over 240 buttons. Ugh!

---

### Post by Favux on 2012-07-09
So it actually drew?  Wow!  I'm thinking it must be on evdev and so that is encouraging.  Tells us we're looking in the right direction.  Did you change the custom evdev.conf?  Maybe commented out the swap axes?

As long as we can get a line I'm not too worried about the other stuff we see like button numbers.  Xinput list-props etc. always report more buttons than are there because the code is set up to reserve a certain button number even if you actually don't have close to that.  Like 32 when you have 3.

I found the lines per inch and that seems to check with other "similar" models so we should have the basic coordinates plus the pressure levels.
LPI = 4000
PL = 1024 (so 0-1023)

Now assuming it is really 4000 and not 4096 or whatever:
X = 4000 x 10 inches = 40000
Y = 4000 x 6 inches = 24000

So our coordinate line should be something close to:
```
Option "Calibration" "0 40000 0 24000"
```

Now if the swap axes option isn't working, although maybe it is now from what you said, we have a few combinations to look at.

min x or y swapped with max x or max y
So that would look something like your coordinates from before if we just do the y case:
```
Option "Calibration" "0 40000 24000 0"
```
and the same thing with x could be tried or both together.

Then the other would to be to actually swap the axes:
```
Option "Calibration" "0 24000 0 40000"
```
And then again you have to consider the min and max swap permutations, e.g.:
```
Option "Calibration" "0 24000 40000 0"
```
Hopefully you won't need to check that out.  But a possible approach.

---

### Post by LannaD on 2012-07-09
All this made think that there's a dependence between Windows drivers, and Linux drivers.

Calibrated tablet has the following values: 40000, 0, 42000, 20000 , swap and invert are both zero, and all axes are absolute. But, as I said, it may change tomorrow. Pressure sensitivity is also well calibrated, but I am still experiencing a lag.

---

### Post by Favux on 2012-07-09
Outstanding!  :D

I assume from "Calibrated tablet" you were able to run xinput_calibrator.  If so it did give you close to the swapped min x and y and max x and y scenario!

So instead of:
```
Option "Calibration" "0 40000 0 24000"
```
you get:
```
Option "Calibration" "40000, 0, 42000, 20000"
```
Which amounts to:
```
Option "Calibration" "40000, 0, 22000, 0"
```
with an offset of 20000 because you've rotated around the z-azis pointing vertically from the origin at 0,0.  Take a sheet of paper and set it so it is laying horizontally so it looks like the tablet.  Then rotate it around the z-axis, the top left corner, to see what I mean.  That's from the CTM or coordinate transformation matrix math, see:  [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)  Not clear where the missing 2000 went.  Maybe the tablet doesn't measure quite 6 inches along the Y axis?

So that clearly needs to be fixed.

---

### Post by Favux on 2012-07-09
Hi LannaD,

I really want to thank you.  I'm learning a lot.  Hopefully I'll have some material to start a troubleshooting page on the DIGI*mend* wiki.

So it isn't out of simple curiousity I'm asking you to test the following:
```
Section "InputClass"
        Identifier "Custom evdev tablet options"
	MatchIsTablet "on"
        MatchProduct "WP1700U"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "Calibration" "0 40000 0 22000"
	Option "InvertX" "1"
	Option "InvertY" "1"
EndSection
```
If the axes inversion works I want to see if it also automatically handles the offsets correctly.

---

### Post by LannaD on 2012-07-10
Well, I'm glad you're finding this torture session useful;).

Just as I expected,  after I restarted my PC, the tablet was misrecognized, once again, and Ubuntu sees it as a 10 button mouse with relative axes. I typed what you suggested, but it made no difference. I can't seem to figure out what makes it tick. It must the identifier, or something.

---

### Post by Favux on 2012-07-10
Hi LannaD,

Darn.

I think I may have a handle on what's going on.  There are two separate issues.

1)  Coordinates are wrong/axes inverted - I hope I've fixed that with the last 52-evdev.conf I posted.  So if it starts working as a tablet again lets see.

2)  The match seems inconsistent.  One time evdev treats it as a mouse then another as a tablet.  That really doesn't make much sense so what I think what is really going on is the tablet firmware needs to be toggled into a non-standard usb protocol, let's call it the high speed tablet protocol.  In other words the usb protocol in the default state is mouse-like.  It (the tablet) is expecting the kernel driver to toggle it into high speed mode.  When it is in the high speed mode it is recognized as a tablet.  So it wasn't that the Windows software influenced the linux install directly.  It is the Windows driver had toggled the tablet's firmware into high speed mode.  And for whatever reason that was preserved during a restart into linux so that evdev treated it correctly as a tablet.

Anyway that scenario seems consistent with what we are seeing.  So we need Nick to fix the kernel driver because I do not know how to trigger the change in usb protocol.

---

### Post by LannaD on 2012-07-10
At least we have the grip on the problem, now. I'm going shopping for some new hardware, now, so we'll see how my tablet will react to a new motherboard.

---

### Post by LannaD on 2012-07-11
Okay, I'm back!

Yesterday I replaced most of my PC's innards (motherboard, graphic card, memory, and processor), and tried to install Windows 7-x64 and Ubuntu-32. Sadly, I can't seem to get them to work well together, but I'm not giving up.

Anyway, here's what happened with the tablet. On Windows, it just wouldn't move, no matter which drivers I installed (Windows Update, or UC-LOGIC 's drivers). On Ubuntu, however, I had a pleasant surprise. Every time I'd start Ubuntu, the tablet would be recognized as a tablet, but it's also badly miscalibrated (axes are inverted, and only 2/3 of the surface are usable).

Apparently, the tablet is at fault. All that tampering I did with various drivers made it unrecognizable for Windows, where it is recognized as three devices (a "USB composite input device",and two "USB input device"s). The other tablet (G-pen 450) is recognized as a single device, and by it's factory name (UC-LOGIC WP5540), and it works with both Windows' tablet drivers, and UC-LOGIC drivers.

I did absolutely nothing after installing Ubuntu, just let it install updates, and (unsuccessfully) tried to install cinnamon. I did have to restart my PC manually after Ubuntu was installed, since it froze, but hopefully, that's not what did the trick.

I am writing this from Chromium, which I had to install because every time I tried right clicking in Mozilla, it would froze.

---

### Post by LannaD on 2012-07-11
And these are still the proper calibration values:

```
xinput set-prop 8 "Evdev Axis Calibration" 40000 0 42000 20000
```

---

### Post by Favux on 2012-07-11
Wow!  Nice job with the hardware.  It's been a while since I built a PC.

I'm not sure why your having a problem dual booting Grub2 and Windows 7.  That hasn't been an issue for me.

I'm also not sure I understand the tablet's problem in Windows.  It sounds like a driver issue.  I'm finding it hard to see how you could have scrambled the tablet itself.  Maybe the firmware is updateable by the Genius drivers?  And your problem is a mismatch between the current Windows Genius driver and the driver version that may have modified the firmware?  That's all I can think of right now anyway.

But good news you have it working in Linux!

I want to try Cinnamon too.  Maybe I'll install the new release of Mint over Maverick.  Keep the previous version of Mint too.  Or is that Mate now?

All in all a kind of weird baffling adventure.

Nick on his latest response on digimend-devel suggested that maybe the idea of using WizardPen as a stop gap is worthwhile.  I'll have to read his post again (hope you got cc'd) because as usual it was pretty dense.  But boy do I learn from him!  :)

---

### Post by LannaD on 2012-07-12
This was my first time.

I installed Windows 7-x64(I had to unplug my second hard drive to do this), and Ubuntu-x86, so I'll try reinstalling Ubuntu-amd64 today, since I had some problems with Mozilla, anyway.

The Windows glitches started after I tried to calibrate my tablet in Ubuntu 10.04 Lucid Lynx, on Wizardpen.

Hopefully, it will also work on Ubuntu 64.

I tried installing cinnamon, but it wouldn't load.

You're telling me. I'm sure all this stress shortened my lifespan:rolleyes:.

I did get the cc, but I still couldn't respond.

---

### Post by LannaD on 2012-07-12
Another update. The tablet only seems to work if it's not unplugged while ubuntu's running. If that happens, the tablet will be misrecognized as a mouse from that point on, even after restarting.

---

