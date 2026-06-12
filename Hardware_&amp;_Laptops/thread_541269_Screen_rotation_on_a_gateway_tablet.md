---
title: "Screen rotation on a gateway tablet"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by aethermade on 2007-09-02
I have a Gatway cx2620. It's been great to me so far, but I can't get the screen to rotate. It seems like there's some sort of conflict with ATI drivers or chipsets or something. Every time that's mentioned the thread I'm looking at dies. 

```

mac@mactablet:~$ sudo xrandr --query
//...(resolution's not my problem)...
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

```
Doesn't look good, does it?

Here's the relevant part of my xorg.conf:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X600 (RV380)"
	#Driver		"ati"
	Driver 	          "fglrx"	
	BusID		"PCI:1:0:0"	
EndSection

```

Right now I'll take pretty much anything. I don't care if I have to reboot my computer every time I need to change the orientation, I just need some way to get this thing into portrait mode every once in a while. Can anyone help?
**Edit: ** Could I emulate another computer with something like VMware and then rotate that window or that emulated display sideways? That would totally work too.

---

