---
title: "Touchpad settings, Lenovo Yoga 2 Pro"
date: 2015-02-14
forum: Hardware
---

### Post by kuckunniwi on 2015-02-14
Hi,

I was wondering if anyone might be able to give me a tad of direction to get my touchpad working smoothly. By default, in Kubuntu Trusty, it's jumpy and a bit difficult to use. There are suggestions in several different places to modify **/usr/share/X11/xorg.conf.d/50-synaptics.conf**. In particular, I tried the option [here]("http://askubuntu.com/questions/367963/ubuntu-on-lenovo-yoga-2-pro"), but although movement becomes more fluid, cursor speed is drastically reduced and it apparently involves sacrificing the two-finger-tap as right-click. 

I've played around with the options a bit, but can't quite get it to my liking. If anyone could point me in the right directions (which parameters to keep, which ones to delete), I'd be very grateful. I don't need the middle button, just something similar to the default but without the jumpiness. 


```

Section "InputClass"
    Identifier "touchpad catchall"
    Driver "synaptics"
    MatchIsTouchpad "on"
    # This option is recommend on all Linux systems using evdev, but cannot be
    # enabled by default. See the following link for details:
    # http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
    MatchDevicePath "/dev/input/event*"

    Option "FingerLow"              "46"
    Option "FingerHigh"             "46"
    Option "ClickFinger1"           "1"
    Option "ClickFinger2"           "2"
    Option "ClickFinger3"           "3"
    Option "TapButton1"             "1"
    Option "TapButton2"             "3"
    Option "TapButton3"             "2"
    Option "AreaBottomEdge"         "85%"
    Option "SoftButtonAreas"        "60% 0 85% 0 40% 60% 85% 0" # Btn2 LRTB - Btn3 LRTB
    Option "EmulateMidButtonTime"   "75"
EndSection
```

---

### Post by Allan_Lasrado on 2015-02-24
Hey,

I played with the above code and found the code below, which solved my problem. Let me know if it does for you.

```

Section "InputClass"
    Identifier "touchpad catchall"
    Driver "synaptics"
    MatchIsTouchpad "on"
    # This option is recommend on all Linux systems using evdev, but cannot be
    # enabled by default. See the following link for details:
    # [http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html](http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html)
    MatchDevicePath "/dev/input/event*"

    Option "FingerLow"              "46"
    Option "FingerHigh"             "46"
    Option "ClickFinger1"           "1"
    Option "ClickFinger2"           "2"
    Option "TapButton1"             "1"
    Option "TapButton2"             "3"
EndSection

```

---

### Post by kuckunniwi on 2015-02-25
Thanks, Allan. I tried the options you mentioned, and everything works (single-tap, double-tap for right-click, two-finger scrolling--both vertical & horizontal). General mouse movement is more fluid and precise, making it easier, for example, to click on a precise location on the time-tracker-bar in vlc's. It's a bit jumpy on longer movements, for some reason (lag?), but much more usable than it was before (default system settings).80

I was wondering if you (or anyone else who happens to stop by here) know the difference between editing 50-synaptiks.conf and 80xpinput, as suggested [here]("http://ossnotebook.blogspot.co.uk/2014/05/ubuntugnome-running-on-yoga-pro-2.html"). 

Cheers!

---

### Post by faure212 on 2015-03-04
I followed your example on my Yoga 2 Pro, and it really did seem to tame the unruly touchpad.  However, it seems that I lost the right-click functionality.  In the file I created I used only the code snippet that Allan_Lasrado provided.  Was I supposed to do something else (insert his code into the existing 50-synaptics-conf file)?
Also, the 50-synaptics.conf file says to copy and rename it to /etc/X11/xorg.conf.d/  Can I give it any name?   
Any help will be appreciated-- I could not use the Touchpad without this fix.

---

### Post by faure212 on 2015-03-06
Once I edited the file and saved it under xorg.conf.dfirst in /etc/X11/xorg.conf.d things have improved, but the touchpad is still a bit touchy, especially when I raise my finger off the touchpad-- the cursor still moves, and often activates a neighboring item, not the one I meant.  Which parameter in this file can make it less spastic?
Thanks

---

### Post by kuckunniwi on 2015-03-09
> **faure212 said:**
> Once I edited the file and saved it under xorg.conf.dfirst in /etc/X11/xorg.conf.d things have improved, but the touchpad is still a bit touchy, especially when I raise my finger off the touchpad-- the cursor still moves, and often activates a neighboring item, not the one I meant.  Which parameter in this file can make it less spastic?
Thanks

Same here. I just tried Kubuntu 15.04 Beta1, though, and the touchpad works like a charm. I figure I can hold up 'til late April, upgrade and save myself the messing around, which causes boot problems when I get a parameter wrong (boot into a LiveCD, delete modified file, etc.).

In any case, if you do modify anything, I suggest you save a backup of your last working config first. Open 50-synaptic.conf for editing, for instance, Save as, and save it as 50-synaptic.conf.backup, then save as 50-synaptik.conf again and make any changes ;)

---

### Post by faure212 on 2015-03-10
Thanks-- I am religious about saving.. ;-)  Do I have to use KDE or will gnome or Unity work too?  I have deserted KDE long ago since it was so demanding on the graphics.  The touchpad and sound problems are the main reasons I am not currently using ubuntu on my Yoga 2 Pro.

---

### Post by kuckunniwi on 2015-03-11
The touchpad can be a bit buggy, I'll grant that much, but I still prefer it over how it works under Win8. No double-finger tap to right-click, so I had to install an extra plugin which creates conflicts with two-finger scrolling. And, of course, no code can be edited manually to change the way it works. I'm sure if I had the time and patience, I could get it running smoothly in (K)Ubuntu. In any case, I like the fact that in the Linux world, we're all treated like adults, and given the unlimited ability to mess around with anything we please on our system :D   

I reckon the touchpad issues will have been addressed in Ubuntu 15.04 as well. Try burning a copy of 15.04 Beta 1 (download [here]("https://wiki.ubuntu.com/VividVervet/Beta1/UbuntuGNOME")) onto a CD or pendrive and booting a live session. Being a beta, development of new features will have halted and all work from here forth will be focused on bug-fixing and stability, so in terms of the touchpad, it should be a fairly decent indicator of how it'll work in the final release, in a little over a month.

What audio issues are you referring to? I've had nothing of that kind. The only issue I do have sometimes has to do with no audio coming out of the laptop speakers; if I plug in headphones/external speakers, there's audio. I believe this is more of a hardware issue (3.5 mm connector), there are tons of instances of it on Lenovo forums... :(   It only does it to me every now and then though, and is never really an issue for me since I don't use the built-in speakers anyway. 

The KDE vs Unity dilemma is a subjective matter. If you want something really lightweight on your system, give Xubuntu or Lubuntu a shot. Otherwise, maybe Ubuntu MATE (based on the old gnome 2) would work well too.

---

### Post by faure212 on 2015-03-11
I have been using Lubuntu for years and loved it, although they never heard of HiDPI... The sound issues have to do with sound appearing reliably ONLY on the earphone, but not on the speakers.  Sometimes closing the lid and reopening it brings it back (which means it is not the 3.5 mm socket), but not every time.  I  would still be using ubuntu if I could get the touchpad to behave, but most of the time it is too spastic-- lifting my finger moves the cursor... ;-(
I'll give 15.04 a try.  Stay tuned.

---

### Post by faure212 on 2015-03-15
I have just been trying cinnamon, and I love it.  However, the touchpad on my Yoga 2 Pro is still nearly unusuable for selecting a tiny target on my HiDPI gorgeous screen.  Everything else seems to work, so I would dearly love to make the touchpad less jumpy, but I do not know how.  There might be a synclient parameter to do it, but I don't know what it is.

---

### Post by kuckunniwi on 2015-05-31
What distro are you running cinnamon in? It's getting a lot of attention, and I know of tons of happy users. How's well is Hidpi being handled?

As a KDE fan, I recently did a fresh install of Kubuntu 15.04. The touchpad works SMOOTH AND FLAWLESSLY, but as for the rest, a very buggy experience, so it looks like I'll be reverting back to good old Trusty. What I *was* able to learn/rescue from the 15.04 is the touchpad configuration. I'll paste the configuration of 50-synpatics.conf used in Vivid and try it back in Trusty to see how well it works. In case you're interested, here it goes:

```
# Example xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# DO NOT EDIT THIS FILE, your distribution will likely overwrite
# it when updating. Copy (and rename) this file into
# /etc/X11/xorg.conf.d first.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"
EndSection

Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection

# This option enables the bottom right corner to be a right button on clickpads
# and the right and middle top areas to be right / middle buttons on clickpads
# with a top button area.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
        Option "SecondarySoftButtonAreas" "58% 0 0 15% 42% 58% 0 15%"
EndSection

# This option disables software buttons on Apple touchpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection
```

---

