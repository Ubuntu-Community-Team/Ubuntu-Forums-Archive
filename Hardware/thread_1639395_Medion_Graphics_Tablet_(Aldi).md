---
title: "Medion Graphics Tablet (Aldi)"
date: 2010-12-06
forum: Hardware
---

### Post by TheCosmicFrog on 2010-12-06
Hi everyone,

Like many people, I picked up a Medion MD 86190 Graphics Tablet from Aldi for the bargain price of €24.99. It works fantastically well in Windows 7, just as well as a Wacom Bamboo I've used in the past. Unfortunately it doesn't work out of the box with Linux, so I'm hoping I might be able to get some help here.

According to lsusb, the details are *ID 172f:0037 Waltop International Corp.* I've tried many different methods mentioned online, including from the LinuxWacom project (apparently this device works with the LinuxWacom drivers). I compiled and installed the xf86 drivers from LinuxWacom, but still no luck. The Waltop official Linux drivers are deprecated, as they only work with XOrg 1.7 and under.

The device should pick up input from just "floating" the stylus above the tablet surface, but the mouse does not move. When I press down on the tablet and move the pen, it creates a "drag box" on my desktop, which means that it's picking up the stylus pointer as a left-mouse click. Obviously this means it's still unusable as a graphics tablet.

Here's the output from lsusb:
```

aaron@aaron-notebook:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 172f:0037 Waltop International Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

...and /proc/bus/input/devices
```

aaron@aaron-notebook:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:06/PNP0C09:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input3
U: Uniq=
H: Handlers=sysrq kbd event3 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=000f Version=0000
N: Name="FSPPS/2 Sentelic FingerSensingPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=7
B: KEY=670000 0 0 0 0 0 0 0 0
B: REL=143

I: Bus=0003 Vendor=172f Product=0037 Version=0110
N: Name="         WALTOP             Tablet    "
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input8
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=1f
B: KEY=c03 0 1f0001 0 0 0 0 0 0 0 0
B: REL=143
B: ABS=1fffff00 1000003
B: MSC=10

```

Does anyone have any experience with this tablet, or any other Aiptek/Waltop/Wacom tablets with Linux?

Thanks guys,
Aaron

---

### Post by Favux on 2010-12-06
Hi Aaron,

Please see the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

Hope this helps.

---

### Post by TheCosmicFrog on 2010-12-06
> **Favux said:**
> Hi Aaron,

Please see the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

Hope this helps.

Hi Favux,

I followed the guide but unfortunately my tablet still isn't responding to any input. I went for III Part (a) instead of (b). Should I try Part (b) or does it make any difference?

Also, after rebooting, when I run 
```

$ sh .xsetwacom.sh

```I get the printout:
```

aaron@aaron-notebook:~$ sh .xsetwacom.sh 
Property 'Wacom Sample and Suppress' does not exist on device.
Property 'Wacom Sample and Suppress' does not exist on device.
Unknown parameter name 'ClickForce'.
Property 'Wacom Pressurecurve' does not exist on device.
Property 'Wacom Hover Click' does not exist on device.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  15
  Current serial number in output stream:  15
Property 'Wacom Sample and Suppress' does not exist on device.
Property 'Wacom Sample and Suppress' does not exist on device.
Unknown parameter name 'ClickForce'.
Property 'Wacom Pressurecurve' does not exist on device.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  15
  Current serial number in output stream:  15
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  28 (X_GetDeviceButtonMapping)
  Serial number of failed request:  15
  Current serial number in output stream:  15
Property 'Wacom Enable Touch' does not exist on device.
Property 'Wacom Enable Touch Gesture' does not exist on device.
Property 'Wacom Touch Gesture Parameters' does not exist on device.
Property 'Wacom Touch Gesture Parameters' does not exist on device.
Property 'Wacom Touch Gesture Parameters' does not exist on device.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  28 (X_GetDeviceButtonMapping)
  Serial number of failed request:  15
  Current serial number in output stream:  15


```

---

### Post by Favux on 2010-12-06
Hi Aaron,

Why oh why won't Waltop users post on the HOW TO thread?  I thought maybe I had just made it too good and there weren't any questions.  ;)

Let's stick with the wacom.conf and not try xorg.conf.  It shouldn't make a difference and will let you hot plug your tablet.

Could I see what you're using for your wacom.conf?

You should be using the stylus script on the Waltop HOW TO not the Bamboo one.  You don't have touch or eraser or a pad with the Waltop.

---

### Post by TheCosmicFrog on 2010-12-06
> **Favux said:**
> Hi Aaron,

Why oh why won't Waltop users post on the HOW TO thread?  I thought maybe I had just made it too good and there weren't any questions.  ;)

Let's stick with the wacom.conf and not try xorg.conf.  It shouldn't make a difference and will let you hot plug your tablet.

Could I see what you're using for your wacom.conf?

You should be using the stylus script on the Waltop HOW TO not the Bamboo one.  You don't have touch or eraser or a pad with the Waltop.

Hi again Favux,

I realise what I just did. At the part where it says ""If you do you can use step "II. Install Xorg's 0.10.10+ xf86-input-wacom for Lucid (the X driver)" at the [Bamboo Pen & Touch HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").", I accidentally continued following the Bamboo tutorial instead of going back to the original tutorial. 

ARGH!

Will let you know how the proper instructions go in a few minutes time ;)

---

### Post by TheCosmicFrog on 2010-12-06
Uh-oh. After following those instructions Ubuntu stalls during bootup. Hmmm...:confused:

---

### Post by Favux on 2010-12-06
OK, sounds like something you did broke X.  Hopefully it was the change to the wacom.conf.  Can you get to a command line during boot before it stalls?  You should be able to.  If so enter:
```
sudo mv /usr/share/X11/xorg.conf.d/50-wacom.conf /usr/share/X11/xorg.conf.d/50-wacom.conf.bak
```
That will rename the file to 50-wacom.conf.bak which will disable it.  Then we'll have to figure out what you did.

---

### Post by TheCosmicFrog on 2010-12-06
Ah, it's all good. Got into a root shell during bootup and saw the X error outputs. Left an Option without any arguments in 70-wizardpen.conf - amateur oversight. That said, it is 3am ;)

You mentioned 50-wacom.conf. I guess I'm editing the wrong thing then...

---

### Post by TheCosmicFrog on 2010-12-06
Okay, anyway *cough* moving on...

Here's my 50-wacom.conf file:
```

aaron@aaron-notebook:~$ cat /usr/share/X11/xorg.conf.d/50-wacom.conf 
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
    MatchProduct "Wacom|WALTOP|WACOM"
#    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection


```

---

### Post by Favux on 2010-12-06
Know the feeling well.  Up late last night in a creative reverie myself.  Feeling a little punch drunk today.

Right, we're editing the wacom.conf to get a Waltop match so the wacom driver is used.  At this point the wizardpen.conf is irrelevant to you and you should comment out any match lines for the Waltop you have in it.  Otherwise you're trying to set up the same tablet on two drivers, wth Wacom and the WizardPen.

Edit:  OK, that looks right.  Just be sure to remove or comment out any Waltop stuff from WizardPen.

---

### Post by TheCosmicFrog on 2010-12-06
Argh, what makes things worse is I'm doing exams at the moment. Sleep is probably advisable!

Okay, nothing in the 50-aiptek.conf file relating to the Wacom or Waltop that I can see:

```

Section "InputClass"
        Identifier "pen"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "SendCoreEvents" "true"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection

```

---

### Post by TheCosmicFrog on 2010-12-06
Okay, Waltop stuff commented out of 70-wizardpen.conf:

```

Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    # MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    Option        "Device"    "/dev/input/event5"
    Option        "TopX"        "214"
    Option        "TopY"        "216"
    Option        "BottomX"    "12253"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    # MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection

```

---

### Post by Favux on 2010-12-06
You should be able to reboot safely now.


I remember those exhaustion highs well.

---

### Post by TheCosmicFrog on 2010-12-06
Okay, rebooted!

Outputs from .xsetwacom are still:
```

aaron@aaron-notebook:~$ sh .xsetwacom.sh 
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.
Cannot find device 'WALTOP International Corp. Slim Tablet stylus'.

```

---

### Post by Favux on 2010-12-06
Tablet working thought?  Hopefully it's just a difference in the "Device Names" used in the script.  Enter in a terminal:
```
xinput --list
```
and post the output.

---

### Post by TheCosmicFrog on 2010-12-06
Tablet not working, unfortunately.

Output from xinput --list:
```

aaron@aaron-notebook:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; FSPPS/2 Sentelic FingerSensingPad           id=11    [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet          id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

```

---

### Post by Favux on 2010-12-06
OK, your is reporting differently so for the "Device name" use:
```
"WALTOP Tablet"
```
as in:
```
xsetwacom set "WALTOP Tablet" Suppress "2"  # data trimmed, 1-100
```
instead of:
```
xsetwacom set "WALTOP International Corp. Slim Tablet stylus" Suppress "2"  # data trimmed, 1-100
```
If you're not on the Wacom driver then either the match line isn't good or something went wrong with your xf86-input-wacom install.  Assuming it's the match try:
```
    MatchVendor "WALTOP"

```
instead of:
```
    MatchProduct "Wacom|WALTOP|WACOM"

```
And remember once it starts working to check 'xinput --list' again for the "Device name".

---

### Post by TheCosmicFrog on 2010-12-06
Hmmm... rebooted and still no luck. Here's the current state of wacom.conf and .xsetwacom:

```

aaron@aaron-notebook:~$ cat /usr/share/X11/xorg.conf.d/50-wacom.conf 
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
#    MatchProduct "Wacom|WACOM"
    MatchVendor "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001|N-Trig Pen"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
    Option "Button2" "3"
EndSection

```

```

aaron@aaron-notebook:~$ sh .xsetwacom.sh 
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.
Cannot find device 'WALTOP Tablet'.

```

---

### Post by Favux on 2010-12-06
Probably time to quit and sleep on it.

What we need to do is look at your Xorg.0.log in /var/log with both match lines.  That may also tell us if the Wacom module is around or if you need to reinstall it.

---

### Post by TheCosmicFrog on 2010-12-06
> **Favux said:**
> Probably time to quit and sleep on it.

What we need to do is look at your Xorg.0.log in /var/log with both match lines.  That may also tell us if the Wacom module is around or if you need to reinstall it.

Haha, when someone on the Internet I've never met tells me I should go to bed, you know things are bad :p

Alright, time to let it lie for now. Thanks for all your help so far. I definitely think we've mad a lot of headway and there's probably just something very small I've neglected/misconfigured. 

Good night sir!

---

### Post by TheCosmicFrog on 2010-12-06
Oh! Oh! Oh!

It is working after all!

However, it acts rather strangely. In order to get it to work "floating above" the tablet, I first need to press down so that the tip is depressed quite a bit, then make a quick "flick" with the pen on the tablet surface. Then when I lift it off the tablet the "float" tracking works. If I lift off too much I need to again press down firmly and make a quick movement. Pressing the pen tip against the tablet also registers a left-click, but again I need to depress it quite a lot. 

Any ideas? :)

---

### Post by Favux on 2010-12-07
Good.  I can't tell if that is Wacom driver behavior though or whether the evdev driver has your stylus.  Need to look at Xorg.0.log.

That said I'm working on updating the xsetwacom stylus script.  That might help also.  Probably post it tomorrow.

---

### Post by TheCosmicFrog on 2010-12-07
> **Favux said:**
> Good.  I can't tell if that is Wacom driver behavior though or whether the evdev driver has your stylus.  Need to look at Xorg.0.log.

That said I'm working on updating the xsetwacom stylus script.  That might help also.  Probably post it tomorrow.

Great, will check back tomorrow!

Well it's 5.10am here in Ireland and I don't think I have any more excuses. The bed is calling me. 

Thanks again for all the help!

Aaron

---

### Post by obediah on 2011-01-19
Did TheCosmicFrog get this working? I think I have the same Alda Medion Tablet and had the same problem with floating mouse pointers. This is the evdev driver. The wacom driver will get the 'right' behaviour.

The issue is that the match string in /usr/share/X11/xorg.conf.d/50-wacom.conf doesn't match correctly. While it is a Waltop product it doesn't match the product string "WALTOP". Rather, as "lsusb -v" will show the vendor is waltop but the product is "Digital Ink Pad". By adjusting my product match string accordingly I get it to work for me (at least on maverick). No .xsetwacom.sh is required for me.

e.g. use:
MatchProduct "Wacom|WALTOP|WACOM|Waltop|Digital"

Digital is the part that will match successfully. Its a bit generic so oneday I might plug in some other USB device and have things go bad but for now it works.

---

### Post by TheCosmicFrog on 2011-01-19
> **obediah said:**
> Did TheCosmicFrog get this working? I think I have the same Alda Medion Tablet and had the same problem with floating mouse pointers. This is the evdev driver. The wacom driver will get the 'right' behaviour.

The issue is that the match string in /usr/share/X11/xorg.conf.d/50-wacom.conf doesn't match correctly. While it is a Waltop product it doesn't match the product string "WALTOP". Rather, as "lsusb -v" will show the vendor is waltop but the product is "Digital Ink Pad". By adjusting my product match string accordingly I get it to work for me (at least on maverick). No .xsetwacom.sh is required for me.

e.g. use:
MatchProduct "Wacom|WALTOP|WACOM|Waltop|Digital"

Digital is the part that will match successfully. Its a bit generic so oneday I might plug in some other USB device and have things go bad but for now it works.

I never did get this working, no. But I will definitely check this out tomorrow. Thank you obediah!

---

### Post by Favux on 2011-01-19
Hi obediah,

Welcome to Ubuntu forums!

Nice work!  Sure hope it works for you TheCosmicFrog.

Script is still useful for more control over the stylus when on the Wacom driver.  Pressure levels, stylus button settings, etc.

---

