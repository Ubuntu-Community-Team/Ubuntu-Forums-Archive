---
title: "I need hlp getting all buttons to work on MX Revolution Mouse?"
date: 2008-06-23
forum: Hardware
---

### Post by slope on 2008-06-23
I struggle with a MX Revolution mouse and xubuntu 64 bit.I have tried several approaches and browsed forums and googles without me getting it all to work. So having tested numeroous solutions I came across btnx. [http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)

I started over again and besides hickups :) [http://ubuntuforums.org/showthread.php?t=836037](http://ubuntuforums.org/showthread.php?t=836037) I could now use more then two buttons and a wheel. Still not across the finish line because I still neet to get the tiltfunction on topscrollwheel to work. If possible it would be nice to have leftside scroll also working.

Any tips or pointers here?

---

### Post by slope on 2008-06-23
Ok in host os Xubuntu it works just fine now. But my guest os Ubuntu that I run from vmware does not detect the mouse.


It installed fine. But when I run btnx and try to detect buttons only left/right + scroll up/down are detected. If I go to the tab named "revoco" I see an error message:

[COLOR="Navy"]**"A MX Revolution mouse has not been detected. revoco is disabled."**[/COLOR]

Below I have bolded all parts that I have done. Do not know how to check nr 1, and the link seems to not work. The rest is done and ok.


> 
1.Make sure your mouse is recognized as a USB input device. See this part for more info.

**2.Remove any custom udev rules that you have made for the mouse.**

**3.It's possible that some buttons use a different event handler than the mouse itself. You must press each button on your mouse during mouse detection to ensure that all event handlers have been detected.**

**4.You might have incompatible settings in your xorg.conf file (see xorg.conf section). If you are using the evdev driver, you are certain to run into problems.**
[B]
5.If you have mouseemu installed, try removing it.[/B] 

Here is my xorg.conf

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
EndSection

```

What is next for this to work?

The strangest thing is that btnx works just fine in xubuntu hardy my Host OS. Can't see why it should not work in guest os?

---

### Post by tamoneya on 2008-06-23
I just configured my vx with btnx and it was pretty simple.  It also works with the mx though.

[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by slope on 2008-06-23
As you might saw I have the mouse working just fine in Host os xubuntu 64.
The problem is guest os ubuntu. I suspect that it might have something to do with USB radio/bluethoot not being detected correctly. I did a reinstall of btnx then but it did not work. Then I did a complete reinstall od ubuntu but still not working.

Anyone tested [btnx]("http://ubuntuforums.org/showthread.php?t=455656") with Vmware?

---

