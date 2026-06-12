---
title: "Problems with Ubuntu 11.04 on Asus Eee PC 1005HA"
date: 2011-04-30
forum: Hardware
---

### Post by radioheads on 2011-04-30
Hi everyone, i've just upgraded my Lucid to Natty, and i ran into some problems.

First of all, touchpad enable/disable buttons are not working.

I've got **acpi_osi=Linux** and **acpi_backlight=vendor** added to GRUB_CMDLINE_LINUX_DEFAULT in my /etc/grub/default, but that doesn't help.

I've also written a simple script, that enables/disables touchpad, and added it to /etc/acpi/events/asus-touchpad:

```

#!/bin/bash
#
# list of synaptics device properties http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html#sect4
# list  current synaptics device properties: xinput list-props '"SynPS/2 Synaptics TouchPad"'
#
if xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | grep 0
then
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
else
    xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
fi
exit

```

```

# /etc/acpi/events/asus-touchpad
# This is called when the user presses the touchpad button.

event=hotkey ATKD 00000037
action=/etc/acpi/asus-touchpad.sh

```

if i execute /home/nox/scripts/asus-touchpad.sh directly, it works. but, it doesn't work when pressing a hotkey. btw, keycode was taken from **acpi_listen** output.

I wonder if there's a solution to this problem =)

And one more problem - while restoring after suspend, video output breaks to artifacts, with everything blinking and so on. Even Ctrl+Alt+F1 console blinks with artifacts, so I think, there's a problem with videocard kernel module loading, but i'm not sure =)

I would be very grateful for any replies.
Cheers =)

*UPD:*
Well, after surfing launchpad and a lot of other sites for a whole night, i've discovered, that problem with suspend triggers from **xserver-xorg-video-intel**, which has been already fixed, but hasn't been added to natty-updates yet.

Problem with touchpad Fn buttons was solved with removing **acpi_os=Linux acpi_backlight=vendor** from /etc/default/grub and running update-grub.

So, everything fixed, maybe this thread would be helpful for somebody.

---

### Post by craigtyson on 2011-05-26
Hi I'm having problems with the display on my 1005HA.  1024x768 does not work nor does duel screen.  

The symptoms of trying to use 1024x768 are that the top third of the screen is unusable and the expected additional screen estate does not appear.  With 10.04 to use 1024x768 gave a compressed image on the LCD screen but this allowed use of non re-sizable windows such as Acrobat Print Dialog. 

Dual screen is now only usable at 800x600 clone or 1024x768 as external only.  no other modes work.

With 10.04 all modes worked eg dual screen LCD@1024x600 VGA@1024x768
Clone both @1024x768 etc

Any help greatly appreciated.

---

### Post by karsnen on 2011-05-26
Hello, 

  I am trying to install ubuntu in my netbook

Model Number : ASUS 1015PEM 


PROB : I am trying to install Backtrack into my netbook, but for some reason it did not recognize my layout


BRIEF:
1. tried "guess map"
2. changed the make of the pen drive(4GB) San disk and Kingston
3. Tried 3 diff pen drives on 4 diff machines(inc one desktop)
4. tried GNOME 32 BIT and 64 BIT.
5.tried different types of  keyboard layouts too.
6. Tried a 32 BIT version on a 16 GB pen drive. 

    
When I tried to do with a Ubuntu edition(11.04), I had the same response but
got an error report.

It is as the one below. 
___________________________________________________

Error activating XKB configuration.
It can happen under various circumstances:
 • a bug in libxklavier library
 • a bug in X server (xkbcomp, xmodmap utilities)
 • X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
11001000

If you report this situation as a bug, please include:
 • The result of xprop -root | grep XKB
 • The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


_________________________________________________________________


Thank you,

Karsnen

---

### Post by craigtyson on 2011-05-27
Karsnen

The 1015PEM uses a different processor and chipset so its probably worth having a search first on the forums to see if other 1015 users are havving any issues.  The 1005HA' ar a single core for example while your 1015PEM is dual core.

C

---

### Post by craigtyson on 2011-05-27
My screen resize problem seems to be the same as this thread.  

[http://ubuntuforums.org/showthread.php?p=10870220#post10870220](http://ubuntuforums.org/showthread.php?p=10870220#post10870220)

C

---

