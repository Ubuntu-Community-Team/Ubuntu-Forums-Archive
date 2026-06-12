---
title: "Help with ISDV4 device/wacom digitizer"
date: 2012-04-24
forum: Hardware
---

### Post by Bones.Kendall on 2012-04-24
Hi, 

I am starting this thread at the suggestion of Favux (Thanks!) because my digital pen is not working correctly based on some recent upgrade.

I am so grateful for the help.

xinput list is this:

```
 Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                id=13   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                 id=14   [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                       id=15   [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation          id=16   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                id=11   [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                  id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Chicony USB 2.0 Camera                    id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
```The odd behavior is that there is no longer pressure. 

And the pen does not write consistently. I will draw a line and it will sometimes quickly sometimes after a moment stop drawing. 

Touch is more consistent, but even with that it will not draw a line when the finger moves too quickly. And the line is not smooth.

Buttons don't work; eraser doesn't work.

I used to change things on my system to get it working, but for a while now, since I started using Kubuntu maybe two years ago, so much has run so smoothly.

So I'm not even sure what I'm running: 

>  do you have the default xf86-input-wacom for Lucid How can I find out?

I think I have this: 2.6.32-41-generic

Thanks for any help.

- Bones

---

### Post by Favux on 2012-04-24
Alright, you appear to have the Lucid Kubuntu.  Along with the 2.6.32 kernel you should have X Server 1.7.  You can enter the terminal command:
```
Xorg -version
```
to verify.

Your *xinput list* seems to indicate a match to the Wacom X driver is being made in the 10-wacom.conf.  This line:
```
&#9116;   &#8627; Serial Wacom Tablet                       id=15   [slave  pointer  (2)]
```
seems to indicate you have the default xf86-input-wacom-0.10.5 installed.  Otherwise I think you'd see:
```
&#9116;   &#8627; Serial Wacom Tablet stylus                id=15   [slave  pointer  (2)]
```
The X driver is now up to version 0.14.0.  By the way Ubuntu calls the package that has the xf86-input-wacom in it xserver-xorg-input-wacom.
> The odd behavior is that there is no longer pressure.

And the pen does not write consistently. I will draw a line and it will sometimes quickly sometimes after a moment stop drawing.

Touch is more consistent, but even with that it will not draw a line when the finger moves too quickly. And the line is not smooth.

Buttons don't work; eraser doesn't work.
Did this happen suddenlty after an update?  Or has this been going on a while?  You know that eraser works only in programs that support it like Gimp.  But you have to configure the extended input devices.

Let's look at the stylus in a little more detail.  Post the output of this command:
```
xinput list-props "Serial Wacom Tablet"
```

---

### Post by Bones.Kendall on 2012-04-24
Okay, so Xorg is 1.7.6

As is, the pen is not usable. I usually use Xournal and that has the eraser feature. I just rechecked it. Xournal allows for the use of  Xinput or not. Using Xinput, the eraser does work, but not consistently.

Everything used to work, pen, highlighter button, eraser. I don't recall changing anything. I believe the problem happened with an upgrade, but I wasn't paying too much attention.


Here is the code from 
xinput list-props "Serial Wacom Tablet"
```
Device 'Serial Wacom Tablet':
        Device Enabled (134):   1
        Device Accel Profile (253):     0
        Device Accel Constant Deceleration (254):       1.000000
        Device Accel Adaptive Deceleration (256):       1.000000
        Device Accel Velocity Scaling (257):    10.000000
        Wacom Tablet Area (318):        0, 0, 26112, 16320
        Wacom Rotation (319):   0
        Wacom Pressurecurve (320):      0, 0, 100, 100
        Wacom Serial IDs (321): 147, 0, 2, 0
        Wacom TwinView Resolution (322):        0, 0, 0, 0
        Wacom Display Options (323):    -1, 0, 1
        Wacom Screen Area (324):        0, 0, 1280, 800
        Wacom Proximity Threshold (325):        0
        Wacom Capacity (326):   -1
        Wacom Pressure Threshold (327): 7
        Wacom Sample and Suppress (328):        2, 4
        Wacom Enable Touch (329):       1
        Wacom Hover Click (330):        1
        Wacom Tool Type (331):  "STYLUS" (334)
        Wacom Button Actions (332):     "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)

```

Thanks again for the help!

Bones

---

### Post by Favux on 2012-04-24
Hi Bones,

In summary:
**Toshiba Portege tablet PC**
Kubuntu 10.04
Kernel = 2.6.32-41
X Server = 1.7.6
xserver-xorg-input-wacom 0.10.5?

Worked correctly until recently.  Update?
Line lag with stylus and intermittent eraser.  Stylus side buttons no longer working.


What would be good is to next rule out a (new) hardware problem.  Do you happen to have a Windows or other install where it works correctly?  Might you have access to another stylus you could check with?

Your *xinput list-props* for the stylus looks good.  You might want to do the same for the eraser and see if anything jumps out.

The line lag can happen when something starts grabbing the CPU.  There's an old Gtk bug that does that in Gnome for instance.  Have you tried running ***top*** in a terminal and checked if a process is grabbing a large portion of the CPU cycles when you see the lagging line?

What is the output of?
```
xsetwacom list
```
Are the stylus buttons not working at all or just not the way you want?

---

### Post by Bones.Kendall on 2012-04-24
Okay, so I booted Windows and there, too, there was a problem, leading me to believe it's the pen itself. 

I rebooted into Kubuntu and launched Xournal and pulled out the "lead tip" from the pen. When writing with just the tip, there is no pressure sensitivity, but the line is followed and drawn without error. That is not happening when the tip is in the pen.  

When I get home tonight, I will try the pen from my old Toshiba R15 and see if that gives me any different result.  I'm going to do some more testing in Windows, too. 

It'll be many hours before I come back, so thanks for the help so far and I'll follow up with more details.  

Bones

---

### Post by Bones.Kendall on 2012-04-24
Embarrassedly, I admit that the problem was with the pen. 

My old pen, from a former tablet, works perfectly, so I tried to solve a problem that wasn't software related. Sorry to waste your time.

Thank you for making me think of it. I appreciate your time and thanks to the Ubuntu community!

Bones

Note to self: Get a backup pen.

---

### Post by Favux on 2012-04-24
Hi Bones,

Glad you got that straightened out.  :)

No reason to be embaressed.  The styli are pretty reliable and it is usually the nib (tip) that goes bad, not the pen's coil/capacitor (LC) circuit.

A backup stylus is a good idea and they're not that expensive.  Fortunately your old Toshiba R15 tablet PC stylus (ISDV4 device and same manufacture didn't hurt) worked on the new Toshiba.  Different styli for different Wacom tablets may not work on other models.

---

### Post by Bones.Kendall on 2012-04-24
Thank you for the explanation. I was wondering how complicated the parts are in the pen. It looks too difficult to take apart, but I thought about trying.

Another day. Back to grading essays.

Thanks again!

---

