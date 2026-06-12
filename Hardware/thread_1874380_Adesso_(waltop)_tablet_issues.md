---
title: "Adesso (waltop) tablet issues"
date: 2011-11-03
forum: Hardware
---

### Post by blackjackhker on 2011-11-03
Hello Ubuntu community :P I'm having some problems right now getting my old Adesso tablet to work under Ubuntu. Here's the life story. I was using 11.04 and all was working fine and dandy with the tablet, but then I switched over to 11.10, and it stopped working right. At first, I could draw with it on KDE's blackboard well, but couldn't use it to click any buttons. It seems that as soon as I click a button, the cursor appears in the top left corner and then flashes back to where it was and the button is not pressed. So I took a shot at fixing it according to a few guides and now I can't seem to get the mouse pointer out of the left corner at all haha.

A problem I'm having (may be noobish :P) following most guides for these tablets is that you are supposed to add a PPA for WizardPen, but when I add the PPA and update, I get a 404, and I can't find xserver-xorg-input-wizardpen in the repo's.

Am I doing anything wrong here? Not exactly sure what I should post for more info, but I'll give what I can.

lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0424:2524 Standard Microsystems Corp. USB MultiSwitch Hub
Bus 003 Device 007: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 007 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 008 Device 003: ID 046d:0a17 Logitech, Inc. G330 Headset
Bus 002 Device 008: ID 050d:3201 Belkin Components F1DF102U/F1DG102U Flip KVM
Bus 002 Device 009: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 003 Device 008: ID 046d:c226 Logitech, Inc. G15 Refresh Keyboard
Bus 003 Device 009: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 003 Device 010: ID 172f:0031 Waltop International Corp. Slim Tablet 12.1"
Bus 003 Device 011: ID 046d:c227 Logitech, Inc. G15 Refresh Keyboard
Bus 002 Device 010: ID 05ac:129c Apple, Inc. 

```ls /usr/share/X11/xorg.onf.d
```

10-evdev.conf  11-evdev-quirks.conf  11-evdev-trackpoint.conf  50-synaptics.conf  50-vmmouse.conf  50-wacom.conf  51-synaptics-quirks.conf

```cat 50-wacom.conf
```

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WALTOP|WACOM|Hanwang|ISD-V4"
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
        MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
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

```Need anything else, let me know. Thanks!

---

### Post by Favux on 2011-11-03
Hi blackjackhker,

Welcome to Ubuntu forums!

With Oneiric as you found out, it works out of the box because it is on the Wacom driver, where it is suppose to be.  You do not need to use the WizardPen driver and besides as you found out DoctorMO hasn't updated the PPA.  I think that's because the WizardPen driver in the Oneiric repository now works for WizardPen tablets if you install it.

Are/were you running an xsetwacom script by chance?  If so could you post it?  If you were running a *set Button 1 1* that's why you couldn't left click.  That's a bug in the current xf86-input-wacoms we found and fixed about a week ago.  Most noticeable if you grab a window.  When you release it it will fly away (the cursor jump you see).

So now we need to figure out why it isn't working.  Check in Software Center or Synaptic that you still have the xorg-xserver-input-wacom package installed.  If not install it and reboot.

If that isn't it please post the output of this command in a terminal:
```
xinput list
```

---

### Post by blackjackhker on 2011-11-03
Thanks! So I see, wizard pen is already installed. Makes sense :P

I haven't used the xsetwacom script yet. Should I? Also, xserver-xorg-input-wizardpen is installed and listed in the software center and synaptic. As for *set Button 1 1*, I haven't specifically entered that in anywhere, so I'd guess not. Though, I have been playing with the settings in System Setting > Input Devices > Tablet a tad. Just to be sure, I reset the settings in there to default with no avail.

xinput list
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet stylus    id=11    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet eraser    id=16    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet pad    id=17    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; G15 Gaming Keyboard                         id=8    [slave  keyboard (3)]
    &#8627; G15 Gaming Keyboard                         id=9    [slave  keyboard (3)]
    &#8627; G15 GamePanel LCD                           id=12    [slave  keyboard (3)]
    &#8627; Belkin Corporation Flip CC                  id=13    [slave  keyboard (3)]
    &#8627; CHICONY HP USB Multimedia Keyboard          id=14    [slave  keyboard (3)]
    &#8627; CHICONY HP USB Multimedia Keyboard          id=15    [slave  keyboard (3)]

```Thanks for your help!

EDIT:

Also may be worth mentioning, it says I have an eraser in that command, but I do not.

---

### Post by Favux on 2011-11-03
OK, but is the wacom driver installed too?  That's the one you want.  It seems to be because of the spurious pad (tablet buttons or express keys) and eraser appended to the <device name>.  Those are because the Wacom code sets up the Waltops to a corresponding Wacom tablet so they come along for the ride.  To verify you should run:
```
xsetwacom list
```
and post the output.  We want to be sure the Wacom X driver (xf86-input-wacom, what Ubuntu calls the xserver-xorg-input-wacom package) is seeing your Waltop.

---

### Post by blackjackhker on 2011-11-03
I believe it is, though I could be wrong. Here's my output:

xsetwacom list
```

WALTOP International Corp. Slim Tablet stylus    id: 11    type: STYLUS    
WALTOP International Corp. Slim Tablet eraser    id: 16    type: ERASER    
WALTOP International Corp. Slim Tablet pad    id: 17    type: PAD

```I also ran this to make sure there weren't any addition wacom packages:

apt-cache search wacom
```

xserver-xorg-input-wacom - X.Org X server -- Wacom input driver
kde-config-tablet - implements a KDE configuration GUI for the Wacom drivers
mypaint - Paint program to be used with Wacom tablets
mypaint-data - Brushes and backgrounds for the mypaint program

```Both xserver-xorg-input-wacom and kde-config-tablet are installed properly. 

Also, I thought it may be beneficial to post this too.

lsmod
```

Module                  Size  Used by
snd_hrtimer            12744  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
dm_crypt               23199  0 
nvidia              11713772  42 
snd_hda_codec_realtek   330769  1 
snd_usb_audio         118064  3 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
joydev                 17693  0 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_pcm                96755  4 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
snd                    68266  21 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
hid_belkin             12632  0 
usbhid                 47198  0 
hid                    95463  2 hid_belkin,usbhid
usb_storage            57901  0 
uas                    18027  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci

```I don't see anything about wacom or waltop in here, though I could easily be mistaken. Unless maybe usbhid is referring to it? The only thing I can think that is unusual about my setup is that I have the tablet plugged into a USB hub (actually the top screen and hub that I salvaged off of my old Logitech G15 that the keyboard sheets went bad in). This didn't present a problem before though, and it's always been running fine like this until recently.

Thanks for all the help!

---

### Post by Favux on 2011-11-03
Your Oneiric setup looks good to me.  I think the Waltop kernel driver is in usbhid (usbhid.ko).

I'm beginning to think you might have this (these?) bug:
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/799202](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/799202)
[https://bugs.launchpad.net/ubuntu/+source/pencil/+bug/762938](https://bugs.launchpad.net/ubuntu/+source/pencil/+bug/762938)

I thought the fix had come through but from the looks of things maybe not.  If not don't know what the hold up is unless the report of the fix causing another bug (near the bottom of the first bug report) halted things.

---

### Post by blackjackhker on 2011-11-03
Those bug reports (especially the first one) seems to describe exactly the problem I was having earlier. Though, I'm not exactly sure how I regressed to not having any cursor movement at all. At the moment, I'm using a dual head setup, each with different resolutions, and my tablet is set to only appear on the left screen at the moment, though I've tested this with each screen individually, and both screens in together with no avail. I'm going to keep playing around with some settings and try to find more guides. This is quite confusing, especially for someone who isn't very experienced with Xorg.

Thanks for the help!

EDIT

Oddly, I noticed that before, when it was working fairly well, I couldn't get the two buttons on the side of the pen to work at all, though now after I have disabled them in the GUI settings pane, they work. That's rather odd.

ANOTHER EDIT

Okay, not I'm dumbfounded. I was playing with the settings, changing thing around and nothing was working. Then, I sighed, closed the settings window, and moved the pen and it started working again O.o But now, my problems are similar, though a bit different. Buttons do not work when clicking them, along with hyperlinks. Though tabs in the settings and in Firefox works fine when clicking them. I'm guessing that it's sending an onclick, but not an offclick.

Also, I'm having a wierd issue that I wasn't having before. I can draw fine in Whyteboard, though I still get random lines when releasing the pen (similar to the first bug you posted), though it seems like the lines are coming from (or going to) the middle of my right-hand monitor. Now, on the KDE blackboard widget, when I press the pen on one spot of the canvas, pick it up completely, then press it on a different part, a line connects the two points where I clicked, though no line ever goes to the middle of my right hand monitor as does with Whyteboard.

I'm not sure what is causing this, but I'm going to keep track of them bug reports and see if any information turns up.

Thanks for all the help!

YAE (Yet another edit :P)

It seems that the random line appearing in whyteboard normally does not appear if I pick up the pen while not in motion, though it adds the line every time I pick the pen up while in motion. Maybe a connection?

EDIT

I downloaded mypaint, and everything works well in it including pressure sensitivity. In the GIMP, it works except for the pressure sensitivity. Also, playing around with it a bit, I can see the cursor jumping to the upper right hand corner of my right screen (note the tablet is bound to the left screen) when depressing the pen. I'm guessing the reason for the lines in whyteboard is due to the way it handles input and is not a bug with the xorg or qt, but that program itself. Though, the cursor moving to the top right of my right monitor is most definitely an issue.

---

### Post by Favux on 2011-11-03
That could be the Gimp history buffer bug, new with Oneiric:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)

---

### Post by sproaty on 2011-11-04
Hi blackjackhker,

I'm the developer of Whyteboard - but I've never tested the application with a tablet and pen, only using a mouse as input; therefore I apologise for the errors you're having.

The way the drawing works is basic starting drawing when the left button is held in, and ending drawing when it is released. Does the pen work that way?

---

### Post by Favux on 2011-11-04
Hi sproaty,

By driver default the pen/stylus tip is Button 1 and it generates a press event when in contact with the tablet and a release when removed.  So it sounds the same.  The Wacom driver also has a pressure feature which uses a Bezier curve but is set to linear by default.

---

### Post by blackjackhker on 2011-11-04
Thanks for the reply Favux! I'm honestly not too worried about the GIMP seeing as I could never get the hang of using a tablet with image editing programs. I strictly use it for note taking and drawing up ideas, hence the use of Whyteboard.

And hello sproaty! I must say, Whyteboard is quite a nice application you've made there! Much appreciated!  As for this problem, what seems to be happening is that the cursor is on the canvas when drawing, though before the offclick event is sent, the cursor instantly moves to the upper right corner of the screen. I imagine your application must also detect mouse events off of the canvas as well as on the canvas. So when the cursor moves to the upper right of the screen without sending an offclick event, a line is drawn from point *a* (where the cursor was when releasing the pen), and point *b *(where the cursor is after the pen glitches and moves to the upper corner).

I would not personally consider this a bug in your software seeing that the pen is giving unusual behavior that is not standard to how it should be used, and this would be hard to replicate without having an issue nearly identical to mine. Though, a fix for this could be to only accept mouse events over the canvas (I believe this would be easy in Python, though I'm not sure what language you used to write this nor am I fluent in any programming language than Python).

Though, like I said, this is not a bug at all on your end.

Thanks for the replies! And thanks sproaty for making this fine application ;)

---

