---
title: "NGS Draw Master not working properly"
date: 2011-02-24
forum: Hardware
---

### Post by durammx on 2011-02-24
Hi!

I was able to run the pen but the mouse isn't working (only the buttons are).

Here goes the Specs:

[NGS -Draw Master]("http://www.ngstechnology.com/desproducto.asp?idp=110&l=6&idcat=11&cl=1") 

xinput --list command

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                   id=8    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse                id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=9    [slave  keyboard (3)]

ls /dev/input/by-id/
usb-UC-LOGIC_Tablet_WP8060U-event-mouse  usb-UC-LOGIC_Tablet_WP8060U-mouse

ls -al /dev/input/by-path
total 0
drwxr-xr-x 2 root root 140 2011-02-25 01:12 .
drwxr-xr-x 4 root root 240 2011-02-25 01:12 ..
lrwxrwxrwx 1 root root   9 2011-02-25 01:12 pci-0000:00:1d.3-usb-0:1:1.0-event-mouse -> ../event3
lrwxrwxrwx 1 root root   9 2011-02-25 01:12 pci-0000:00:1d.3-usb-0:1:1.0-mouse -> ../mouse0
lrwxrwxrwx 1 root root   9 2011-02-25 01:12 platform-i8042-serio-0-event-kbd -> ../event2
lrwxrwxrwx 1 root root   9 2011-02-25 01:12 platform-i8042-serio-1-event-mouse -> ../event4
lrwxrwxrwx 1 root root   9 2011-02-25 01:12 platform-i8042-serio-1-mouse -> ../mouse1

evtest command - USING MOUSE

Event: time 1298602240.672349, type 2 (Relative), code 0 (X), value 1
Event: time 1298602240.672354, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.672357, -------------- Report Sync ------------
Event: time 1298602240.680347, type 2 (Relative), code 0 (X), value 1
Event: time 1298602240.680351, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.680355, -------------- Report Sync ------------
Event: time 1298602240.696348, type 2 (Relative), code 0 (X), value 2
Event: time 1298602240.696352, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602240.696355, -------------- Report Sync ------------
Event: time 1298602240.752350, type 2 (Relative), code 0 (X), value 1
Event: time 1298602240.752354, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.752358, -------------- Report Sync ------------
Event: time 1298602240.776348, type 2 (Relative), code 0 (X), value -1
Event: time 1298602240.776352, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.776355, -------------- Report Sync ------------
Event: time 1298602240.808350, type 2 (Relative), code 0 (X), value -1
Event: time 1298602240.808354, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.808358, -------------- Report Sync ------------
Event: time 1298602240.832348, type 2 (Relative), code 0 (X), value -2
Event: time 1298602240.832355, -------------- Report Sync ------------
Event: time 1298602240.856349, type 2 (Relative), code 0 (X), value -1
Event: time 1298602240.856356, -------------- Report Sync ------------
Event: time 1298602240.872347, type 2 (Relative), code 0 (X), value -1
Event: time 1298602240.872352, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.872355, -------------- Report Sync ------------
Event: time 1298602240.920351, type 2 (Relative), code 0 (X), value 1
Event: time 1298602240.920355, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.920358, -------------- Report Sync ------------
Event: time 1298602240.960349, type 2 (Relative), code 0 (X), value 2
Event: time 1298602240.960353, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602240.960356, -------------- Report Sync ------------
Event: time 1298602240.976344, type 2 (Relative), code 0 (X), value 1
Event: time 1298602240.976350, -------------- Report Sync ------------
Event: time 1298602240.984342, type 2 (Relative), code 0 (X), value 2
Event: time 1298602240.984348, -------------- Report Sync ------------
Event: time 1298602240.992341, type 2 (Relative), code 0 (X), value 1
Event: time 1298602240.992344, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602240.992347, -------------- Report Sync ------------
Event: time 1298602241.000340, type 2 (Relative), code 0 (X), value 2
Event: time 1298602241.000343, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602241.000347, -------------- Report Sync ------------
Event: time 1298602241.008340, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.008343, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602241.008346, -------------- Report Sync ------------
Event: time 1298602241.016340, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.016344, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602241.016347, -------------- Report Sync ------------
Event: time 1298602241.032344, type 2 (Relative), code 0 (X), value 2
Event: time 1298602241.032350, -------------- Report Sync ------------
Event: time 1298602241.040340, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.040345, -------------- Report Sync ------------
Event: time 1298602241.048340, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.048343, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602241.048346, -------------- Report Sync ------------
Event: time 1298602241.064344, type 2 (Relative), code 0 (X), value 2
Event: time 1298602241.064350, -------------- Report Sync ------------
Event: time 1298602241.072341, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.072346, -------------- Report Sync ------------
Event: time 1298602241.080341, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.080347, -------------- Report Sync ------------
Event: time 1298602241.088341, type 2 (Relative), code 0 (X), value 2
Event: time 1298602241.088345, type 2 (Relative), code 1 (Y), value 1
Event: time 1298602241.088348, -------------- Report Sync ------------
Event: time 1298602241.096340, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.096343, type 2 (Relative), code 1 (Y), value 1
Event: time 1298602241.096346, -------------- Report Sync ------------
Event: time 1298602241.104339, type 2 (Relative), code 0 (X), value 1
Event: time 1298602241.104345, -------------- Report Sync ------------
Event: time 1298602241.112343, type 2 (Relative), code 0 (X), value 3
Event: time 1298602241.112346, type 2 (Relative), code 1 (Y), value 1
Event: time 1298602241.112350, -------------- Report Sync ------------
Event: time 1298602244.360335, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.360341, -------------- Report Sync ------------
Event: time 1298602244.368325, type 2 (Relative), code 0 (X), value 1
Event: time 1298602244.368331, -------------- Report Sync ------------
Event: time 1298602244.376326, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.376331, -------------- Report Sync ------------
Event: time 1298602244.384326, type 2 (Relative), code 0 (X), value 1
Event: time 1298602244.384329, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.384332, -------------- Report Sync ------------
Event: time 1298602244.392325, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.392328, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.392331, -------------- Report Sync ------------
Event: time 1298602244.400326, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.400329, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.400332, -------------- Report Sync ------------
Event: time 1298602244.408330, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.408333, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.408337, -------------- Report Sync ------------
Event: time 1298602244.416329, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.416335, -------------- Report Sync ------------
Event: time 1298602244.424326, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.424329, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.424332, -------------- Report Sync ------------
Event: time 1298602244.432325, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.432328, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.432331, -------------- Report Sync ------------
Event: time 1298602244.440325, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.440328, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.440331, -------------- Report Sync ------------
Event: time 1298602244.448325, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.448328, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.448331, -------------- Report Sync ------------
Event: time 1298602244.456328, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.456332, type 2 (Relative), code 1 (Y), value 1
Event: time 1298602244.456335, -------------- Report Sync ------------
Event: time 1298602244.464328, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.464332, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.464335, -------------- Report Sync ------------
Event: time 1298602244.472326, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.472329, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.472332, -------------- Report Sync ------------
Event: time 1298602244.480325, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.480328, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.480331, -------------- Report Sync ------------
Event: time 1298602244.488324, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.488327, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.488331, -------------- Report Sync ------------
Event: time 1298602244.496325, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.496328, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.496331, -------------- Report Sync ------------
Event: time 1298602244.504327, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.504331, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.504334, -------------- Report Sync ------------
Event: time 1298602244.512326, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.512330, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.512333, -------------- Report Sync ------------
Event: time 1298602244.520326, type 2 (Relative), code 0 (X), value 4
Event: time 1298602244.520329, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.520333, -------------- Report Sync ------------
Event: time 1298602244.528324, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.528327, type 2 (Relative), code 1 (Y), value -3
Event: time 1298602244.528330, -------------- Report Sync ------------
Event: time 1298602244.536324, type 2 (Relative), code 0 (X), value 4
Event: time 1298602244.536327, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.536330, -------------- Report Sync ------------
Event: time 1298602244.544325, type 2 (Relative), code 0 (X), value 4
Event: time 1298602244.544328, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.544331, -------------- Report Sync ------------
Event: time 1298602244.552327, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.552333, -------------- Report Sync ------------
Event: time 1298602244.560324, type 2 (Relative), code 0 (X), value 4
Event: time 1298602244.560327, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.560330, -------------- Report Sync ------------
Event: time 1298602244.568327, type 2 (Relative), code 0 (X), value 4
Event: time 1298602244.568331, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.568334, -------------- Report Sync ------------
Event: time 1298602244.576325, type 2 (Relative), code 0 (X), value 4
Event: time 1298602244.576328, type 2 (Relative), code 1 (Y), value -3
Event: time 1298602244.576331, -------------- Report Sync ------------
Event: time 1298602244.584324, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.584327, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.584331, -------------- Report Sync ------------
Event: time 1298602244.592325, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.592328, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.592331, -------------- Report Sync ------------
Event: time 1298602244.600327, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.600330, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.600333, -------------- Report Sync ------------
Event: time 1298602244.608324, type 2 (Relative), code 0 (X), value 3
Event: time 1298602244.608327, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.608330, -------------- Report Sync ------------
Event: time 1298602244.616327, type 2 (Relative), code 0 (X), value 1
Event: time 1298602244.616330, type 2 (Relative), code 1 (Y), value -2
Event: time 1298602244.616333, -------------- Report Sync ------------
Event: time 1298602244.624324, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.624328, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.624331, -------------- Report Sync ------------
Event: time 1298602244.632324, type 2 (Relative), code 0 (X), value 1
Event: time 1298602244.632329, -------------- Report Sync ------------
Event: time 1298602244.640324, type 2 (Relative), code 0 (X), value 2
Event: time 1298602244.640328, type 2 (Relative), code 1 (Y), value -1
Event: time 1298602244.640331, -------------- Report Sync ------------
Event: time 1298602244.656326, type 2 (Relative), code 0 (X), value 1
Event: time 1298602244.656329, type 2 (Relative), code 1 (Y), value 1
Event: time 1298602244.656332, -------------- Report Sync ------------
Event: time 1298602244.672329, type 2 (Relative), code 0 (X), value 1
Event: time 1298602244.672332, type 2 (Relative), code 1 (Y), value 1
Event: time 1298602244.672336, -------------- Report Sync ------------
Event: time 1298602244.704330, type 2 (Relative), code 1 (Y), value 2
Event: time 1298602244.704335, -------------- Report Sync ------------
Event: time 1298602244.736330, type 2 (Relative), code 0 (X), value -1
Event: time 1298602244.736334, type 2 (Relative), code 1 (Y), value 1
Event: time 1298602244.736337, -------------- Report Sync ------------
Event: time 1298602244.744324, type 2 (Relative), code 0 (X), value -2
Event: time 1298602244.744327, type 2 (Relative), code 1 (Y), value 3
Event: time 1298602244.744330, -------------- Report Sync ------------

evtest - USING PEN

Event: time 1298602336.743917, type 3 (Absolute), code 2 (Z), value 18986
Event: time 1298602336.743921, type 3 (Absolute), code 3 (Rx), value 15580
Event: time 1298602336.743924, -------------- Report Sync ------------
Event: time 1298602336.799916, type 3 (Absolute), code 2 (Z), value 19126
Event: time 1298602336.799919, type 3 (Absolute), code 3 (Rx), value 15484
Event: time 1298602336.799921, -------------- Report Sync ------------
Event: time 1298602336.815912, type 3 (Absolute), code 2 (Z), value 19234
Event: time 1298602336.815915, type 3 (Absolute), code 3 (Rx), value 15481
Event: time 1298602336.815917, -------------- Report Sync ------------
Event: time 1298602338.463907, type 3 (Absolute), code 2 (Z), value 3753
Event: time 1298602338.463910, type 3 (Absolute), code 3 (Rx), value 8259
Event: time 1298602338.463913, -------------- Report Sync ------------
Event: time 1298602338.615907, type 3 (Absolute), code 2 (Z), value 3821
Event: time 1298602338.615910, type 3 (Absolute), code 3 (Rx), value 8101
Event: time 1298602338.615913, -------------- Report Sync ------------
Event: time 1298602339.887903, type 3 (Absolute), code 2 (Z), value 29565
Event: time 1298602339.887907, type 3 (Absolute), code 3 (Rx), value 8259
Event: time 1298602339.887909, -------------- Report Sync ------------
Event: time 1298602339.927902, type 3 (Absolute), code 2 (Z), value 29696
Event: time 1298602339.927907, type 3 (Absolute), code 3 (Rx), value 8046
Event: time 1298602339.927909, -------------- Report Sync ------------
Event: time 1298602339.951901, type 3 (Absolute), code 2 (Z), value 29812
Event: time 1298602339.951905, type 3 (Absolute), code 3 (Rx), value 7893
Event: time 1298602339.951907, -------------- Report Sync ------------
Event: time 1298602340.015902, type 3 (Absolute), code 2 (Z), value 29933
Event: time 1298602340.015906, type 3 (Absolute), code 3 (Rx), value 7672
Event: time 1298602340.015908, -------------- Report Sync ------------
Event: time 1298602340.079902, type 3 (Absolute), code 2 (Z), value 30048
Event: time 1298602340.079905, type 3 (Absolute), code 3 (Rx), value 7435
Event: time 1298602340.079908, -------------- Report Sync ------------
Event: time 1298602340.191900, type 3 (Absolute), code 2 (Z), value 30066
Event: time 1298602340.191904, type 3 (Absolute), code 3 (Rx), value 7598
Event: time 1298602340.191906, -------------- Report Sync ------------
Event: time 1298602340.207901, type 3 (Absolute), code 2 (Z), value 29986
Event: time 1298602340.207905, type 3 (Absolute), code 3 (Rx), value 7790
Event: time 1298602340.207907, -------------- Report Sync ------------
Event: time 1298602343.151886, type 3 (Absolute), code 2 (Z), value 27338
Event: time 1298602343.151890, type 3 (Absolute), code 3 (Rx), value 30332
Event: time 1298602343.151892, -------------- Report Sync ------------
Event: time 1298602343.295887, type 3 (Absolute), code 2 (Z), value 27456
Event: time 1298602343.295890, type 3 (Absolute), code 3 (Rx), value 30319
Event: time 1298602343.295893, -------------- Report Sync ------------
Event: time 1298602343.415885, type 3 (Absolute), code 2 (Z), value 27579
Event: time 1298602343.415888, type 3 (Absolute), code 3 (Rx), value 30032
Event: time 1298602343.415890, -------------- Report Sync ------------
Event: time 1298602343.679883, type 3 (Absolute), code 2 (Z), value 27778
Event: time 1298602343.679886, type 3 (Absolute), code 3 (Rx), value 29884
Event: time 1298602343.679888, -------------- Report Sync ------------
Event: time 1298602343.951881, type 3 (Absolute), code 2 (Z), value 27800
Event: time 1298602343.951885, type 3 (Absolute), code 3 (Rx), value 29740
Event: time 1298602343.951887, -------------- Report Sync ------------

---

### Post by Favux on 2011-02-26
Hi durammx,

As you are probably already aware of, most WizardPen tablets do not have a mouse.  We've tried to set the mouse up on a couple of tablets that did have one without any luck.

Right now as you can see from the X & Y postition coordinates reported by evtest the mouse isn't being picked up.

First thing is the default WizardPen 70-wizardpen.conf mouse snippet blocks the mouse rather than enabling it.  So we'd have to modify it.

Then I suppose we need to figure out if the WizardPen driver supports a mouse.  Maybe the driver only supports a device in Absolute mode like the stylus, which is why it doesn't pick up on the mouse which is in Relative mode.  Or possibly we are running into the X server 1.8 or 1.9 not supporting the configuration of a dependent device.  Although if the system sees it as a separate device (different device input event) that shouldn't be an issue.  I don't see why the driver would be limited to only one device input event.

You may need to contact DoctorMo to resolve the issue if we can't figure it out.

---

### Post by durammx on 2011-02-26
Also when I unplug and plug the tablet, the PS/2 mouse make the same thing has the mouse of the tablet. weird??

---

### Post by Favux on 2011-02-26
Are you in Maverick or Lucid?  Since, as I mentioned, there isn't a snippet currently to match the WizardPen mouse and put it on the WizardPen driver I'm not too surprised evdev or some other driver is picking it up.  But from that I'm gathering it isn't coming in on the input device mouse event that the 70-wizardpen.conf is currently blocking, which is interesting.
 
If Maverick your 70-wizardpen.conf should be in /usr/share/X11/xorg.conf.d/.  Let's look at it.

After we modify it we can check in Xorg.0.log in /var/log if the wizarpen driver is picking up the WizardPen mouse.

---

### Post by durammx on 2011-02-27
I'm using maverick!
The config file is on place

Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/by-id/usb-UC-LOGIC_Tablet_WP8060U-event-mouse"
   MatchTag        "wizardpen"
   Driver          "wizardpen"
   Option          "Device"   "/dev/input/event3"
   Option          "TopX"     "208"
   Option          "TopY"     "0"
   Option          "BottomX"  "32311"
   Option          "BottomY"  "32192"
EndSection

Section "InputClass"
   Identifier      "wizardpen ignore mouse dev"
   MatchIsTablet   "on"
   MatchDevicePath "/dev/input/by-id/usb-UC-LOGIC_Tablet_WP8060U-mouse"
   Option          "MouseSpeed" "16"
   Option          "Ignore"     "yes"
   Driver          ""
EndSection

The Xorg.0.log:

XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.202] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.202] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.202] (II) LoadModule: "evdev"
[    18.202] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.202] (II) Module evdev: vendor="X.Org Foundation"
[    18.202]     compiled for 1.9.0, module version = 2.3.2
[    18.202]     Module class: X.Org XInput Driver
[    18.202]     ABI class: X.Org XInput driver, version 11.0
[    18.202] (**) Power Button: always reports core events
[    18.202] (**) Power Button: Device: "/dev/input/event1"
[    18.212] (II) Power Button: Found keys
[    18.212] (II) Power Button: Configuring as keyboard
[    18.212] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.212] (**) Option "xkb_rules" "evdev"
[    18.212] (**) Option "xkb_model" "pc105"
[    18.212] (**) Option "xkb_layout" "pt"
[    18.215] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[    18.217] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.217] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.217] (**) Power Button: always reports core events
[    18.217] (**) Power Button: Device: "/dev/input/event0"
[    18.228] (II) Power Button: Found keys
[    18.228] (II) Power Button: Configuring as keyboard
[    18.228] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.228] (**) Option "xkb_rules" "evdev"
[    18.228] (**) Option "xkb_model" "pc105"
[    18.228] (**) Option "xkb_layout" "pt"
[    18.231] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event3)
[    18.231] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
[    18.231] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev tablet catchall"
[    18.231] (**) UC-LOGIC Tablet WP8060U: Applying InputClass "wizardpen"
[    18.231] (II) LoadModule: "wizardpen"
[    18.232] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[    18.236] (II) Module wizardpen: vendor="X.Org Foundation"
[    18.236]     compiled for 1.9.0, module version = 0.7.4
[    18.237]     Module class: X.Org XInput Driver
[    18.237]     ABI class: X.Org XInput driver, version 11.0
[    18.237] (**) Option "Device" "/dev/input/event3"
[    18.243] (--) UC-LOGIC Tablet WP8060U: MaxX:32767 MaxY:32767 MaxZ:1023
[    18.243] (--) UC-LOGIC Tablet WP8060U: aspect ratio:1.33:1
[    18.243] (**) UC-LOGIC Tablet WP8060U is in absolute mode
[    18.243] (II) UC-LOGIC Tablet WP8060U: ScreenX = 1280, ScreenY = 1024
[    18.243] (**) UC-LOGIC Tablet WP8060U: TopX                   = 208
[    18.243] (**) UC-LOGIC Tablet WP8060U: TopY                   = 0
[    18.243] (**) UC-LOGIC Tablet WP8060U: BottomX                = 32311
[    18.243] (**) UC-LOGIC Tablet WP8060U: BottomY                = 32192
[    18.243] (**) UC-LOGIC Tablet WP8060U: TopZ    (min pressure) = 0
[    18.243] (**) UC-LOGIC Tablet WP8060U: BottomZ (max pressure) = 1023
[    18.243] (**) UC-LOGIC Tablet WP8060U: always reports core events
[    18.253] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: WizardPen Tablet)
[    18.253] (II) UC-LOGIC Tablet WP8060U Increment: 25
[    18.264] (II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse0)
[    18.264] (II) No input driver/identifier specified (ignoring)
[    18.269] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    18.269] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.269] (**) AT Translated Set 2 keyboard: always reports core events
[    18.269] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    18.280] (II) AT Translated Set 2 keyboard: Found keys
[    18.280] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.280] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.280] (**) Option "xkb_rules" "evdev"
[    18.280] (**) Option "xkb_model" "pc105"
[    18.280] (**) Option "xkb_layout" "pt"
[    18.281] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[    18.281] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    18.281] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    18.281] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
[    18.281] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    18.281] (II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    18.281] (II) ImPS/2 Generic Wheel Mouse: Found relative axes
[    18.281] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    18.281] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    18.281] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    18.281] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.281] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    18.281] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    18.281] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
[    18.281] (II) No input driver/identifier specified (ignoring)
[  2452.622] (II) XKB: reuse xkmfile /var/lib/xkb/server-F9AB5957C4038215CF2E4173BD9C63568071BF76.xkm
[  8709.808] (II) XKB: reuse xkmfile /var/lib/xkb/server-F9AB5957C4038215CF2E4173BD9C63568071BF76.xkm

---

### Post by Favux on 2011-02-28
Hi durammx,

You need to remove the *Option "Ignore" "yes"* line.  That tells the X server to ignore that device.  The *Driver ""* essentially does the same thing because it doesn't specify the driver.  So change that line to:
```
Driver "wizardpen"
```
Be sure to have your working 70-wizardpen.conf backed up and be prepared to restore it from the command line if you break X.

---

### Post by durammx on 2011-02-28
Have u saw this project?

[http://digimend.sourceforge.net/](http://digimend.sourceforge.net/)

Mouse still dead

---

### Post by Favux on 2011-02-28
Yes, Nikolai has submitted patches to the kernel to enable the Waltop tablets to work better with the Wacom drivers.

Are you seeing the mouse in *xinput list*?  What device input event or event # is the mouse showing up with in Xorg.0.log?

---

### Post by durammx on 2011-03-05
It's working thanks to Nikolai.


Insta_ll_[]("http://ponomarevs.sknt.ru:48484/pub/linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb")[http://ponomarevs.sknt.ru:48484/pub/linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb](http://ponomarevs.sknt.ru:48484/pub/linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb)
[http://ponomarevs.sknt.ru:48484/pub/xserver-xorg-input-evdev_2.3.2-6ubuntu3.1_i386.deb](http://ponomarevs.sknt.ru:48484/pub/xserver-xorg-input-evdev_2.3.2-6ubuntu3.1_i386.deb)
[http://ponomarevs.sknt.ru:48484/pub/linux-headers-2.6.35-25-generic_2.6.35-25.44_i386.deb](http://ponomarevs.sknt.ru:48484/pub/linux-headers-2.6.35-25-generic_2.6.35-25.44_i386.deb)

And uninstall wizardpen package and delete config files

using this kernel
Mouse and pen working perfectly!

---

### Post by Favux on 2011-03-05
Hi durammx,

Outstanding!  Thanks to you and Nikolai we finally have a solution for the WizardPen mouse.  :)

---

### Post by durammx on 2011-03-06
But only work with this tweak kernel and the evdev-input.

---

### Post by Favux on 2011-03-06
Sure, but that means once the kernel patches are available in a kernel then the WizardPen driver maintainer (Martin Owens?) could add support for the mouse in the WizardPen driver code.

---

### Post by durammx on 2011-03-07
I think the project is a little bit abandoned, but I will send him a mail.

---

### Post by DoctorMO on 2011-03-07
It's not abandoned, it's actually mothballed and I am just a caretaker since waltop kernel patches are taking over from the specialised wizardpen driver.

We need to get in touch with Nikolai and ask him to release DKMS packages instead of full kernel debs. If you install these then you will either a) loose security fixes, b) loose wizardpen support as soon as you get security fixes or c) require Nikolai to release a new kernel every week.

I can't find where to contact Nikolai, but we need to sort this out so Ubuntu users don't install random kernels in the form of downloadable deb files (very undesirable!!). If you know how to contact Nikolai, please ask him to email me and I can help him make dkms packages and put them in the wizardpen ppa for all other tablet users.

Please don't advise other tablet users to download deb file kernels.

---

### Post by Favux on 2011-03-07
Hi Martin,

Nikolai Kondrashov <spbnick@gmail.com>

Please be nice, not that you aren't.  Nikolai seems to be one of the few people working on improving the user experience with generic tablets such as the Genius, Trust, Adesso, DigiPro, Vistablet and others.  UC-LOGIC and other WizardPen and non-wizardpen tablets like the Waltop being among them.

durammx you might even want to give Nikolai some positive feedback.

---

