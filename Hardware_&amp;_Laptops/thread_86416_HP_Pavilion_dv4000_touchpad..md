---
title: "HP Pavilion dv4000 touchpad."
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by Sunnz on 2005-11-05
Has anyone got vertical scrolling working on a dv4000? If so can you please post your xorg.conf here? I tried to look thru other threads but they are rather confusing. (Different laptops and different problems.)

---

### Post by rado_london on 2006-02-08
I have the same problem, but I couldnt find find any solution either.

---

### Post by guano on 2006-02-17
Well, I have a DV4000, with touchpad working. 
Here's the part of my xorg.conf that matters:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver "synaptics"
	Option "AlwaysCore"
	Option "Device" "/dev/input/event2"
	Option "Protocol" "event"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime" "0"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "0"
	Option "MinSpeed" "0.45"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.020"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "0"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
	Option "SHMConfig" "true"
EndSection
```


Just remind something: if you turn your laptop on with a usb mouse plugged in, scrolling will be disbled. turn the laptop on WITHOUT an external mouse, log in (into gnome, kde, whatever) and then plug the mouse.

Hope this helps

---

### Post by guano on 2006-02-17
Hey, if you want it to work no matter if the mouse is plugged in on boot or not, you will have to deal on writing your on udev rules... 

take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=78904&page=5](http://ubuntuforums.org/showthread.php?t=78904&page=5)

cheers

---

### Post by rado_london on 2006-02-17
Hey the entry in the xorg.conf worked. But I have an specific area where i am supposed to use the scroll. Now it is 2 times wider. How can I repai this. 
Thanks

---

### Post by rado_london on 2006-04-07
The scrolling works out of the box in Dapper. Congrats

---

### Post by padovani on 2006-04-07
My situation is strange: the mousepad works and I have edited xorg.conf bu qhen I try [FONT="Courier New"]synclient -h[/FONT]:
[INDENT]  [FONT="Courier New"]  No touchpad found
    Do you use a newer kernel than 2.4?
    Then browse the messages or boot.msg for the hardware info[/FONT]
[/INDENT]
And [FONT="Courier New"]synclient -m 100[/FONT]:
[FONT="Courier New"]    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     0    0   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0[/FONT]
and nothing else...
I would apreciate to have scrolling too... Any sugestions?

Laptop: HP-DV4165US

---

