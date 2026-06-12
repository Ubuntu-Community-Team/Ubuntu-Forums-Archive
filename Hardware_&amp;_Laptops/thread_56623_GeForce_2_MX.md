---
title: "GeForce 2 MX"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by wolfen on 2005-08-13
I have GeForce 2 MX and it is detected by X.Org during install like Savage card and X.org don't start after this mistake! What should i do? I'm a total newbie in linux!  ;-)

---

### Post by xodeus on 2005-08-13
[QUOTE=wolfen]I have GeForce 2 MX and it is detected by X.Org during install like Savage card and X.org don't start after this mistake! What should i do? I'm a total newbie in linux!  ;-)[/QUOTE]
 I really don't understand..
The card is found during install and identified as a S3 savage card?
That's weird.
Can you try to edit your /etc/X11/xorg.conf and go to the section where it says something about:

...
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"

But instead of my NVIDIA text then your own card and where it says nvidia in my case under driver change this in your case to nv and restart X?
If that works then try to do this steps:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by wolfen on 2005-08-14
Thank you! It works!  :)

---

### Post by xodeus on 2005-08-14
[QUOTE=wolfen]Thank you! It works!  :)[/QUOTE]
 No problem :D
Be welcome to ask again.

---

