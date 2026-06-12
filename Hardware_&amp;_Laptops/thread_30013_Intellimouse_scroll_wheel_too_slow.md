---
title: "Intellimouse scroll wheel too slow"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by toganet on 2005-04-26
Hey all, I finally got my Microsoft wireless intellimouse explorer 2.0 working, and I've got one last little issue that is bugging me.  I'm hoping all the great minds here can lend a hand.

Scrolling works in all the applications I have tried.  However, it is waaay slow -- I have to "fling" the scroll wheel to get it to move at all.  When I boot into windows, I do not have this problem.

I have a feeling that it may have to do with the strange button mapping on this mouse -- the side buttons (back/forward) are 4 & 5, and the scroll wheel seems to be 6,7,8, & 9.  I've used various combinations in xorg,conf, to no avail.

Any suggestions?  Is this a job for xmodmap?  I'm new to fancy mice, so I haven't played too much with xmodmap or imwheel, and would prefer for this to "just work".

---

### Post by 23meg on 2005-04-26
i'm afraid it's probably not specific to your mouse. the default mouse wheel scroll amount setting in Gnome is very low, and [so far i've found no way of adjusting it.](http://www.ubuntuforums.org/showthread.php?t=26137)

---

### Post by toganet on 2005-04-27
[QUOTE=23meg]i'm afraid it's probably not specific to your mouse. the default mouse wheel scroll amount setting in Gnome is very low, and [so far i've found no way of adjusting it.](http://www.ubuntuforums.org/showthread.php?t=26137)[/QUOTE]

Thanks -- I saw that thread and still held hope...

I will continue to investigate, and post here if I find a solution.

---

### Post by toganet on 2005-05-03
Ok, I got it working, so I thought I would post here for the community's future reference.  The only thing not working is horizontal scrolling, which I never use anyway.

First, I followed the Howto available [here.](http://www.ubuntulinux.org/wiki/IntellimouseMousemanBackForwardButtons/view?searchterm=intellimouse) 

Then, I modified the following files as shown, in order to acommodate the 9 buttons on this mouse.

Here is the relevant section of of my xorg.conf file:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
        Option 		"Buttons" 		"9"	
	Option		"ZAxisMapping"		"8 9"
	Option 		"Resolution" 		"100"
  	Option     	"Emulate3Buttons" 	"false"
EndSection
``` 

And here is my xmodmap script:

```
#/bin/bash
xmodmap -e "pointer = 1 2 3 6 7 8 9 4 5"
``` 

Then, I logged out of Gnome and logged back in.  Voila! My mouse is no longer hindering my productivity.

The trick was the correct combination of the input section in xorg.conf and an xmodmap script.

---

### Post by ozPATT on 2006-11-02
i went to the link you mentioned, but I don't see any help there... says page doesnt exist. 

i am not using a microsoft mouse, it is some weird and wonderful other make, but i seem to be suffering the same problem, whereby the scroll works, but really slow. 

it was fine in ubuntu 6.06, i just upgraded to 6.10 today, and since then it has been slow. 

as a web developer, it is going to seriously decresae my productivity tomorrow if i cant fix this :s 

i only have 3 buttons including the scroll wheel, and do not know enough yet about linux commands to fix it, or to adapt what you have written above. does someone know how i might be able to fix this?

Thanks

Patrick

---

