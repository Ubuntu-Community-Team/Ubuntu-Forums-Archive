---
title: "Making Non-Wacom tablets work in Ubuntu12.04"
date: 2013-03-17
forum: Hardware
---

### Post by EscapedNight on 2013-03-17
I am using Ubuntu 12.04 Unity. And I want to buy a non wacom tablet for my graphics works. Anyways, in different places and forums, I have read that non-wacom tablets doesnt work properly in Linux or if they work, they dont work In Qt apps like krita or Blender. I dont need to make it work In Blender, But I want to and I must work it in krita. (Though in wizardpen setup guide of ubuntu, It is written krita works *"full support since 1.6"*...)

I have read about severals methods about configuring a non-wacom tablet in Linux...like using the ppa of Doctormo (wizardpen driver) or tweaking the evdev driver o or changing few lines in 50-Wacom.conf file or creating some new things inside xorg.conf.d folder...
Since I'm not a programmer type, and because I'm using Ubuntu for one year or so, i know the basics but not a linux savvy. I'm an artist and all I need is a step by step process to make my device work. 

The tablet I'm aiming to buy is all **iBall 8060U** which is a rebranding of [COLOR=#2E3436][FONT=Open Sans]**UC-Logic Tablet WP8060U **[/FONT][/COLOR]and the tablet is on the *supported* list of this page [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status) I dont know much of these, but people were talking about this list in KDE/krita forums...

I better know about a good process because what if after buying it, i find it doesnt work at all...And also Wacom is high for my budget. So Please help.
If even it works out of the box, pressure sensitivity wont work with krita most possibly until we tweak something... If even i get a slightest idea that the tablet should work, I wont have a hole in my pocket buying a wacom...
Thank you.

---

### Post by Favux on 2013-03-18
Hi EscapedNight,

As far as I can tell the iBall 8060U (UC-Logic Tablet WP8060U) should work out of the box in Precise (12.04) for you.  You won't know absolutely for sure until you can run the command **lsusb** in a terminal with the tablet attached.  The output contains the Vendor and Product ID for the tablet.

The "Tablet support status" page tells you the kernel driver for the tablet is working in the 2.6.36 kernel or later.  Precise has the 3.2 kernel.  The evdev X driver (xf86-input-evdev) picks up the usb data from the kernel and translates it into stuff the X Server can understand.  And the X Server is what draws everything on your monitor.

Unfortunately, as far as I know, the Qt bug with evdev is still present.  Qt does not draw with pressure when the Pen is on the evdev driver, although it handles Pens on the Wacom driver fine.  So there is still a problem with Krita unless you do one of the hacks linked to in the DIGI*mend* wiki.

The most recent Blender has fixed the pressure bug it had with evdev.  That doesn't do you much good, does it?

---

### Post by EscapedNight on 2013-03-18
> **Favux said:**
> Hi EscapedNight,

As far as I can tell the iBall 8060U (UC-Logic Tablet WP8060U) should work out of the box in Precise (12.04) for you.  You won't know absolutely for sure until you can run the command **lsusb** in a terminal with the tablet attached.  The output contains the Vendor and Product ID for the tablet.

The "Tablet support status" page tells you the kernel driver for the tablet is working in the 2.6.36 kernel or later.  Precise has the 3.2 kernel.  The evdev X driver (xf86-input-evdev) picks up the usb data from the kernel and translates it into stuff the X Server can understand.  And the X Server is what draws everything on your monitor.

Unfortunately, as far as I know, the Qt bug with evdev is still present.  Qt does not draw with pressure when the Pen is on the evdev driver, although it handles Pens on the Wacom driver fine.  So there is still a problem with Krita unless you do one of the hacks linked to in the DIGI*mend* wiki.

The most recent Blender has fixed the pressure bug it had with evdev.  That doesn't do you much good, does it?


Hi, 
Thank you for replying. yeah that's right, i cant finally understand if there is a problem or not until i get the tablet. But well now i know it SHOULD work. And yeah I dont work much in Blender, so it does not do much good to me :P :D
I will keep this thread unsolved Until i get the tablet so that i can get future helps about configuring it. 
Btw, can you tell me the ways how to make it work in krita? Or you will need the lsusb data and those for that?
I need it work in three apps must - gimp2.8, mypaint and krita. In inkscape it will work i guess.

---

### Post by Favux on 2013-03-18
Viktoria S. figured out how to get them working in Qt/Krita.  Don't know if I would be much help to you with it.  When you go to the DIGI*mend* wiki:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  it's in the Application Setup page.  From there go to the Krita page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Krita](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Krita)

In the tip she links you to the bug report where the hacks are.  As she says using the hack is risky and just because it worked for her doesn't mean it will work for you, although it probably would.  Unfortunately it doesn't look like the Qt dev.s have even looked at the bug report.  So I don't know if they are even aware of the problem or are doing anything about it.

Yes, Inkscape should be fine.

---

### Post by EscapedNight on 2013-03-18
> **Favux said:**
> Viktoria S. figured out how to get them working in Qt/Krita.  Don't know if I would be much help to you with it.  When you go to the DIGI*mend* wiki:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  it's in the Application Setup page.  From there go to the Krita page:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Krita](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_in_Krita)

In the tip she links you to the bug report where the hacks are.  As she says using the hack is risky and just because it worked for her doesn't mean it will work for you, although it probably would.  Unfortunately it doesn't look like the Qt dev.s have even looked at the bug report.  So I don't know if they are even aware of the problem or are doing anything about it.

Yes, Inkscape should be fine.


Those are very useful links, Not much for Krita but for other apps surely. Thank you :)
Some days ago, I posted in Krita's forum...But I didn't notice she posted another solution there without doing anything with Qt. Take a look. [http://forum.kde.org/viewtopic.php?f=139&t=98347&sid=58b1a599eaebfcb047a86d7290fefa18&start=30#p251547](http://forum.kde.org/viewtopic.php?f=139&t=98347&sid=58b1a599eaebfcb047a86d7290fefa18&start=30#p251547)

---

### Post by Favux on 2013-03-18
Yes, but that only works with the new KYE (Genius) tablets, not the UC_LOGIC tablets.  The KYE's will work with the Wacom X driver but the UC-LOGIC tablets don't.  The KYE's are suppose to work with the evdev X driver so using the Wacom X driver amounts to a work around.

---

### Post by EscapedNight on 2013-03-18
> **Favux said:**
> Yes, but that only works with the new KYE (Genius) tablets, not the UC_LOGIC tablets.  The KYE's will work with the Wacom X driver but the UC-LOGIC tablets don't.  The KYE's are suppose to work with the evdev X driver so using the Wacom X driver amounts to a work around.

Oh i see! What a bad luck :/

Okay thank you a lot. I will inform in this thread if I have any trouble with my tablet :)
Have a nice day :)

---

### Post by EscapedNight on 2013-03-20
> **Favux said:**
> Yes, but that only works with the new KYE (Genius) tablets, not the UC_LOGIC tablets.  The KYE's will work with the Wacom X driver but the UC-LOGIC tablets don't.  The KYE's are suppose to work with the evdev X driver so using the Wacom X driver amounts to a work around.

By the way, I heard after 13.04, Ubuntu will be written in Qt - that means non-wacom tablets wont work in ubuntu anymore?

---

### Post by Favux on 2013-03-20
If that happens hopefully the bug will be fixed by then.  But non-wacoms should continue to work in Gtk app.s like Gimp and Inskscape.  And as mentioned Blender has fixed its issue.  Blender doesn't use either of the toolkits, it is independent of Gtk and Qt.

---

### Post by EscapedNight on 2013-03-25
> **Favux said:**
> If that happens hopefully the bug will be fixed by then.  But non-wacoms should continue to work in Gtk app.s like Gimp and Inskscape.  And as mentioned Blender has fixed its issue.  Blender doesn't use either of the toolkits, it is independent of Gtk and Qt.

Hi, I bought the tablet Finally. It's iBall 8060U which is rebranding of UC-Logic WP8060U.

First of all, it's not working well.  Or simply I dont know how to make it work. Works in mypaint, but the brush radius shows pretty big on canvas but the line is not that thick :P
Didnt test in other app yet

Here,


```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 002: ID 192f:0916 Avago Technologies, Pte. 
Bus 004 Device 003: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 003 Device 002: ID 5543:0005 UC-Logic Technology Corp. Tablet WP8060U

 xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                     id=12    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                     id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=10    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=11    [slave  keyboard (3)]




```

Update, it's working in gimp, inkscape and mypaint. Can't sculp on blender because I have 2gb RAM, so cant check. And No pressure in krita. Can you instruct me how to build the patch to make it work in krita?
Also, do i need to calibrate it?

---

### Post by Favux on 2013-03-25
It does sound like it is working as expected.

I've never tried patching Qt before.  Since we are talking Ubuntu I guess the best thing would be to get a hold of the Qt deb package for your release of Ubuntu.  Then you would patch that.  That could be a bit of pain:  taking the deb apart, adding a new patch to the Debian patch control, renaming the deb. etc.  There are instructions on how to do that on the Ubuntu wiki.  It's the kind of thing someone then posts as a PPA if they've gone to that kind of trouble.  Patching and compiling Qt might be simpler but I don't know if it will work if you just use the latest tar release or clone the git repository.  It likely would.  You probably want to check around and see if anyone has posted instructions or a PPA.  Maybe post on the bug report asking for help?

You only need to calibrate if the location of the Pen on the tablet doesn't correspond to where it should be on the monitor.  If tracing the edges of the tablet also traces the monitor edges your are probably good.  If you need to calibrate you could use xinput_calibrator.

---

### Post by EscapedNight on 2013-03-27
> **Favux said:**
> It does sound like it is working as expected.

I've never tried patching Qt before.  Since we are talking Ubuntu I guess the best thing would be to get a hold of the Qt deb package for your release of Ubuntu.  Then you would patch that.  That could be a bit of pain:  taking the deb apart, adding a new patch to the Debian patch control, renaming the deb. etc.  There are instructions on how to do that on the Ubuntu wiki.  It's the kind of thing someone then posts as a PPA if they've gone to that kind of trouble.  Patching and compiling Qt might be simpler but I don't know if it will work if you just use the latest tar release or clone the git repository.  It likely would.  You probably want to check around and see if anyone has posted instructions or a PPA.  Maybe post on the bug report asking for help?

You only need to calibrate if the location of the Pen on the tablet doesn't correspond to where it should be on the monitor.  If tracing the edges of the tablet also traces the monitor edges your are probably good.  If you need to calibrate you could use xinput_calibrator.

well the pen is calbrated it seems, i checked all four corners. My biggest problem is - my paint, gimp doesnt recognize it at first. What i mean is...suppose the tablet is plugged in, and then i start the pc, open gimp/mypaint - gimp doesn't let me draw anything, neither with mouse, nor the pen. By selecting brush, i only get an pointer with a brush icon (normally it takes the shape of the brush selected like eclipes, or spherical) and mypaint thinks my  tablet is a mouse, so until unplug and replug, it doesnt recognize pressure.
I went to gimp edit>prefereces>input devices>extended settings>chose uc-logic>and made the mode to screen> saved and closed  But everytime i start gimp  it takes the core pointer as main input device and let me draw nothing.
My mouse is not unplugged, I have both the tab and mouse plugged always.

---

### Post by Dragonbite on 2013-03-27
With these fixes, are the tablets acting like a tablet (absolute positioning)?  

I have an older tablet that never worked as a tablet, but did as a mouse. Meaning that if I swipe the pen from left to right, the mouse will move from left to right but if I pick up the pen and go back to the left and swipe to the right again the cursor will move further to the right instead of reading that the pen is now on the left side of the tablet and hop the cursor to where it is located.

I haven't tried this in 12.04 so I wonder if it is fixed. That would be awesome.

---

### Post by EscapedNight on 2013-03-27
> **Dragonbite said:**
> With these fixes, are the tablets acting like a tablet (absolute positioning)?  

I have an older tablet that never worked as a tablet, but did as a mouse. Meaning that if I swipe the pen from left to right, the mouse will move from left to right but if I pick up the pen and go back to the left and swipe to the right again the cursor will move further to the right instead of reading that the pen is now on the left side of the tablet and hop the cursor to where it is located.

I haven't tried this in 12.04 so I wonder if it is fixed. That would be awesome.

nah, my pen can do all those what my mouse can. just gimp 2.8 is being buggy and qt developers are not listening to users, so no pressure in krita.

---

### Post by Dragonbite on 2013-03-27
> **EscapedNight said:**
> nah, my pen can do all those what my mouse can. just gimp 2.8 is being buggy and qt developers are not listening to users, so no pressure in krita.

That's the thing, I want my tablet to operate as a tablet (touch left side, cursor jumps to left side, touch right side, cursor jumps to right side) instead of like a mouse.

---

### Post by Favux on 2013-03-27
@ Dragonbite,

Once the kernel driver (usb descriptor) is fixed then the evdev.conf in xorg.conf.d tablet snippet recognizes the tablet as a tablet.  And it automatically sets the tablet to Absolute mode, which is what you want, not Relative Mode like a mouse.  Or the same thing happens if you use the WizardPen driver and it works for your tablet.


@ EscapedNight,

My guess is when you do the hotplug the device order gets changed and that's why Gimp picks up the pen.  If you look at the output from xinput list:
```
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                     id=12    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                     id=13    [slave  pointer  (2)]
```
you see the "device name" for both devices is the same.  One is actually the pen and the other can be the mouse or frame buttons on the tablet.  Some of the app.s like Gimp are set up to handle Wacom and the Wacom X driver appends the device type (stylus, eraser, cursor/mouse, touch) to the "device name".  That way you know what to set to screen in Gimp.  Fortunately usually the first UC-LOGIC device is the pen, but not always as you have found.

You can figure out which is which by running:
```
xinput list-props ID#
```
Where you get the ID# from **xinput list**.  But as you see order apparently can change.

So anyway there is a problem with the current setup.  Either the app.s have to become sensitive to the flag the kernel is putting on the device type or the device type needs to be appended to the device name.  We've been talking about this issue for quite a while without a solution.  Not sure how likely it is the evdev maintainers would accept code to label the device type like the wacom driver has.  But a few weeks ago I found a submission to the kernel's input mailing list where a dev. submitted a patch to append pen to the device name for a touch device that could also use a pen.  Nick wasn't real thrilled with using similar code for UC-LOGIC because he would like a more general solution.  But it looks relatively simple to me.

Easy for me to say because I wouldn't have to code or submit it.  So if the kernel's input maintainers accept the other guy's patch and Nick finds some time to code and submit it we might finally have a solution.

I suspect this limitation is one reason the WizardPen driver only worked for the tablet pen and never the tablet mouse.  It blocked the mouse input.

In the meantime we may be able to set up a custom .conf to block any tablet device but the pen.  Do you have a tablet mouse or is the other device tablet frame buttons?

---

### Post by EscapedNight on 2013-04-10
> **Favux said:**
> ..................

I suspect this limitation is one reason the WizardPen driver only worked for the tablet pen and never the tablet mouse.  It blocked the mouse input.

In the meantime we may be able to set up a custom .conf to block any tablet device but the pen.  Do you have a tablet mouse or is the other device tablet frame buttons?


Hi, I'm sorry for so late reply, I've been pretty busy last few days. So well I got a wireless mouse with the tablet, but i dont use it, neither I know why to use it. So it's packed in my drawer as it came, i didnt even unpack it. I am using only the tablet, the pen and my normal old mouse.

---

### Post by Favux on 2013-04-11
The event node is created whether or not you are actually using the mouse because the kernel driver is aware the tablet supports a mouse.  What I was thinking is we could try to prevent the input event from being created, similar to how the WizardPen .conf file does it.  So the only event would be the pen event.  First you'd need the custom .conf directory /etc/X11/xorg.conf.d and then we could try a custom .conf in it.  See:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev#Custom_tablet_.conf](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev#Custom_tablet_.conf)  If it works then when you run **xinput list** you would see only the one event node for the pen.

---

### Post by CptanPanic on 2013-04-11
Hello,
Maybe you can help me also.  I have a monoprice tablet (WP8060U), and it seems like it is detected fine in X, as I can move the cursor around, but in Gimp if I activate it by setting mode to screen/monitor.  I am unable to move the drawing cursor, just the mouse cursor.  Once the tablet it activated, I cannot draw with mouse either.  What can I check?  This is actually in 12.10.
Thanks,
CP

---

### Post by Favux on 2013-04-11
It sounds like the same issue.  In Gimp how many entries do you see for the tablet and what are they?

---

