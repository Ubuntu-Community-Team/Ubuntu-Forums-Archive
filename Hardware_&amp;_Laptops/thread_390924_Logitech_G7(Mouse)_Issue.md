---
title: "Logitech G7(Mouse) Issue"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by forfree on 2007-03-22
Ok, I have a Logitech G7, I've added the following to my xorg.conf, I'm trying to get the left and right scroll buttons to work:

```

Section "InputDevice"
        Identifier      "Logitech G7"
        Driver          "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
	Option		"Dev Phys"		"usb-0000:00:10.1-2/input0"
        Option          "Device"                "/dev/input/mice"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5 7 8"
	Option         	"Emulate3Buttons" 	"no"
EndSection

```

Note, the mouse works fine for basic use, but xev doesn't pick up either the left or the right scroll buttons.  Any ideas guys?

---

### Post by matburton on 2007-03-23
I have the same problem with my wired Intelli Mouse Explorer (think its version 4)

The horizontal scroll buttons don't show in xev and after a lot of searching for a solution I gave up.

I know that's not much help but I thought I'd just let you know you're not alone :(

---

### Post by OutrightLie on 2007-04-06
I'm running the latest version of Feisty, and I have the same problem. The left and right scroll buttons do not show up in xev. It would be really nice if we could get some insight on to this.

---

### Post by battleshipterry on 2007-04-25
I have the same have tried the forms for help keep needing to use the backup copy of xorg.conf it crashes on reboot, the info about xorg.conf is throwing me a little.still not scrolling left /right and thumb button does not work.
 _forfree_ you have   (Identifier      "Logitech G7") did you name it that or did it have that name allready? mine does not reconize it as "Logitech G7"



I like Ubuntu just got to work out kinks on my system mouse proublem /BF2 on online and working PDA syncing up all are hopefully soon fixed I used **Mandrake 8.2** wow that was confusion on my part back then. Ubuntu has brought Linux a very long way Thank You all who have contributed.

---

