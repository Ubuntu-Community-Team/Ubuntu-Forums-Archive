---
title: "Does Ubuntu even suport Genius tablets?"
date: 2012-02-22
forum: Hardware
---

### Post by Cæncel on 2012-02-22
today i bought one, Genius  G-Pen 509 and can't find how to properly setup it, all i find is that outdated thing about this PPA my Synaptic PAckage Managers keep telling is 404:  ppa:doctormo/xorg-wizardpen

```
Failed to fetch http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/doctormo/xorg-wizardpen/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
```what do i need for using my tablet? i spent at least one hour trying to figure out how and this whole thing is letting me down, how is that wacom support is that big and genius related hardware is not mentioned?

i'm using X/Ubuntu 11.10

---

### Post by Favux on 2012-02-22
Hi Cæncel,

Support should be automatic now with Oneiric.  The Genius tablets that are supported in the 3.0 kernel are automatically picked up by the evdev X driver.  That's why the DoctorMO PPA hasn't been updated for Oneiric.  The WizardPen driver's job has been taken over by evdev.

We need to know which model tablet you have.  Post the line in the output of the following command in a terminal:
```
lsusb
```
that has the tablet in it.

---

### Post by Cæncel on 2012-02-22
is the last line:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 007 Device 003: ID 172f:0038 Waltop International Corp. Genius G-Pen F509
```

Also i noticed that sometimes my device works "fine", others it don't and some times the tablet just switch from working properly (full area of sensitivity) to just a small region and really badly detected, a stright line actually does curves and some other weird behavior, to be sure my device works fully i tested it on a Windows xp machine, with no problems. I say it works "fine" because i have problems with the two buttons of the pen, is there anything i can do to calibrate it?, thanks for the reply

---

### Post by Favux on 2012-02-22
OK, you have Waltop tablet.  They are suppose to use the Wacom X driver but some of them seem to work better with evdev.
Vendor ID = 172f = Waltop
Product ID = 0038

Let's see what driver it is on.  What is the output of this terminal command?
```
xinput list
```

Not sure yet what is causing the intermittently working issue.  Is this happening after hot pluggin it?

---

### Post by Cæncel on 2012-02-22
```
 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PIXART USB OPTICAL MOUSE                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=14    [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP             Tablet          id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```

yes, sometimes it happens as soon as the device is connected, sometimes the device starts pretty good and in the middle of test or after assigning them other functions, like with MyPaint preferences, the odd behavior starts, other times it just start bad and immediately fixes itself, is pretty confusing.

---

### Post by Favux on 2012-02-22
Alright, my guess is it is currently on the evdev driver.  Let's check that.  What is the output of:
```
xinput list-props 11
```

---

### Post by Cæncel on 2012-02-22
ok, here is the output:

```
Device '         WALTOP             Tablet    ':
    Device Enabled (155):    1
    Coordinate Transformation Matrix (157):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (275):    0
    Device Accel Constant Deceleration (276):    1.000000
    Device Accel Adaptive Deceleration (277):    1.000000
    Device Accel Velocity Scaling (278):    10.000000
    Evdev Axis Inversion (279):    0, 0
    Evdev Axis Calibration (280):    <no items>
    Evdev Axes Swap (281):    0
    Axis Labels (282):    "Abs X" (295), "Abs Y" (296), "Abs Pressure" (297)
    Button Labels (283):    "Button Left" (158), "Button Middle" (159), "Button Right" (160), "Button Wheel Up" (161), "Button Wheel Down" (162), "Button Horiz Wheel Left" (163), "Button Horiz Wheel Right" (164), "Button Side" (293), "Button Extra" (294), "Button Unknown" (274), "Button Unknown" (274), "Button Unknown" (274), "Button Unknown" (274)
    Evdev Middle Button Emulation (284):    0
    Evdev Middle Button Timeout (285):    50
    Evdev Wheel Emulation (286):    0
    Evdev Wheel Emulation Axes (287):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (288):    10
    Evdev Wheel Emulation Timeout (289):    200
    Evdev Wheel Emulation Button (290):    4
    Evdev Drag Lock Buttons (291):    0

```

---

### Post by Favux on 2012-02-22
On evdev.  Why don't you try Wacom and see if that makes a difference.  Check the /usr/share/X11/xorg.conf.d/50-wacom.conf and see if Waltop is commented out in it.  I've forgotten if it still is.  If it is add Waltop matching by following the instructions on the Waltop HOW TO for Natty:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)

---

### Post by Cæncel on 2012-02-22
> **Favux said:**
> On evdev.  Why don't you try Wacom and see if that makes a difference.  Check the /usr/share/X11/xorg.conf.d/50-wacom.conf and see if Waltop is commented out in it.  I've forgotten if it still is.  If it is add Waltop matching by following the instructions on the Waltop HOW TO for Natty:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)

i don't see a 50-wacom.conf file, do i need to install first a package or something?

---

### Post by Favux on 2012-02-23
The Wacom package should be installed automatically as a default.  The package is called xserver-xorg-input-wacom and contains the Wacom X driver xf86-input-wacom.

---

### Post by Cæncel on 2012-02-23
> **Favux said:**
> The Wacom package should be installed automatically as a default.  The package is called xserver-xorg-input-wacom and contains the Wacom X driver xf86-input-wacom.
ok. installed the package and created the file as expected, it has already a line for Waltop:
```

Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WALTOP|WACOM|Hanwang|ISD-V4"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection
```

i tried as the tutorial says but i don't see any folder or file "xorg.conf.d" under /etc/X11/, and after see that the file already has some lines with WALTOP i don't know if i should keep with the HOW TO

---

### Post by Favux on 2012-02-23
You don't need to keep up with the HOW TO.  That's only if that file doesn't have Waltop.  Now if you restart or log out it should be on the Wacom driver when you go back in.  Does it work?

---

### Post by Cæncel on 2012-02-23
well, yes and not, it works in the sense that the pen now is able to use the whole tablet for drawing, but the issue with the buttons and the oddities drawing persist, plus, there is a big lag between traces, i made a quick test moving the pen in a straight line and this is how is drawn:

In Pencil (Animation software):

[IMG]http://img11.imageshack.us/img11/2570/pencl.png[/IMG]

and in MyPaint:

[IMG]http://img51.imageshack.us/img51/9259/penk.png[/IMG]

plus my pen's buttons are also wrong, pressing one leads the function of the other being activated and in some cases, to draw as if the pen were pressed against the tablet, can this be corrected with configuration or calibration?

---

### Post by Favux on 2012-02-23
I see pressure in those lines, which is good.  What exactly is wrong with the lines?  Are you just drawing straight lines and getting that?  Still too busy for me to follow you.

Hopefully the buttons and maybe the lag are configuration issues.  What is the output of?
```
xsetwacom list
```
Are you using generic Ubuntu Oneiric?

---

### Post by Cæncel on 2012-02-23
> **Favux said:**
> I see pressure in those lines, which is good.  What exactly is wrong with the lines?  Are you just drawing straight lines and getting that?  Still too busy for me to follow you.

Hopefully the buttons and maybe the lag are configuration issues.  What is the output of?
```
xsetwacom list
```Are you using generic Ubuntu Oneiric?

well, the lines are wrong because these are intended to be straight lines, and not curves, whenever i make a line or a simple shape, the cursor don't follow my movement and goes wild in some cases:

```
         WALTOP             Tablet     stylus    id: 11    type: STYLUS    
         WALTOP             Tablet     eraser    id: 15    type: ERASER    
         WALTOP             Tablet     pad    id: 16    type: PAD   
```i'm using a Xubuntu derivative, 11.10 with generic Kernel and nothing really modified, some days back i noticed i no longer can slide my list of bookmarks on Firefox with the wheel mouse but i pay no importance since everything out of that works as always, i have to mention that the lag don't happen with the mouse so i'm guessing it could be something with configuration, maybe two libraries trying to take over the pen or the mouse and the pen fighting over who is the slave input or something

---

### Post by Favux on 2012-02-23
Huh.  So that might be serious bug somewhere.  And you were seeing that with evdev also, correct?

Because your "device name" is mishapened (exported that way from the kernel) we might have a little trouble figuring it out for the xsetwacom commands because the unnecessary whitespaces maybe required.  In other words you might have to use:
```
"         WALTOP             Tablet     stylus"
```
instead of:
```
"WALTOP             Tablet     stylus"
```
for example.  So you may have to play around with it a little.

For the buttons try entering in a terminal:
```
xsetwacom set "         WALTOP             Tablet     stylus" Button 2 3
xsetwacom set "         WALTOP             Tablet     stylus" Button 3 2
```
For the lag try:
```
xsetwacom set "         WALTOP             Tablet     stylus" RawSample 8
```
To get the buttons working without the tip touching the tablet try:
```
xsetwacom set "         WALTOP             Tablet     stylus" TabletPCButton off
```
Enter in a terminal *man xsetwacom* to see the instructions.

---

### Post by Cæncel on 2012-02-23
well, i tried with a few values and nothing seems to improve at all, it makes sense that the name of my tablet is being read as "[FONT=monospace]  [/FONT]        WALTOP             " and not "WALTOP", looking at the anterior post and the list of available devices inside GIMP for example, list my device with that name including spaces, so either i'm not doing things right or this is going beyond my power because the configurations don't seem to work at all, i also would like to know if i'm going to have to make all this again in the next Ubuntu release which is LTS, or if while this finds a solution is worth install a drawing program via Wine so i can start working right away with some works i have scheduled? is there anything else i can do besides the configuration?

also many thanks for your support, is quite disappointing not being able to use it i can't deny it, but well, i'll be willing to do what it takes to fix it soon.

---

### Post by Favux on 2012-02-23
Shoot.  By the way you can use the ID # instead of the "device name" like we did in the *xinput list-props* command earlier.  The reason you want to use "device name" is the ID # can change, especially after a hot plug.

You should run the *xinput list-props* command now that the tablet is on the Wacom driver.  Often you can find the problem by looking at your Xorg.0.log file in /var/logs.

Provided the install of the xf86-input-wacom package went OK you should see some effect from the the xsetwacom commands.  Your model is in the xf86-input-wacom source code in the wcmUSB.c code:
```
	{ WALTOP_VENDOR_ID, 0x38, 100000, 100000, &usbBambooFun  },
```
So I don't think the Wacom X driver is the problem.

Looking on Nick's [DIGImend Project]("http://digimend.sourceforge.net/") site I don't see your model in the compatibility table:  [http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v0.4](http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v0.4)  What that could mean is Nick needs to fix the HID descriptor for your model so it behaves correctly.  If that is so he would want the information from usbhid-dump he describes in *HOW TO HELP*.  You might want to contact him and ask him about your model.

He just figured out the KYE Systems Genius tablets and is in the process of adding them to the kernel.  As far as I've been able to tell he's pretty much the only developer working on the non-Wacom tablets.  So he deserves kudos.

---

### Post by Cæncel on 2012-02-23
> **Favux said:**
> 

Looking on Nick's [DIGImend Project]("http://digimend.sourceforge.net/") site I don't see your model in the compatibility table:  [http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v0.4](http://digimend.git.sourceforge.net/git/gitweb.cgi?p=digimend/kernel-patches.git;a=blob_plain;f=COMPATIBILITY;hb=v0.4)  What that could mean is Nick needs to fix the HID descriptor for your model so it behaves correctly.  If that is so he would want the information from usbhid-dump he describes in *HOW TO HELP*.  You might want to contact him and ask him about your model.

thanks, i'm going to check that *HOW TO HELP*, at this point is somehow a relief to know that my device is not supported at all, since everything else was working as it should and the problem was not in my tablet or system at all.

> He just figured out the KYE Systems Genius tablets and is in the process of adding them to the kernel.  As far as I've been able to tell he's pretty much the only developer working on the non-Wacom tablets.  So he deserves kudos.

he certainly deserves them, only one person, wow, i'm going to send him the results of my tests, and thank you again, hopefully this can be corrected soon :)

---

### Post by Cæncel on 2012-02-24
ok, some news, i reported my problem with Nikolai "Nick" and he is currently helping me, he sent me a patch for the kernel and i'm currently compiling it (and lord if takes hours), he says he made changes to support tablets but that these changes in the Kernel may be around at least in half a year more or less, never the less he said this patch could be helping me while the next official release is.. uh... released. greetings and really, i'm very grateful for your help Favux.

---

### Post by Favux on 2012-02-25
Thanks for the update Cæncel!  Good luck.  :)

---

