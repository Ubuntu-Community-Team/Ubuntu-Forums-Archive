---
title: "Jumpy microsoft wireless mouse"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by stuart.crouch on 2006-10-25
Im hoping someone will know how to fix this problem I'm having with the microsoft wireless mouse. 

One in ten times that I boot into linux the mouse will have this issue where it jumps about 90 pixels down and 90 pixels to the left.  The jump seems to happen after having moved the mouse about 300 pixels across the screen (in any direction), and it always jumps the same distance relative to its last location.

It did it when I tried Warty, and it currently does it in Breezy.  It doesnt do it in SuSE but SuSE doesnt plug and play very well with my soundcard, and I find it has less apps and Im not a fan of its application installer (and theres more support on the web for ubuntu).  It also doesnt go wrong in windows, but then if M$ stuff didnt work with M$ stuff I'd be irate (or in hysterics).

Its not been the biggest issue for me, as linux reboots like grease lightening on my PC (if it booted at the speed my windows partition does I'd be screaming by now), and usually solves the problem, but I'd like to solve the root issue.  Id rather not buy a new mouse as it came as a bundle with the microsoft comfort keyboard so there is just one reciever.

---

### Post by John.Michael.Kane on 2006-10-25
Have you tried Dapper 6.06.1 ?

Also Is the mouse configured correctly under xorg ?

Are you using new batteries?

---

### Post by stuart.crouch on 2006-10-25
6.06.1? I didnt know there was one. How can I tell what version Im on?  How do I get it if Im not on it?  Can I just upgrade or do I need to burn another cd?

Im not sure what Im looking for in the xorg.conf - Here is the mouse section

```

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

```

The batteries were changed just over a month ago, the problem has occured both before and after :(

---

### Post by stuart.crouch on 2006-10-27
bump? 

Tried the edgy live cd. A useless test as neither normal or safe mode graphics would work on this PC :(  Odd, coz dapper worked in safe mode :)

---

