---
title: "Synaptics Touchpad"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by lee_connell on 2006-08-04
Hi all,

I have Dell E1505 and touchpad works however I'm having issues.  I use the tapping feature to click around.  It seems as though the sensitivity in the xorg.conf file is not correct, but I've played with it and can't get any different results.

When I tap it sometimes takes 2-3 taps to get it to actually execute my tap.  This is very annoyings.  The left mouse click works everytime with no problems.  Is there any advice as to how to fix this problem?

NOTE:  It doesn't matter how hard I tap the touchpad, it still will not execute my tap until the 2nd or 3rd tap.  This doesn't happen everytime but extremely often.

Thanks!

---

### Post by mpvano on 2006-08-05
There are quite a few more settings for the touchpad than the few that are listed in the default xorg.conf file.

On some machines you need drastically different settings than the ones provided.

You should have a program called "synclient" . Try running it from a terminal window. If it won't run and reports a problem with shared memory, you need to modify your xorg.conf to have the line

Option "SHMConfig"                      "true"

in the synaptics input device section and then restart your machine.

using "synclient -l" you can examine ALL the relevant settings. The documentation for the program in /usr/share/doc explains their function.

synclient lets you modify individual settings to experiment until you find a set of settings that work for you. It may take a few iterations to get the touchpad stable in all conditions of humidity, etc.

I use a shell script to load the temporary settings for ALL the possible values (derived from synclient -l) with a single command when I'm experimenting. It's easy to get confused if you modify more than one parameter at a time.

Once you have a set that works well, you can add ALL the variables in the set to the input section in xorg.conf for the touchpad.

You can still "touch up" individual settings using synclient if they're not quite right and then modify them later in xorg.conf. The problem is that settings in xorg.conf only take effecgt when X is started.

I think you're probably having trouble with the values that indicate how many cells need to be active or inactive to indicate the finger is down. The values depend on your finger shape.

These values vary a lot - the values for one brand of computer are unlikely to be right for yours. These values may not work at all with your machine, but for reference, I'm listing the values that work well on my IBM T30 for me. (It took me a while to get them figured out).

        Option "SHMConfig"                      "true"
        Option "LeftEdge"                       "1900"
        Option "RightEdge"                      "5400"
        Option "TopEdge"                        "1900"
        Option "BottomEdge"                     "4000"
        Option "FingerLow"                      "40"
        Option "FingerHigh"                     "50"
        Option "MaxTapTime"                     "180"
        Option "MaxTapMove"                     "220"
        Option "MaxDoubleTapTime"       "180"
        Option "ClickTime"                      "50"
        Option "EmulateMidButtonTime" "75"
        Option "VertScrollDelta"        "70"
        Option "HorizScrollDelta"       "0"
        Option "MinSpeed"                       "0.03"
        Option "MaxSpeed"                       "0.12"
        Option "AccelFactor"            "0.03"
        Option "EdgeMotionMinZ"         "30"
        Option "EdgeMotionMaxZ"         "160"
        Option "EdgeMotionMinSpeed"     "0"
        Option "EdgeMotionMaxSpeed"     "0"
        Option "EdgeMotionUseAlways" "0"
        Option "UpDownScrolling"        "1"
        Option "TouchpadOff"            "0"
        Option "GuestMouseOff"          "0"
        Option "LockedDrags"            "0"
        Option "RTCornerButton"         "0"
        Option "RBCornerButton"         "0"
        Option "LTCornerButton"         "0"
        Option "LBCornerButton"         "0"
        Option "TapButton1"                     "1"
        Option "TapButton2"                     "2"
        Option "TapButton3"                     "3"
        Option "CircularScrolling"      "0"
        Option "CircScrollDelta"        "0"
        Option "CircScrollTrigger"      "0"
        Option "CircularPad"            "0"

Note that my configuration may enable or disable some features according to my taste. For example, I disable horizontal scrolling.

Don't forget your settings will probably be much different than mine. Use the defaults from "synclient -l" for your machine as starting points.

I hope this gets you started...

Mario

---

### Post by lee_connell on 2006-08-07
Mario,

Thank you very much for your detailed response.  I just got time to test this out.  Thanks for the input, I will be trying this tonight!!

Lee

---

### Post by lee_connell on 2006-08-07
I can't seem to get it right it's like it's not detecting my finger pressure every time.  I also have to have sendcoreevents true or mouse wont move.

---

### Post by mpvano on 2006-08-07
I don't know about your sendcoreevents issue, it's probably a difference in how your X windows is configured. I wouldn't worry about it if you got it straightened out...

FingerHi and FingerLow are the values that you should focus on.

For starters, you might go back to just adding the shared memory command and no other settings (just comment them out in xorg.conf if you've already added them), restart X and then dump the defaults for your configuration using synclient -l .

Then experiment with small changes in those values. As I warned you, the values for my machine are probably not even close to appropriate for yours.

You can Think of the FingerHi and FingerLow values as if they are the relative area of your finger in contact to be understood as meaning touching, and releasing contact with pad.

Experiment with just one value a ta time using individual setclient commands. Once you're happier with one, add it to the xorg.conf file. and work on another.

Mario

---

### Post by lee_connell on 2006-08-08
Mario,

I did change fingerhigh and fingerlow.  that seemed to work, now when i tap on something it works 90% of the time, however now i have to put alot more pressure on the touchpad to move the mouse around?

---

### Post by mpvano on 2006-08-08
Sounds like your on the right track. I got things more or less working right in 10 or 20 experiments, but I had to experiment for months to get everything working completely to my satisfaction. Don't be afraid to experiment, the values don't work very intuitively....

A little patience and a lot of experimentation will get you there....

Mario

---

