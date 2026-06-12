---
title: "After upgrading Dapper to Edgy, my mouse won't work"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by Pizmar on 2007-04-10
Hello there.  I'm not completely positive this is the best forum to place this post in, but I figure that it's at least completely wrong.

So, I upgraded my Dapper Drake to Edgy Eft earlier today.  It went pretty smoothly.  However, one very big problem quickly became evident.  


At the login screen, I noticed the mouse didn't work.  The pointer stayed in the center of the screen, and wouldn't respond to moving the actual mouse.  I logged in, and it was still like that.

I use a Microsoft Wireless IntelliMouse Explorer 2.0.  It is connected through a USB port.  I was always able to use it on Dapper(though the side and tilt button wouldn't work... oh well) but after the upgrade, it doesn't work.

Now, I have a dual boot set up, with Windows XP as the other partition.  The mouse works fine there(so I ruled out the possibility of a coincidental accident).  I was also able to borrow a friend's simple 3 button PS/2 mouse, which worked.  I used it long enough to enable num-pad navigation, so I can mess with linux slightly more easily.




Now, I have tried some things.
-I tried editing the mouse section in xorg.conf.  I changed protocol to "ExplorerPS/2", "PS/2", "usb", "auto", and "IntelliMouse".  One of them actually wouldn't let the GUI load.... forgot which one.  I also tried changing  Device to "dev/bus/usb/etcetera", none of which worked.





Well, Here is the mouse section of my xorg.conf file.  I figure that will be relevant.  If you guys need anything else to help solve this problem, let me know.  Any help with this problem will be rewarded with treasure.


```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```

---

