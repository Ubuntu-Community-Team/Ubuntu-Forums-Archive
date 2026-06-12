---
title: "Tablet PC (specifically Acer C213TMi)"
date: 2009-08-23
forum: Hardware
---

### Post by RAPTOR_JESUS on 2009-08-23
Hello,

I have been on and off trying ubuntu, and up til release 9.04, I've managed to destroy my install within 10 minutes of installing it, either by using poor drivers, or trying to configure my more windows-friendly hardware.

Now that I've installed 9.04 and it's taken all the beatings I've given it for the past 4 days, I'm thinking now is the time to try and stick at it, and use it pretty much full-time on my Acer Travelmate C213.

I expect you can see by now where I'm going with this - I've searched high and low for a working solution to this: *How on earth do I get the full tablet functionality in ubuntu?*

Every resource I have come across has been roughly at least 2 years old, and none of the stated "fixes" have appeared to work.

Is there any new information getting ubuntu running on these things?

---

### Post by Favux on 2009-08-23
Hi RAPTOR_JESUS,

It looks like a pretty recent machine.  How old is it?  Do you know what sort of digitizer it uses?  A Wacom for example?  And by any chance do you know what internal connection the digitizer uses?  Usb or serial?

---

### Post by RAPTOR_JESUS on 2009-08-24
Yeah, it's not exactly old. My specific machine is the best part of 2 years old now.
Evidence suggests that it is indeed a wacom tablet, pressure sensitive etc. Stylus has 3 "buttons" - tip, side, and eraser. I believe it's also USB, but I'd have to check further.
 
At the moment, holding the side button (under windows, a right click) "grabs" the desktop cube, and allows me to rotate it. As my laptop has only two mouse buttons, I can't tell if this is default behaviour for a middle click or what.
 
wacom-tools doesn't appear to recognise the tablet, but out-of-the-box Ubuntu does permit basic function.
 
Of course, as usual, I'm not experienced with linux, so if there are any OS specifics that can produce more information, I'm all ears!

---

### Post by Favux on 2009-08-24
Hi RAPTOR_JESUS,

While the stylus tip is Button1 usually it's the buttons on the side that count when talking number of buttons.  So you "have" a stylus with one button and an eraser.  That's pretty standard.

In Jaunty (9.04) they came pretty close to out of the box functionality.  But two problems.  The 0.8.2-2 linuxwacom wacom.ko (the usb kernel driver/module) often doesn't work correctly.  It will produce an error #13 or some such.  The other is that the default .fdi doesn't parse the names HAL/dBus is returning correctly into linuxwacom names.

So what we've done is just compile a more recent wacom.ko and copy it over the default wacom.ko.  Just the wacom.ko, not the rest of linuxwacom.

And we've come up with a modified .fdi that parses the names correctly.  This allows you to use 'wacomcpl' (LWP's calibration/configuration gui)  To see what I mean in a terminal enter:
```
xsetwacom list
```
It should return stylus and eraser, not be blank.  To see what HAL is calling your stuff enter:
```
xinput --list
```

First go to Synaptic Package Manager and make sure both of the default 0.8.2-2 linuxwacom packages are installed:  xserver-xorg-input-wacom & wacom-tools.  Reboot.

Then go to "Jaunty Users" near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  And follow the link in 1) to gali98's Jaunty HOW TO.

After you're set up you can get wacomcpl working by looking at Section 3  Calibrating your Table PC lower down on the first HOW TO you link to.  In wacompl when you configure your buttons you'll find out you were right.  Button1 will be the tip, Button2 will be the one on the side of the stylus.  Set Button2 to 3 if you want it as a right mouse click.

Good luck!

---

### Post by RAPTOR_JESUS on 2009-08-26
Sorry it's taken me so long to get back, been busy with dogs ;]

Anyway, on close investigation - specifically xinput --list - I'm starting to think that maybe it **is** a serial tablet.

```
"Wacom Serial Tablet PC Pen Tablet/Digitizer"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1

```

     is what I'm getting back from this. 
Having read on to the how-to, the suggestion was that it'd only work for USB tablets.
Should I go ahead with it anyway, or is there another avenue I should take?

Thanks for your help up to now though :)

---

### Post by Favux on 2009-08-26
Hi RAPTOR_JESUS,

That sure looks like a serial tablet pc to me.  OK, different story.

Yours looks like it is working out of the box except for the problems with name parsing by the .fdi.  It's calling your:

stylus = "Wacom Serial Tablet PC Pen Tablet/Digitizer"

eraser = "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

So look at 3) and 3a) in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  It gives you two options.  If you use rec's script once "xsetwacom list" returns stylus and eraser you're good.

Then follow "Section 3:  Calibrating Your Tablet PC" lower down on the HOW TO.  That should get wacomcpl set up and enable it's settings (in .xinitrc) to survive a reboot.  Also the rotation scripts with "xsetwacom" commands will work.

---

### Post by RAPTOR_JESUS on 2009-08-26
Well, that appears to have worked so far!
Thanks for your time with this, perhaps in hindsight I shouldn't have restricted my searches to my specific tablet model ;)

Now moving onto rotation, and then perhaps the on-board speakers problem...!

In the two years I've been on and off destroying installs of ubuntu, this one certainly seems the most sturdy. 
That said though, are there any linux apps that are actually eraser-aware? Is linux now aware that the eraser is just that; an eraser?

Thanks again for your help!

---

### Post by Favux on 2009-08-26
Hi RAPTOR_JESUS,

Good!

Yes Gimp and Inkscape are.  You have to set up their extended input devices options.  See near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  In Xournal the eraser is the stylus button.  You should also check out CellWriter.

Good luck!  Have fun.

---

### Post by RAPTOR_JESUS on 2009-08-26
Ah, fantastic. Xournal is absolutely essential to me sticking with linux on tablet for the time being; now I've prodded it a bit and set the stylus up the way I want it, it's a perfectly good alternative to Windows Journal. I'll check out Inkscape as well, but as I've not really experimented with the artistic capabilities of the tablet (my own aren't exactly great!) it's lower down the list than getting the sound working.

Has anyone come up with a similar app to MS OneNote yet?

---

### Post by Favux on 2009-08-26
Hi RAPTOR_JESUS,

> Has anyone come up with a similar app to MS OneNote yet? 
No as far as I know only CellWriter can turn writing into text.  Evernote had an online demonstration for linus but I think they dropped it.

---

### Post by RAPTOR_JESUS on 2009-08-26
Well, I've installed CellWriter - looks like it'll take a bit of getting used to, but it's starting to look like I have a functional Linux-flavoured Tablet PC :)

My biggest gripe at the moment is that the three buttons on the side don't work - xev picks up no signal from them being pressed. Shame, but not fatal.

I had seen a thread that would deal with the sound issue (ie, onboard speakers not being used when nothing plugged into the headphone jack), but it's from a couple of years ago, and I wonder if it's "incompatible" so to speak with newer releases.

But all in all, things are looking up :) Thanks!

---

### Post by Favux on 2009-08-26
Hi RAPTOR_JESUS,

Bezel buttons can be a problem.  We can only get 2/4 working for TX2*'s.  Several things could be going on including a buggy DSDT or not having installed a kernel module you need.  To get some ideas, and have a laugh,  see notes just above the key code addendum here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  It links you to some posts.

Sound can be tricky.  Other than searching the forums and googling about the only thing you can do is read the info. on the ALSA site and the wiki.  Although you could take a look for ALSA-Configuration.txt.gz, it should be on your system, probably at /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz.  You read the intro and then try to find the section for your audio chipset.  To get your chipset;
```
aplay -l
```
Then you just try the options available for chip set.  Rebooting between.  Pretty much trial and error.  It's so much better to find someone who already figured it out.  And of course it could be a problem with mixer settings.  Ouch!

---

