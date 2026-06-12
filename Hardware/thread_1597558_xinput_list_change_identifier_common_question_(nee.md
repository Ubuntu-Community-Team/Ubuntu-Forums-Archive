---
title: "xinput list: change identifier common question (need: tablet should be &quot;stylus&quot; )"
date: 2010-10-15
forum: Hardware
---

### Post by stefan-koch on 2010-10-15
Hello,
OS:ubuntu 10.10 amd64
does somebody know how to change the identifier from "xinput list"

execute "xinput list" in bash:
root@ubuntu:/home/ubuntu# xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HD Video WebCam                             id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
root@ubuntu:/home/ubuntu#

**I want change "WALTOP International Corp." into "stylus"**

[1] That **works** in ubuntu 9.10 with HAL:
<merge key="info.product" type="string">stylus</merge>

[2] And with that in ubuntu 10.10 with udev it does **NOT** work:
ENV{ID_VENDOR_ID}=="172f", ENV{ID_MODEL_ID}=="0034", ENV{info.product}="stylus", ENV{x11_driver}="wizardpen"


[1]: /etc/hal/fdi/policy/99-x11-wizardpen.fdi
[2]: /lib/udev/rules.d/67-xorg-wizardpen.rules
-see attachments- i have changed the suffix to .txt, because this board software doesn't support .fdi or .rules files.

The problem is: QT-software needs the name "stylus" to work with an tablet. Without that only GTK, ... applications work with the tablet

But this renaming question is **common**.

**Has somebody an idea to solve this problem?**

**Is it possible to change this value with the xorg.conf file?**

Thanks

Stefan Koch

---

### Post by Favux on 2010-10-15
Hi stefan,

It is possible to go back to stylus, eraser, etc. with a wacom tablet using the xorg.conf.  You lose hot plugging of course.  I'm not sure whether it's due to:
```
    Identifier    "stylus"
```
or
```
    Option        "Type"        "stylus"
```
If it's the Identifier it should work for any tablet.

---

### Post by stefan-koch on 2010-10-15
I have added both options to /usr/share/X11/xorg.conf.d/70-wizardpen.conf:

Section "InputClass"
   Identifier      "stylus"
   Option          "Type"     "stylus"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag        "wizardpen"
   Driver          "mouse"
   Option          "MouseSpeed" "16"
   Option          "ignore"     "true"
EndSection


But "xinput list" does not write "stylus" but "WALTOP ..."

---

### Post by Ayuthia on 2010-10-15
You actually have to create an xorg.conf file and place that information in there.  I have not seen a way to change the name through the xorg.conf.d format.

---

### Post by stefan-koch on 2010-10-15
Is there a way to do that with udev?

---

### Post by stefan-koch on 2010-10-15
With the attached config files xinput prints a stylus but also a WALTOP...
And the default mouse driver will not ignored (the same, as no wizardpen driver is installed - with modification for my tablet)

i have compressed the xorg0.log to zip, because this file was to big for this board

---

### Post by stefan-koch on 2010-10-15
The effect of the not ignored mouse driver is, that until the i press with the pen, i mark thinks, resize windows ... : a click event will sent

---

### Post by stefan-koch on 2010-10-15
for more details about the click problem/mouse ignoring problem see: [https://bugs.launchpad.net/wizardpen/+bug/611676](https://bugs.launchpad.net/wizardpen/+bug/611676)

---

### Post by Favux on 2010-10-15
Hi stefan,

Change the mouse ignore snippet in the wizardpen.conf to:
```
Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
Make sure the first snippet for the tablet ("/dev/input/event*") is commented out since you are using xorg.conf for that.

Your:
```
   Option          "Device"        "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse"
```
line isn't working.  Xorg.0.log shows the evdev driver is picking up the Waltop.  Let's find the by-path instead:
```
dmesg | grep [Ww]altop
```
and
```
ls -l /dev/input/by-path
```

---

### Post by stefan-koch on 2010-10-15
It doesn't work

Note actually I would test hal, and have installed it, so I have attached the hal policy file(/etc/hal/policy/99-wizardpen.conf)

It does not work

The attachment (zip-file) includes some config files/log files

---

### Post by stefan-koch on 2010-10-15
What mean you with: "Make sure the first snippet for the tablet ("/dev/input/event*") is commented out since you are using xorg.conf for that."?

---

### Post by Favux on 2010-10-15
The first snippet in post #3 (the wizardpen.conf in xorg.conf.d):
```
#Section "InputClass"
#Identifier "stylus"
#Option "Type" "stylus"
#MatchIsTablet "on"
#MatchDevicePath "/dev/input/event*"
#MatchTag "wizardpen"
#Driver "wizardpen"
#EndSection
```
You don't need it since you are configuring the Waltop to the wizardpen driver in xorg.conf.  Actually since it isn't set up for the Waltop it probably isn't doing anything anyway, but just to be sure.

---

### Post by Favux on 2010-10-15
Alright, from your dmesg it would be:
```
dmesg | grep WALTOP
```
and we need the ls output too.  Do them after a fresh boot.

---

### Post by stefan-koch on 2010-10-16
See a1.zip for ls -l and dmesg

NOTE: hal and wizardpen are not installed (we have a fresh installation)

---

### Post by Favux on 2010-10-16
Good, progress.  The by-path for your Waltop to use in the xorg.conf should be:
```
    Option "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-mouse"
```
You can go ahead and install the 70-wizarpen.conf in the appropriate directory.  Actually, if you've installed the latest WizardPen driver the .conf should be there in Maverick.  DoctorMo just fixed things for the Maverick driver and uploaded them last night.  Be sure to comment out the first snippet, which is for the tablet.  And use the mouse ignore snippet I showed you a few posts back.  Be sure to back up everything before you change it so you can restore the back ups if needed.

This should get the tablet working with the WizardPen driver in xorg.conf, with any luck.

---

### Post by stefan-koch on 2010-10-16
So standard installation with wizardpen works with GTK+ software.

But the standard installation only works if I patch the 67-wizardpen.conf file in /lib/udev/rules.d/

see: [https://bugs.launchpad.net/wizardpen/+bug/611676](https://bugs.launchpad.net/wizardpen/+bug/611676)

now working (**not** "stylus") see attachment a2.zip

---

### Post by Favux on 2010-10-16
OK, if I understand you correctly the Waltop is now working through the xorg.conf but you are not seeing stylus in the 'xinput --list'.  Is that correct?  If so then we've established using Identifier "stylus" in xorg.conf doesn't work to present the system with stylus.  Correct?

By the way I skimmed through your bug report to understand why you added the udev rule.  As far as I know know one else needs to add that with a 70-wizardpen.conf properly configured for the Waltop.
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

### Post by stefan-koch on 2010-10-16
no that was the default installation of wizardpen without xorg.xonf (with xorg.conf.d) in the next step I will test xorg.conf

---

### Post by stefan-koch on 2010-10-16
What's the difference between:
Option     "ignore"     "true"
Option     "Ignore"     "Yes"
AND
Option     "Ignore"     "yes"

?

The first is the default setting, the second from a answer from you to me (yesterday), and the third form you (today)

---

### Post by Favux on 2010-10-16
Probably none.  If true = yes, which it sounds like it does.  OK, I'm interested in seeing where we get with xorg.conf on the stylus issue.

---

### Post by stefan-koch on 2010-10-16
So stylus problem solved, but this prolem exists again (with patch) :[https://bugs.launchpad.net/wizardpen/+bug/611676](https://bugs.launchpad.net/wizardpen/+bug/611676)

---

### Post by Favux on 2010-10-16
Outstanding!  Stylus is now in xinput --list!  Nice job!

OK, hold off on the udev rule for now.  Let's see if we can get it working without it.  First comment out the six coordinate lines in xorg.conf:
```
#   Option          "TopX"          "0"
#   Option          "TopY"          "0"
#   Option          "BottomX"       "20000"
#   Option          "BottomY"       "12500"
#   Option          "MaxX"          "20000"
#   Option          "MaxY"          "12500"
```
And see what that does.

---

### Post by stefan-koch on 2010-10-16
the problem is not the same as in the bug report, see last post in bur report for details. (added before 5 minutes)

---

### Post by stefan-koch on 2010-10-16
With the outcommented lines the problem still exists (click event happens without pressing).

---

### Post by Favux on 2010-10-16
I spoke too soon.  Xorg.0.log shows it on evdev and then evdev finally drops it.  Let's change the xorg.conf a little.  Change the stylus section to:
```
Section "InputDevice"
    Identifier      "stylus"
    Driver          "wizardpen"
    Option          "Device"        "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-mouse"
EndSection
```

---

### Post by stefan-koch on 2010-10-16
that does not work (same problem).

Why not use usb-WALTOP_International_Corp._Slim_Tablet-event-mouse ?

Attachment: includes
/etc/X11/xorg.conf
/usr/share/X11/xorg.conf.d/70-wizardpen.conf
/lib/udev/rules.d/67-xorg-wizardpen.rules
...

What's with the udev rule (you have something impied about udev in your last posts)?

---

### Post by stefan-koch on 2010-10-16
```
root@test-TravelMate-8571:/home/test/a4# ls -l /dev/input/
insgesamt 0
drwxr-xr-x 2 root root    100 2010-10-16 18:27 by-id
drwxr-xr-x 2 root root    160 2010-10-16 18:27 by-path
crw-r----- 1 root root 13, 64 2010-10-16 18:27 event0
crw-r----- 1 root root 13, 65 2010-10-16 18:27 event1
crw-r----- 1 root root 13, 66 2010-10-16 18:27 event2
crw-r----- 1 root root 13, 67 2010-10-16 18:27 event3
crw-r----- 1 root root 13, 68 2010-10-16 18:27 event4
crw-r----- 1 root root 13, 69 2010-10-16 18:27 event5
crw-r----- 1 root root 13, 70 2010-10-16 18:27 event6
crw-r----- 1 root root 13, 71 2010-10-16 18:27 event7
crw-r----- 1 root root 13, 72 2010-10-16 18:27 event8
crw-r----- 1 root root 13, 63 2010-10-16 18:27 mice
crw-r----- 1 root root 13, 32 2010-10-16 18:27 mouse0
crw-r----- 1 root root 13, 33 2010-10-16 18:27 mouse1
root@test-TravelMate-8571:/home/test/a4# ls -l /dev/input/by-id/
insgesamt 0
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 usb-SuYin_HD_Video_WebCam_CN1014-S36D-OV05R-VA-R03.01.01-event-if00 -> ../event6
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 usb-WALTOP_International_Corp._Slim_Tablet-event-mouse -> ../event5
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 usb-WALTOP_International_Corp._Slim_Tablet-mouse -> ../mouse0
root@test-TravelMate-8571:/home/test/a4# ls -l /dev/input/by-path/
insgesamt 0
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 pci-0000:00:1a.7-usb-0:2:1.0-event -> ../event6
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 pci-0000:00:1d.0-usb-0:1:1.0-event-mouse -> ../event5
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 pci-0000:00:1d.0-usb-0:1:1.0-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 platform-i8042-serio-0-event-kbd -> ../event4
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 platform-i8042-serio-4-event-mouse -> ../event7
lrwxrwxrwx 1 root root 9 2010-10-16 18:27 platform-i8042-serio-4-mouse -> ../mouse1
root@test-TravelMate-8571:/home/test/a4#
```

---

### Post by Favux on 2010-10-16
No one else with a Waltop tablet is using your udev rule.

The problem is the stylus or Waltop section we are using is not attaching the WizardPen driver to your tablet for some reason.  So the stylus shouldn't be working.  Is it?  It does not seem to matter which we use, the by-path or by-id.  That's what we have to fix now.

Try adding this line:
```
Section "InputDevice"
    Identifier      "stylus"
    Driver          "wizardpen"
    Option          "Device"       "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-mouse"
    Option          "USB"          "on"
EndSection
```
If that doesn't work add the udev rule in and try the previous xorg.conf.

---

### Post by stefan-koch on 2010-10-18
As you know I have added the following lines to the /lib/udev/rules.d/67-wizardpen.conf file:

```
# Waltop International Corp.
# Genius G-Pen F610
ENV{ID_VENDOR_ID}=="172f", ENV{ID_MODEL_ID}=="0034", ENV{x11_driver}="wizardpen"
```

Should I remove this lines?

---

### Post by stefan-koch on 2010-10-18
Without this lines, with wizardpen standard installation the same error happens. But with this lines the Tablet work's perfect with wizardpen driver standard installation (without exception: "stylus" for QT-Apps)

---

### Post by stefan-koch on 2010-10-18
The USB-option does not solve the problem.

Needs the by-path option, that the tablet is connectet everytime to the same usb-port, or could it connected to other ports?

I can not make sure, that the tablet was on the same port during the posts.

---

### Post by stefan-koch on 2010-10-18
I think the problem is the "standard mouse" that works although if the wizardpen driver is NOT installed.

(this standard driver supports high tablet quality (and I think also pressure sensitivity), too.

But with the described problem.

I think this driver must disablet, is this right?

NOTE: It could be that your instructions help, there are the following issue:
If I press the stylus, the mosue get  a bit leftet and a bit higher, if I release it it get's righter and taller on the screen. (TWO mouses?)

---

### Post by stefan-koch on 2010-10-18
OK this TWO MOSUSES problem only exists with
  Option          "Device"        "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-event-mouse"

and NOT with:

  Option          "Device"        "usb-WALTOP_International_Corp._Slim_Tablet-event-mouse"

---

### Post by stefan-koch on 2010-10-18
Sorry, it exist's in both cases.

(It could be that I have forgotten to change by-path to by-id) --> I think this is a validation that ONE mouse is not disabled.

---

### Post by stefan-koch on 2010-10-18
With both /etc/X11/xorg.conf and /usr/share/xorg.conf.d/70-wizardpen.conf it works half.
xinput lists then stylus and WALTOP

But only if in /etc/X11/xorg.conf
Option "MachTag" "wizardpen" is outcommented
```
Section "InputClass"
   Identifier "stylus"
#   #Option "Type" "stylus"
   MatchIsTablet "on"
   MatchProduct  "WALTOP"
   MatchDevicePath "/dev/input/event*"
#   MatchTag "wizardpen"
   Driver "wizardpen"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchIsTablet     "on"
   MatchProduct    "WALTOP"
   MatchDevicePath "/dev/input/mouse*"
   Option          "Ignore"     "Yes"
EndSection

```

---

### Post by stefan-koch on 2010-10-18
I have found a trick how to disable the default mouse (when no wizardpen driver is installed)

```
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/by-path/platform-i8042*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/by-path/platform-i8042*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/by-path/platform-i8042*"
        Driver "evdev"
EndSection

#Section "InputClass"
#        Identifier "evdev tablet catchall"
#        MatchIsTablet "on"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
#EndSection

#Section "InputClass"
#        Identifier "evdev touchscreen catchall"
#        MatchIsTouchscreen "on"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
#EndSection


```With that config, the graphics tablet is disabled.

But if I change 

CASE 1
Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/**by-path/platform-i8042***"
        Driver "evdev"
EndSection

to
CASE 2
Section "InputClass"
         Identifier "evdev keyboard catchall"
         MatchIsKeyboard "on"
         MatchDevicePath "/dev/input/**event***"
         Driver "evdev"
 EndSection


CASE 1:tablet is disabled, but keybord doesn't work (touchpad works fine)
CASE 2: the same error exists - the click event error. But keybord works (Note without wizardpen driver there never TWO mouses, but the click event happens without pressure) - 

Seemingly the tablet will be recogniced as keyboard, too.

Is there a **option** MatchIs**Not**Product "WALTOP", because I will able to use the keyboard and to disable the default driver. the "ignore" "true" options doesn't work really.

NOTE: in /dev/input are more events than adding /dev/input/by-id and /dev/input/by-path together. 
There is  a platform-i8042-serio-0-event-kbd but you see in CASE 1 it doesn't work.

---

### Post by Favux on 2010-10-18
Hi stefan,

I'm not following everything you are doing.

The basic problem I see from a4 and a5's Xorg.0.log is your Waltop tablet is not using the WizardPen driver.  I don't know why.  It is on the evdev driver.  That seems to be the basic issue.  It may be the WizardPen driver is not correctly installed.

I would suggest removing all of your changes to udev, xorg.conf, etc.  Then follow the Waltop HOW TO:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)  Then let's look at your Xorg.0.log and see if your Waltop is finally on the WizardPen driver.

Once we've seen proof you have a working WizardPen driver then let's try the changes for stylus in the 70-wizardpen.conf and xorg.conf.

---

### Post by stefan-koch on 2010-10-19
NOTE: I use two different ubuntu 10.10 "installations" one with wizardpen driver and one without.
The without is run ubuntu10.10 live cd from usb.

My intention was how to disable the evdev driver, and THEN enable wizardpen driver.
Because there are two mouses, perhaps the first evdev and the second wizardpen - that was my idea, but this idea could be wrong.

---

### Post by Favux on 2010-10-19
> NOTE: I use two different ubuntu 10.10 "installations" one with wizardpen driver and one without.
The without is run ubuntu10.10 live cd from usb.
Ahhh.
> My intention was how to disable the evdev driver, and THEN enable wizardpen driver.
Because there are two mouses, perhaps the first evdev and the second wizardpen - that was my idea, but this idea could be wrong. 
This is the reverse order of how you want to do it.

Evdev only picks up a device if no other driver has picked it up.  It is the failsafe driver.  That's why it has the catchalls.  So you want WizardPen working.  That will get you a more accurate picture of what is happening.

The "ignore mouse dev" snippet prevents the WizardPen from trying to set up on the spurious mouse device.  Actually some Waltop tablets do come with a tablet mouse, but we don't know how to get them working yet.  It seems like the WizardPen driver can't handle both a stylus and a mouse.

---

### Post by stefan-koch on 2010-10-20
So now I have tested the same procedure in the installation with wizardpen driver.

If I use the /usr/share/X11/xorg.conf.d/10-evdev.conf:
```
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/by-path/platform-i8042*"
        Driver "evdev"
EndSection

#Section "InputClass"
#        Identifier "evdev keyboard catchall"
#        MatchIsKeyboard "on"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
#EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/by-path/platform-i8042*"
        Driver "evdev"
EndSection

#Section "InputClass"
#        Identifier "evdev tablet catchall"
#        MatchIsTablet "on"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
#EndSection

#Section "InputClass"
#        Identifier "evdev touchscreen catchall"
#        MatchIsTouchscreen "on"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
#EndSection
```

With this trick I can use the tablet correctly with name "stylus" in xinput list (WALTOP doesn't appear anymore) But I can't use my keyboard. I must use a screen keyboard to enter xinput list >> xinput ...

**Is there a option MatchIs_Not_Vendor "WALTOP"?**

---

### Post by stefan-koch on 2010-10-20
Although that works with "stylus" QT-Apps doesn't recognize the tablet.

xorg.conf (without the outcommented lines)
```
Section "ServerLayout"
    Identifier "Default Layout"
    InputDevice "stylus"
EndSection

Section "InputDevice"
   Identifier      "stylus"
   Driver          "wizardpen"
   Option          "Type"   "stylus"
   Option          "Device"        "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse"
   Option          "USB"           "on"
EndSection
```

---

### Post by Ayuthia on 2010-10-20
Which Qt apps are you trying to use?  My last understanding with some Qt apps like Krita will now be able to use pressure with the stylus for the Wacom driver.  The original change was that it needed to be stylus, but it looks like it now does not need the that as the name.  I have an N-trig device that is using the Wacom driver for the stylus (with the name 'N-Trig Pen stylus') and the pressure is working.  

I am not for sure about the wizardpen driver though.

---

### Post by stefan-koch on 2010-10-20
I have tested my own application that uses QTabletEvent "header" and Krita.
In ubuntu 9.10 set "stylus" with hal (for info.product - without xorg.conf) solved this problem (for Krita and my own app).

[http://doc.qt.nokia.com/4.7/qtabletevent.html](http://doc.qt.nokia.com/4.7/qtabletevent.html)
-> Note for X11 users

[http://doc.qt.nokia.com/4.7/qtabletevent.html#uniqueId](http://doc.qt.nokia.com/4.7/qtabletevent.html#uniqueId)
means that, that wacom driver is at exceptional position? Or is "stylus" required, too. Or would it work also with wizardpen?

---

### Post by Ayuthia on 2010-10-20
> **stefan-koch said:**
> I have tested my own application that uses QTabletEvent "header" and Krita.
In ubuntu 9.10 set "stylus" with hal (for info.product - without xorg.conf) solved this problem (for Krita and my own app).

[http://doc.qt.nokia.com/4.7/qtabletevent.html](http://doc.qt.nokia.com/4.7/qtabletevent.html)
-> Note for X11 users

[http://doc.qt.nokia.com/4.7/qtabletevent.html#uniqueId](http://doc.qt.nokia.com/4.7/qtabletevent.html#uniqueId)
means that, that wacom driver is at exceptional position? Or is "stylus" required, too. Or would it work also with wizardpen?

I think that Qt actually coded something special for the Wacom driver.  From what I understand, the device needs to be using the Wacom driver and Type has to be stylus.  The name of the device is no longer an issue as far as I can tell.

I am thinking that the wizardpen driver is not compatible with it right now, but I could be wrong.  I am not able to find any information on it.

---

### Post by Favux on 2010-10-20
Any information on the Aiptek driver?  I think we can set up your Waltop tablet on it too.

Disappointing that the system now says stylus but you still can't get pressure.  I assume you verified the tablet is now on the WizardPen driver and not evdev.

I suppose we could try putting your Waltop tablet on the wacom driver, where it's suppose to be anyway.  I'm just doubtful that the kernel patches that would allow us to do that have been backported into Maverick yet.  But we might get lucky.  Maybe the new kernel updates have it.

---

### Post by stefan-koch on 2010-10-20
Pressure sensitive works (GIMP) but not in QT apps.

---

### Post by stefan-koch on 2010-10-20
@Ayuthia
Since when? Qt 4.6 or Qt 4.7?
With ubuntu 9.10 and Qt 4.5 it works fine.

---

### Post by stefan-koch on 2010-10-20
Why patching kernel?
Why are there so many different drivers, that support my WALTOP tablet: evdev (Yes, evdev supports pressure sensitivy), wizardpen, wacom and aiptek driver?

---

### Post by Favux on 2010-10-20
> Why patching kernel?
The Waltop kernel driver in the hid usb part of the kernel doesn't support the Wacom X driver like it should.  Nikolai Kondrashov has submitted patches to the kernel to make it work right.  In the meantime the wacom dev.s have set up the Wacom X driver to work with Waltop as soom as the kernel does.
> Why are there so many different drivers, that support my WALTOP tablet: evdev (Yes, evdev supports pressure sensitivy), wizardpen, wacom and aiptek driver?

Just lucky I guess.  But seriously the Waltop is suppose to be on the wacom driver.  That's intended to be it's home.  It did work on the wacom driver in Intrepid.  And in Jaunty and Karmic with a minor patch to the wacom driver.  Waltop did release a stand alone driver for their tablet based on the linuxwacom driver.  We did finally get it to compile but it was kind of disappointing.

---

### Post by stefan-koch on 2010-10-20
I think that I have seen there are new kernel packages in the update manager.
Does they include the patch?

---

### Post by Ayuthia on 2010-10-20
> **stefan-koch said:**
> @Ayuthia
Since when? Qt 4.6 or Qt 4.7?
With ubuntu 9.10 and Qt 4.5 it works fine.

The changes for the Wacom driver were in 4.7.  I was thinking that they added Wacom support in 4.7, but I would not think that they would have taken away any functionality for other devices (of course there are regressions that do occur).

---

### Post by Favux on 2010-10-20
> I think that I have seen there are new kernel packages in the update manager.
Does they include the patch?
I don't know.  I think the patches were submitted to the 2.6.36 or .37 kernel.  So the Ubuntu dev.s would have to deliberately backport them into the Ubuntu 2.6.35 Maverick kernel.  That's what I meant by "get lucky".

---

### Post by stefan-koch on 2010-10-20
@Favux
Should I now uninstall the wizardpen driver and install the wacom driver?

---

### Post by stefan-koch on 2010-10-20
@Ayuthia
Are there plans (at Nokia), to support wizardpen, aiptek driver, too?
Or making the Qt tablet support driver and name (stylus, ...) independet, like GTK it does?

---

### Post by Favux on 2010-10-20
Well it is a long shot.  But if you want to try you just need to comment out the WizarPen stuff in xorg.conf and the 70-wizardpen.conf.  You don't need to uninstall the driver.  Then you'd need make sure xserver-xorg-input-wacom is installed.  Then you'd want to change the 50-wacom.conf from:
```
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#    MatchProduct "Wacom|WALTOP|WACOM"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

```
to
```
Section "InputClass"
    Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
    MatchProduct "Wacom|WALTOP|WACOM"
#    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

```

---

### Post by stefan-koch on 2010-10-20
Thanks, that will work out of the box. Including Pressure sensitivity. It works fine with Krita and my QT-App.
Note xinput shows the vendor, too (but including stylus) was that the mistake?

---

### Post by Ayuthia on 2010-10-20
> **stefan-koch said:**
> @Ayuthia
Are there plans (at Nokia), to support wizardpen, aiptek driver, too?
Or making the Qt tablet support driver and name (stylus, ...) independet, like GTK it does?

I am not for sure.  I was surprised that they did it for a specific driver.  I am not for sure about the next direction, but I would think that they will do something about it.  Either that or else a generic driver is going to help make it all happen.  

It is looking like touchscreens are going toward the evdev driver (for multitouch) and most stylus devices are becoming supported by the Wacom driver.

---

### Post by Favux on 2010-10-20
Hi stefan,

> Thanks, that will work out of the box. Including Pressure sensitivity. It works fine with Krita and my QT-App.
That is absolutely outstanding!  :)

If you could test it some more and verify it is working well I can change the HOW TO's.  I wish we knew whether it was due to them fixing the kernel (or whatever) or not.  Or if you just got lucky with your particular tablet.
> Note xinput shows the vendor, too (but including stylus) was that the mistake?

Adding stylus (and eraser) to "WALTOP International Corp. Slim Tablet" is being done by the wacom driver.  That's it's new naming convention.  The Xorg.0.log shows that.

---

### Post by stefan-koch on 2010-10-20
What driver should I test wizardpen or wacom?

xinput list showed with wizardpen: "stylus"
why not "WALTOP ... stylus" ?

---

### Post by Favux on 2010-10-20
I'm talking about the wacom driver which has given you pressure in everything.  I want to know if your tablet continues to work correctly with it or if there are problems.

With the WizardPen driver we were "forcing" stylus using the xorg.conf.  We could have used "WALTOP International Corp. Slim Tablet stylus" as the Identifier, but you said Krita and my QT-App were hard coded for "stylus".  Because they wrote the fix for the wacom driver it really doesn't matter what the name is now.

---

### Post by stefan-koch on 2010-10-20
@Fafux
My next step is installing ubuntu 10.10 on harddisk. I hope that I get no problems, but the first effect is very good.

@Ayuthia
Thanks, too.

---

### Post by stefan-koch on 2010-10-22
There is a little problem with the wacom driver.

See attached png for details.

If I write fast, some points before I press will recogniced OR after I press it unpressed points will recogniced.

I have feel so, but it could be that's no new thing... And it's only my handwriting is to bad...
-> this could be an little ERROR in wacom driver / or with my tablet or it is NOT an error.
(I thought that this was in wizardpen better)

---

### Post by Favux on 2010-10-22
Let's set up an xsetwacom script and see if you can adjust the stylus preformance using wacom.  What is your output with?:
```
xsetwacom list
```
You stylus has two buttons.  Does it actually have an eraser?

---

### Post by stefan-koch on 2010-10-22
The WALTOP taplet does not have a pen, including an eraser when rotate the pen 180°.
I can use the both buttons in Xournal as eraser, but I can match the buttons to other functions.

```
user5v@PC-5V:~$ xsetwacom list
WALTOP International Corp. Slim Tablet eraser ERASER    
WALTOP International Corp. Slim Tablet stylus STYLUS
```

---

### Post by stefan-koch on 2010-10-22
I have uploaded a wrong screenshot. Now it is the right one.

---

### Post by Favux on 2010-10-22
OK, with your stylus on the wacom driver this script should work for you.  Notice there are a fair number of parameters you can adjust.  So play with them if needed.

Download the script and make it executable.  Instructions are in "IV. For Lucid & Maverick you use a xsetwacom script file..." at the [Bamboo P&t HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

### Post by stefan-koch on 2010-10-22
I have execute the script. Both buttons open the context menu. (right click with touchpad,...).
It does not solve the problem (see screenshot for details)
What are the 4 Parameters in PressCurve?
The tablets maximum coordinates are Y: 12500 X:20000 (that are the values from wizardpen)
Is it possible to set TopZ, BottomZ like wizarpen it allows?

---

### Post by stefan-koch on 2010-10-22
I use TopX=0 TopY=0 BottomX=20000 BottomY=11250 because I have a 16:9 display and the tablet is 16:10

---

### Post by Favux on 2010-10-22
It sets the bezier curve, how hard or soft it is.
> PressCurve            i1 i2 i3 i4                 sets the pressure bezier curve, where i1+i4=100; i2+i3=100

> It does not solve the problem (see screenshot for details)
I don't actually understand your problem.  You could try changing ClickForce.

---

### Post by stefan-koch on 2010-10-22
Is it possible to set a timer after 10 ms Xournal will get the first click event?

---

### Post by stefan-koch on 2010-10-22
the problem is the t should not have this ledger (to bottom).
I have tested this with windows, this happens sometimes but not so often than wit wacom driver.
With wizardpen this was similar.

It could be that wizardpen and the windows driver are slower in reaction time - could it be?

---

### Post by stefan-koch on 2010-10-22
Your script solves the improve the prolem, a bit.

---

### Post by stefan-koch on 2010-10-22
The problem is marked in the screenshot with a red cycle.
see #62

---

### Post by stefan-koch on 2010-10-22
If I take the Suppress option to 20 the prolem arise!

---

### Post by stefan-koch on 2010-10-22
Suppress = 1 solves the problem!

---

### Post by stefan-koch on 2010-10-22
What is Suppress?

---

### Post by Favux on 2010-10-22
Are you saying when you move the stylus tip fast, loops are not forming?

Nur eine bisschen Deutsch sprechen.

---

### Post by Favux on 2010-10-22
Good!
> Suppress                integer (0 - 100)      number of data trimmed for the tools associated with the same tablet

from:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

---

### Post by stefan-koch on 2010-10-22
Yes, that could be my expression.

---

### Post by stefan-koch on 2010-10-22
Suppress = 0 brings X-Server to crash or to stop working
Why that?

---

### Post by Favux on 2010-10-22
xsetwacom rewritten for xf86-input-wacom.  The HOW TO has the old xsetwacom for linuxwacom.  So change the range from 0-100 to 1-100.  Notice that is in the script I gave you.

---

### Post by stefan-koch on 2010-10-23
I have attached a screenshot that show you the difference between Suppress 4 and Suppress 1.

(Favux_Waltop_wacom.conf-.xsetwacom.sh was **not** executed)

---

### Post by Favux on 2010-10-23
Hi stefan,

Thank you.  Now I see what you were talking about.  Suppress 1 eliminates the unintended "lines" or stylus markings.

---

### Post by stefan-koch on 2010-10-28
With suppress value 1 it works fine.

Is it possible to set up the suppress rule in 50-wacom.conf in /usr/share/X11/xorg.conf.d INSTEAD setting it in the .xsetwacom...sh script? (system spectrum <-> user spectrum)

---

### Post by Favux on 2010-10-28
Hi stefan,

Yes, it would look like:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Suppress" "1"
EndSection
```
From:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

---

### Post by stefan-koch on 2010-10-29
Option "Surpress" "1" 
-OR-
Option "Suppress" "1"

does not work.

xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Suppress
-> returns in both cases 4.

(xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Surpress
-> Unknown parameter name 'Surpress'.)

---

### Post by Favux on 2010-10-29
Sorry for the typo.

It's interesting the Option does not work the same as the xsetwacom command.  They should be the same.  As you know the xsetwacom commands were rewritten for xf86-input-wacom.  Maybe they're going through different sections of the code or there is a bug with one or the other.

Don't do this, but it does make you wonder what would happen if you used the Option in a xorg.conf section.

---

### Post by mrspacklecrisp on 2010-11-20
So sorry to barge in here, but I'm having the same problem and I'm not sure what to do. Lucid, Asus T101MT, tablet uses evdev and our own egalax driver. I can make lines as normal, but no pressure. If anyone would be willing to help me I would be oh so grateful.

---

### Post by stefan-koch on 2010-12-15
@mrspacklecrisp:
I tried first to forbid X11 to use the evdev driver (you should it see in any of my posts) but if this is a way, the solution is not beautiful.

@fafux
the tablet works fine with the wacom driver. but I must set the "Suppress" value manually, is it possible to do this automatically? with .xsessionrc this works, but only if the tabled is connected before log in.

---

### Post by Favux on 2010-12-15
Hi stefan-koch,

> the tablet works fine with the wacom driver
Good.
> but I must set the "Suppress" value manually, is it possible to do this automatically? with .xsessionrc this works, but only if the tabled is connected before log in.

I just noticed in post #85 we had the Waltop match line commented out.  Maybe that's why suppress didn't work?  It should have been:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
	MatchProduct "Wacom|WALTOP|WACOM"
#	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Suppress" "1"
EndSection
```
If that isn't the problem did we set up your script in autostart?
> To set it up to auto-start, download the attached file, and rename it .xsetwacom.sh (or whatever you want) and place it in your home directory. Remember it will be a hidden file. To enable the xsetwacom commands in the .xsetwacom.sh file to apply to Xserver through a reboot you enter in a terminal:
```
chmod +x ~/.xsetwacom.sh
```
or you could right click on the file and in Properties, in the Permission tab, check Execute as program. Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh" (without the quotes). You can also change your settings on the fly using the xsetwacom parameters in a terminal. They only apply during the current session.

Once the script is executable you can double click on it to apply it's settings or reboot to check the auto-start set up.


---

### Post by stefan-koch on 2010-12-20
```
-rw-------  1 user5v user5v 532141 2010-12-20 22:07 .xsession-errors
-rw-------  1 user5v user5v      0 2010-12-09 21:27 .xsession-errors-:1
-rw-r--r--  1 user5v user5v     73 2010-12-15 12:22 .xsessionrc
-rwxr-xr-x  1 user5v user5v     74 2010-12-17 18:11 .xsetwacom.sh

```.xsessionrc:
```
setwacom set "WALTOP International Corp. Slim Tablet stylus" Suppress 1

```.xsetwacom.sh
```
#!/bin/sh
xsetwacom set "WALTOP International Corp. Slim Tablet stylus" Suppress 1
``````
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
#       MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "20000"
        Option "BottomY" "11250"
        Option "Suppress" "1"
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


```[B]
But if I plug the tablet after log in in the usb port - it doesn't set the Suppress to 1
Have you an idea?[/B]

Thanks

---

### Post by stefan-koch on 2010-12-27
My pen has two buttons, but both does the same.
How to enable the second button? How to scroll with the tablet (with second button)?

A.e. first button: right click
second: scroll

How to enable this?

Thanks

---

### Post by Favux on 2010-12-27
Hi stefan-koch,

Use Options after the driver line.  So for Suppress it should look like:
```
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
#       MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Suppress" "1"
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "20000"
        Option "BottomY" "11250"
EndSection

```
Or leave the Suppress line out of wacom.conf and use the xsetwacom command.  You shouldn't need to use both.  The same with the TopX&Y etc. coordinates.

In the wacom.conf the stylus buttons would look like:
```
Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
#       MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Suppress" "1"
	Option "Button2" "3"  # right click
	Option "Button3" "2"  # middle click
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "20000"
        Option "BottomY" "11250"
EndSection
```
And you can use xsetwacom instead for the buttons.

But the Waltop stylus buttons don't seem to work quite right with the Wacom driver.  Some were reporting each button was working but most that both do the same thing.

Stylus buttons won't do scroll.  However you can install EasyStroke and it will do scroll for you when you use the stylus.  The EasyStoke wiki has that example.

---

### Post by stefan-koch on 2010-12-28
With this config:
```

Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
#       MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Option "Suppress" "1"
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "20000"
        Option "BottomY" "11250"
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

```I've got this (.xs....sh-scripts are now disabled):
```

xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Suppress
4

```

---

### Post by stefan-koch on 2010-12-28
```

Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
#       MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "20000"
        Option "BottomY" "11250"
        Option "Button2" "3"
        Option "Button3" "2"
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

Now with both buttons a right click will emitted.

---

### Post by stefan-koch on 2010-12-28
xinput --list shows an eraser and the stylus

```

xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2+USB Mouse                            id=10   [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet eraser     id=12   [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet stylus     id=13   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=15   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; HD Video WebCam                           id=11   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=14   [slave  keyboard (3)]

```

---

### Post by Favux on 2010-12-28
Did you try putting the driver line above the options like I suggested?
```
        Driver "wacom"
       Option  ...
```
It looks like maybe the default Suppress for your Waltop is 4.  To check out your default parameters use:
```
xsetwacom get "WALTOP International Corp. Slim Tablet stylus" "Suppress" param
```
or
```
xsetwacom get "WALTOP International Corp. Slim Tablet stylus" "Button2" param
```
etc.

Without a script or trying to set the value in wacom.conf.

---

### Post by stefan-koch on 2010-12-29
With that wacom.conf
```

Section "InputClass"
        Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
        MatchProduct "Wacom|WALTOP|WACOM"
#       MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "TopX" "0"
        Option "TopY" "0"
        Option "BottomX" "20000"
        Option "BottomY" "11250"
#       Option "Button2" "3"
#       Option "Button3" "2"
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

I've got this:
```

xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Suppress
4

```

and you would have this:
```

user5v@PC-5V:~$ xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Suppress param
4
user5v@PC-5V:~$ xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Button2 param
2
user5v@PC-5V:~$ xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Button3 param
3
user5v@PC-5V:~$ xsetwacom get "WALTOP International Corp. Slim Tablet stylus" Button1 param
1

```

Thank you for the numerous answer's.

---

### Post by stefan-koch on 2011-02-18
I have tested today kubuntu 10.10 daily (2011-02-18 ) now evdev works fine. The problem, that the click event will be send if I only move the stylus (without pressing) has been solved.

With evdev now both buttons work, not only one as with the wacom driver.

But the bad end: it works fine with GTK-apps but not with QT.

---

