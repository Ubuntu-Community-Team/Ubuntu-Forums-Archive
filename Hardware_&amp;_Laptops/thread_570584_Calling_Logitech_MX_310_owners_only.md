---
title: "Calling Logitech MX 310 owners only"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by rlange on 2007-10-08
After searching pages and pages for info to edit my xorg.conf to make my mouse work correctly  and reconfiguring X numerous times, I am looking to have the mouse section of your xorg.conf  posted here. Other Logitech mouse owners please start your own help thread  as this is for the **MX310** only. This will keep others from having to read about 6 other Logitech mice while trying to get their MX310 working

Thanks
**Edit: Solved here is the edit to xorg.conf:**


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

---

### Post by SFN on 2007-10-21
Here's mine.

Section "InputDevice"
        Identifier      "Logitech USB-PS/2 Optical Mouse"
        Driver          "evdev"
        Option          "Name"          "Logitech USB-PS/2 Optical Mouse"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection

---

### Post by kg1 on 2007-12-11
Just for the record (since there aren't many MX310 specific posts), the following works for me in 7.10

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "Device"        "/dev/input/event2"
        Option          "Name"          "Logitech MX310"
EndSection

```

I also have the following in my .Xmodmap file:

```
xmodmap -e pointer = 1 2 3 4 5 8 9 6 7 10
```

There are a lot of posts on configuring mice, but I found the following one at linuX-gamers.net to be one of the cleanest.

[ http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons&back=HOWTO+INDEX+Hardware")

---

### Post by Kevanx on 2008-04-28
Anyone find that their MX310 extra buttons stop working in Hardy Heron? I just upgraded, and it went very smoothly, except for that. My xorg.conf hasn't changed.

---

### Post by engineson on 2008-04-30
I seem to be having the same issue... I upgraded to 8.04 yesterday and lost browser back-button functionality. I went back and tried different settings in /etc/X11/xorg.conf as I had done when I first got it working but nothing I've tried seems to work... That being said, I have no solution to offer but you're not alone ...

---

### Post by engineson on 2008-05-04
After a few hours of playing... I finally got it to work again... here's an excerpt from my xorg.conf file...

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Name"	"Logitech MX-310"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"7"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"False"
	Option		"ButtonMapping"	"1 2 3" 
EndSection

---

### Post by mikespug on 2008-05-05
For those interested today's updates seem to have solved the issue of the back/forward buttons not working without any editing of the xorg.conf file.  I have an unedited xorg.conf file and have full functionality of the mouse.

---

### Post by GlenboLake on 2008-06-03
My MX310 never worked in 7.04 or 7.10, but my install of 8.04 is completely fresh (i.e. not an upgrade)  The back and forward buttons work just fine in Firefox, but the extent of its customization in xorg.conf is
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```
That is, no settings at all.  Also, back and forward still don't work in Nautilus.  The only thing is, I liked using the extra button right below the scroll wheel; in Windows, I had it recall the last application.  Does anybody know if it's possible to do that or bring up some kind of application switcher with GNOME?  Like being able to Alt-Tab with the mouse without having to go all the way down to the Window List.

---

### Post by Kevanx on 2008-06-21
Mine still didn't work, and everything is fully updated. Working perfectly for me after two steps

1) I used engineson's new InputDevice segment
2) In System > Synaptic Package Manager I added the IMWheel package as per the instructions I found here:
[http://ubuntuforums.org/showthread.php?t=28374&highlight=mx310+logitech](http://ubuntuforums.org/showthread.php?t=28374&highlight=mx310+logitech)

That page has instructions regarding nautilus as well, although they're a bit over my head for the time being.
No tweaking needed, just those two steps and a restart, and it works in Firefox. I suspect step 2 was the only necessary step, based on other people's notes about it working without editing xorg.conf

---

### Post by goathens on 2008-06-24
what about the application switcher button?  the tiny button right in the middle of the mouse?

I want to bind it to compiz "expo" but no matter which button I bind it to (1 through 9), it doesn't use that app-switcher button.

my mouse section in xorg:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

This is in a fresh install of ubuntu 8.04
EDIT: Forgot, my mouse is a USB plugged into a PS/2 adapter.

---

### Post by goathens on 2008-06-26
Aha! I fixed my own problem.

I used a compination of evdev and xmodmap to make things work (in hardy)
I also switched my mouse to USB (i don't know why I was using the ps/2 adapter when I had open usb ports...)

Here's the vital portion of /etc/X11/xorg.conf:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"Device" "/dev/input/event4"
	Option		"Name" "Logitech MX310"
	Option		"CorePointer"
	Option		"Buttons"	"9"
EndSection
```

that **/dev/input/event4** was found by searching the output of terminal command:```
cat /proc/bus/input/devices
``` and looking for my mouse device.

I think evdev is installed by default. Otherwise run in terminal:
```
sudo apt-get install xserver-xorg-input-evdev
```

On my system, it seems that the following is true:
[LIST]
[*]mouse buttons 4 5 are for vertical scrolling (coincidentally these buttons are the scroll-wheel).
[*]mouse buttons 6 7 are for horizontal scrolling (the thumb and pinky buttons...)
[*]mouse buttons 8 9 are for browser back and forward (8 is the application button)
[/LIST]

SO, we want to remap keys 6 7 into 8 9 so that firefox will use them for back/forward instead of horizontal scroll. Xmodmap works great for this.  It seems gdm/kdm don't use xinitrc, and I wanted this to effect all x sessions on my system, so I created the following file:
/etc/X11/Xsession.d/80logitechMX310-xmodmap 
```
# This file is sourced by Xsession(5), not executed.
# The "|| true" is to ensure that the Xsession script does not terminate on error

if [ -x /usr/bin/xmodmap ]; then
	/usr/bin/xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7" || true
fi
```

I kindof fudged the filename and permissions- there were other files in that directory starting with 80, and one of them had xmodmap commands in it for a default trackpad config, so I copied that file to 80logitechMX310-xmodmap and edited that.

Ctrl+Alt+Backspace and DONE.

The end result is that the thumb/pinky work as expected in web browsers (not nautilus) and the application button is accessible as button 6.  By default it is "scroll left" but I bound it to the compiz-fusion expo function.

---

