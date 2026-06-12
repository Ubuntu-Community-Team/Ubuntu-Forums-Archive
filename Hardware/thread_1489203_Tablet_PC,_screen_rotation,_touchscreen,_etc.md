---
title: "Tablet PC, screen rotation, touchscreen, etc"
date: 2010-05-20
forum: Hardware
---

### Post by sinerasis on 2010-05-20
Hello all,

I just got my new Toshiba m780. Seems as though most things work fine with 10.04 LTS.

I'm looking for some help with the tablet mode, does Ubuntu have any tablet solutions?

Ideally when I flip the screen around it would switch to portrait (I can do that with settings manually just fine). The touchscreen does not flip when I do the rotation though, so that's a problem (it gets out of whack). Any ideas there?

I will mostly be using it for gps mapping (tangogps). 

I'm thinking about trying the Netbook edition, just to see if it makes buttons bigger and more touch friendly, but I'm not really sure yet.

Thanks in advance,
Jeff
(Seattle)

---

### Post by Favux on 2010-05-20
Hi Jeff,

```
The touchscreen does not flip when I do the rotation though, so that's a problem (it gets out of whack).
```
Do you mean the digitizer devices like stylus, and touch?  By the way what does it have:  stylus, stylus buttons (how many), eraser, and touch?  What script are you using for rotation?  Does the swivel hinge have a switch, so that you get automatic screen/digitizer rotation in Windows?

Probably just need the names of your devices for the rotation script.  So enter in a terminal:
```
xinput --list
```

---

### Post by sinerasis on 2010-05-20
When I rotate the screen, from landscape to portrait the resolution adjusts and the screen looks good, but when I touch the screen the mouse will move as if the screen is still in landscape mode.

There's a stylus, with eraser and thumb button, and you can touch the screen with your fingers. In Windows the rotation does happen automatically, so yes, I assume there is a screen switch/button in there somewhere.

Here's the results of xinput:

 Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                         id=15    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=14    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; CNA7157                                     id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]


There are also a few buttons on the screen which look like they are for rotation, but I'm not really sure (I wiped Windows right when I got it).

---

### Post by Favux on 2010-05-20
OK, so what you need to be aware of in a rotation script:

stylus = Serial Wacom Tablet

eraser = Serial Wacom Tablet eraser

touch = Serial Wacom Tablet touch

There was a change in the naming convention to longer more descriptive names.  Just substitute in the longer name or the ID number for the older nomenclature like stylus.

See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  A method one script should work for you.  Then just set it up on a launcher or if you detect a signal from the rotation key you can key bind it.  Also described in the HOW TO.  Or you might want to try wacomrotate, Method 3.

---

### Post by sinerasis on 2010-05-20
Thanks Favux!

Looks like it's rotating properly with your script, however I've got another weird thing going on now...

When I run the script to rotate it, the screen will flip, the touch controls look to be working, however when I lift my finger the pointer skips to the lower right corner of the screen. Make any sense?

---

### Post by sinerasis on 2010-05-21
Actually, it's just touch input that is making the cursor jump, the pen and eraser is tracking properly when rotated. Do I need to include a rotation on the mouse or glidepoint by any chance?

...and how would I set this script to run when the screen is turned to tablet mode automatically?

---

### Post by Favux on 2010-05-21
Hi Jeff,

Good you're rotating and so have a working tablet pc.  :)

The touch pointer jumping when rotated is a bug in the X driver xf86-input-wacom.  It's been fixed but you'd have to clone the git repository.  See Appendix 5 in the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

To get automatic rotation you can look at Method 4's auto-rotation script.  That depends on a signal the HP swivel hinge sends through WMI.  I don't know if there is a toshiba-wmi.  Some send it through ACPI, so if you detect a signal with ACPI listen you should be able to get it working.

---

### Post by sinerasis on 2010-05-21
I seem to be having problems with step 4 of Appendix 5:

~/Desktop/xf86-input-wacom$ ./autogen.sh --prefix=/usr
./autogen.sh: 9: autoreconf: not found

---

### Post by Favux on 2010-05-21
Looks like you missed a dependency(ies) in step 3) like autoconf.  If you copied that line notice it's long and extends well beyond the end of the box.

---

### Post by sinerasis on 2010-05-21
Yes that was the problem. It successfully ran, but I'm still getting a jumping mouse...

---

### Post by Favux on 2010-05-21
Do you mean an external usb mouse you have attached or touch's pointer arrow?

All I can say is it has worked for several folks so far.  Maybe try rebooting a couple times.

---

### Post by sinerasis on 2010-05-21
no external mouse, I just use the trackpad.

I'll give a few reboots and report back...

Thanks for your help thus far! :)

---

### Post by sinerasis on 2010-05-21
after a couple of reboots no change.

in portrait mode, touching the screen works normally, but when I lift my finger off the cursor jumps to that position rotated clockwise.

kinda seems like something else needs to be included in the rotation script, but I've tried all the devices listed in the xinput -list with not change...

any ideas?

---

### Post by Favux on 2010-05-21
Does the cursor/pointer return to your finger when you touch the screen again?

If touch in portrait starts off in correct orientation, pointer at finger, then the rotation script is right.

---

### Post by sinerasis on 2010-05-21
Yes, when I'm using my finger to touch the screen the cursor follows my finger.

Only once I lift my finger off does the cursor jump.

It does not jump when using the stylus or eraser.

---

### Post by Favux on 2010-05-21
Hi Jeff,

OK, that sounds kind of like the bug I reported to the LWP's bug tracker, except for the calibration offset I had, and was fixed in linuxwacom 0.8.6-2.  I'm pretty sure the fix made it into the latest xf86-input-wacom git repo so I don't know why cloning it didn't fix it for you as it has for others.  But there is a new touch/touch gestures patch coming through that may fix it for you.  Hopefully out in the next week or two.  Then just try cloning the git again.  Monitor:  [https://sourceforge.net/projects/linuxwacom/](https://sourceforge.net/projects/linuxwacom/) and [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog) for it.

Fortunately it's cosmetic and not functional.

---

### Post by sinerasis on 2010-05-21
Good to know, I'll be watching for it. Thanks for the help :)

---

### Post by sinerasis on 2010-05-22
I've been continuing to play around and see if I can figure anything out. So I haven't gotten anywhere, but I had a few more questions pop up:

After rotating the screen, the trackpad/mouse works in relation to ubuntu, but not logically for the user: if the top of the screen is rotated to the left of the screen, moving the mouse up on the trackpad, moves the mouse left visually. So you're moving it up in ubuntu, but left visually by sliding your finger up on the trackpad. Is that supposed to happen? It's not at all easy to use that way.

---

### Post by Favux on 2010-05-22
It just means the trackpad hasn't been rotated unlike the wacom devices.  There may be a way to do that.  Is it a Synaptics pad?  But why would you want to?  When rotated in tablet mode doesn't your screen cover the trackpad?

---

### Post by sinerasis on 2010-05-22
Yes on both of those.

Well... I guess since I haven't gotten it usable in portrait mode, I've been using the trackpad... it probably wouldn't be an issue if I could get the touchscreen to work in portrait mode




somewhat related, is there any software that would add a virtual keyboard that's actually usable? it'd be nice if it would integrate well, when you hit a text field or something it would auto pop up and stuff (kinda like android/iphone)

---

### Post by Favux on 2010-05-22
Sure you want at least CellWriter, Xournal, and EasyStroke.

---

### Post by sinerasis on 2010-05-22
Favux

Going back to the rotation script, how would you rotate the mouse with the display?

I don't know much about bash programming, but it looks like the script is calling xsetwacom, which probably wont work for devices that aren't using the wacom driver?

How would I prefix other devices? Is the information contained in the output of xinput -list?

---

### Post by Favux on 2010-05-22
Right, xsetwacom commands are only for wacom devices.

Well, given I've never done it theoretically it would be something like the following.  Given your xinput --list showed what looked like three mouses:
```
&#9116; &#8627; PS/2 Mouse id=11 [slave pointer (2)]
&#9116; &#8627; AlpsPS/2 ALPS GlidePoint id=12 [slave pointer (2)]
&#9116; &#8627; Macintosh mouse button emulation id=16 [slave pointer (2)]
```
And it looks like your trackpad is the ALPS Glidepoint.  So you'd want to look at it's properties  with some variation of:
```
xinput list-props AlpsPS/2
```
Then once you get output you'd want to see if it included something describing Axes like:
```
Axis Inversion (128)
Axis Calibration
Axes Swap
```
Then if so you would have to mess with something like:
```
xinput set-int-prop AlpsPS/2 128
```
followed by a couple integers specifying what you want.

Anyway a fair amount of work.

---

### Post by sinerasis on 2010-06-01
I've messed around with different versions, reinstalling, etc.

Still getting the jumping mouse. Where can I go for some more help?

---

### Post by odd on 2010-08-09
I've also got the jumping touch pointer when rotated. I've submitted bug report @LWP ([https://sourceforge.net/tracker/?func=detail&aid=3041514&group_id=69596&atid=525124](https://sourceforge.net/tracker/?func=detail&aid=3041514&group_id=69596&atid=525124)).

Funny thing is, as I described in bug-report - touch pointer worked for a while when I enabled easystrokes at startup with Button1 as gesture button, but from few days it doesn't.

I don't think I've messed with anything related (maybe the mouse properties (acceleration, sensitivity, double-click timeout) - but nothing more than that.

---

