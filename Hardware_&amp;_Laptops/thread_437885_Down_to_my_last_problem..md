---
title: "Down to my last problem."
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by DNSBubba on 2007-05-09
Okay, I'm down to my last problem with my new Ubuntu install (At least, the last one I know of. :) )

I'm using a MS Laser Mouse 6000, and while the system sees all the buttons on the mouse and they all do something, depending on what app I'm in, they do the wrong thing (Note - This does not include the two primary buttons, or the scroll wheel. They are doing just what they should.)

For instance, in Firefox, clicking the left side button is the same as clicking the left primary button, and clicking the right side button is the same as clicking the right primary button (The context menu pop's open).

So I'm sure I'm just down to a configuration issue somewhere, but I just don't know where.

Any help is appreciated  and welcome.

Thanks in advance.

---

### Post by Spartan.II.117 on 2007-05-13
Here is the relevant section from my xorg.conf file, let me know if this helps.

section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
        Option          "Buttons" "9"
        Option          "ButtonMapping" "1 2 3 6 7 8 9"
EndSection

---

### Post by DNSBubba on 2007-05-14
Sorry for the delayed reply.

I changed my xorg.conf to reflect yours, but unfortunately it didn't work. Honestly, it's something that I can live with, as everything else (Printer, USB, Beryl) is working just fine.

Thanks for trying to help.

---

### Post by Spartan.II.117 on 2007-05-14
try this page, it should help.

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

let me know if this helps!

---

### Post by DNSBubba on 2007-05-14
BINGO!!!!!

One of the solutions on there worked like a charm!!! Thank you so much. Now, everything on this system is working just as it should, and I am 100% MS free!!! :guitar:

---

