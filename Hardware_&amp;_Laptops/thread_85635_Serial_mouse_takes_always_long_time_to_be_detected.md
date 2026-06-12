---
title: "Serial mouse takes always long time to be detected"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by dtygel on 2005-11-03
Hi all!

   I've just upgraded to Breezy! (not gracefully: had to do a full install after the dist-upgrade from hoary simply failed: it seemed to have something to do with my language support: brazilian portuguese, I don't know).

   I'm liking it really much, except for one problem with my old chap: my serial mouse, connected in ttyS0: it gets detected, but only after a while, EVERYTIME I restart X. Am I missing something in configuration? I've changed the input path in xorg.conf from "input/mice" to "/dev/ttyS0", because before it just didn't work at all. Now it works, but only after an irritating minute moving the mouse like crazy: suddenly, it starts moving normally, during all my session, wihthout any problems.

   Here is my xorg.conf mouse section:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"auto"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

   Can someone give me some light there? :confused:

---

### Post by teaker1s on 2005-11-03
look in wilki (top right of this page) search mouse and manually set up the mouse I'm guessing that until the mouse creates an output-moving it it's not detected

---

### Post by dtygel on 2005-11-04
Hi teaker1s,

    thanks a lot for the hint: I looked at the "SerialMouseHowTo" in the wiki section, and solved my problem: it wasn't the port, but the protocol. I had changed it from imsps2 to "auto", and so it had to detect the protocol everytime I logged in. Now I changed it to, uuuurgh, "Microsoft", and it works immediately. :D 

      Cheers (ubuntu really rocks!),

            daniel

---

