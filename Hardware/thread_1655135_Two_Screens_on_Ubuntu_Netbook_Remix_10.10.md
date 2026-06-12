---
title: "Two Screens on Ubuntu Netbook Remix 10.10"
date: 2010-12-29
forum: Hardware
---

### Post by crowverte on 2010-12-29
I recently installed Ubuntu Netbook Remix 10.10 on an Asus Eee PC 1015 series netbook. Now, I'm trying to use a 20" Gateway monitor with the netbook. When I plug the VGA cable into the netbook and click "detect monitors" in the monitor settings the monitor settings window flashes continuously on both screens and the app launcher disappears. Is there a way to fix this?

---

### Post by SnickerSnack on 2010-12-29
I use xrandr to handle external displays on my laptop.  This thread has a lot of good info: [http://ubuntuforums.org/showthread.php?t=1527703&highlight=xfce+dual+monitor](http://ubuntuforums.org/showthread.php?t=1527703&highlight=xfce+dual+monitor) (especially some of the links therein).  It can be a bit of a hassle to figure out which commands you need, but once you do, you can make some shortcuts/buttons/scripts (whatever is convenient in UNR).

I may be able to help with more specific questions if you choose to try doing this with xrandr.  For now, here is the command I use to turn on an external monitor to the left of my laptop:

xrandr --output VGA1 --left-of LVDS1 --mode 1024x768

and then to turn it off:

xrandr --output VGA1 --off

---

### Post by crowverte on 2010-12-29
I tried to run xrandr and it connected the second monitor the the problem with the flashing windows and missing app launcher persisted.
In fact, it automatically detects the second screen when the VGA connector is plugged into the netbook.

I'm extremely new at this and I really appreciate your help.

---

### Post by SnickerSnack on 2011-01-02
It could be a video driver problem.  I don't know much about video drivers.

---

### Post by regebro on 2011-03-06
I have the exact same problem on a Samsung N150.

Although xrandr is cool and always is good in an emergency, I really would want this to work properly.

Update: xrandr has the same problem if run without parameters. Specifying a smaller size on the external screen worked, but even then using xrandr to turn off and on the external screen could cause blinking or black screens forcing a hard reboot via the power button.

I did find a workaround:

Boot the machine with the external screen on. Ubuntu will default to mirroring the screens with 800x600 resolution. You can then go into the monitor console and change the resolutions to 1024x600 (netbook) and 1024x768 (external) with no problems. Changing the external laptop to a larger (1650x1024) resolution will at this point cause the same problem, but now it will revert to the previous setting after 30 seconds.

This does indeed look like a driver bug.

---

### Post by PandaPandaPanda on 2011-06-23
I experienced this problem on Samsung N150 Plus, but accidentally found a workaround, which requires no rebooting.

1) Laptop set to 1024x600 as standard
2) Connect external monitor (mine is 1280x1024), and open Monitor preferences
3) Set external monitor to 1280x1024, and ensure laptop screen is oriented **below** external screen
4) Apply

Seems rather strange to me that the orientation causes the problem, but if I have the screens oriented next to one another, I have the flashing issue, and when below, I don't.

Hope this helps :)

---

