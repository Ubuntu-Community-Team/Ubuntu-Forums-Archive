---
title: "I want to touch my touchpad...."
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by Tadhg on 2006-02-05
Well, i have a predicament. Second time around installing ubuntu (on this Laptop:Dell Inspiron 2500) First time,touchpad worked wireless didnt. Now wireless works but my touchpad doesnt. Has anyone any ideas on how to go about fixing it? I dont even know where to start. I've dl'd and run tpconfig and it tells me the synaptics drivers are installed. What else can i do?

---

### Post by dustigroove on 2006-02-05
Unfortunately I don't have an answer for you, but I thought I should share that your post title made me shoot coffee out of my nose...

---

### Post by Tadhg on 2006-02-06
heheh. 


Can anyone come to my rescue? I'm getting sick of this mouse.

---

### Post by Chris Tucker on 2006-02-06
id attempt to help you, but my laptop as my thread in this section shows, has taken up acting.. and its pretty good at acting dead. but i can still see it breathing so i know its fixable..
if i get up and running and theres still no response to help you, i'll give it a shot

but with that topic title i dont imagine you'll have a hard time catchng people's attention, i also nearly choked when i saw it.. no coffee here though..

---

### Post by UnrulyGrrl99 on 2006-02-06
Is this a problem in X or in a console/shell environment?
For the console, try running /etc/init.d/gpm start
For problems in Xorg, checkout [https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28touchpad%29]("https://wiki.ubuntu.com/SynapticsTouchpadHowto?highlight=%28touchpad%29")
NOTE: you will be editing "xorg.conf" not "XF86config-4", as is mentioned in this article

---

### Post by Tadhg on 2006-02-06
unfortunately that hasnt fixed  it. No touchpad and no sound are the two things stopping me from loving ubuntu at the moment.

---

### Post by kennethb on 2006-02-06
You likely need to modify our xorg.conf file. Did you have an external mouse hooke-up to your laptop when you installed Ubuntu? Have you modified your xorg.conf file before?

---

### Post by Tadhg on 2006-02-07
I've done both. I originally had a mouse hooked up and than realised it afterwards so reinstalled ubuntu with it out in. No luck. I've edited the xorg.conf file a few times, even taking out every reference to any non-touchpad pointing device, i.e any other mouse.Still no luck. I've also checked the BIOS which seems in orfer too.

It's kinda strange and I'm starting to think that maybe the touchpad is somehow broken , as it worked out of the box last time i installed Ubuntu, which was with the same install cd im using now. Thing is, the touchpad was working with XP which i had installed only a few days ago.Madness.

---

### Post by kennethb on 2006-02-07
This may not help you, given you have already tried tweaking your xorg.conf file. But, here is the "InputDevice" section of my xorg.conf file:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

The Synaptics Touchpad is my touchpad on my laptop. Mine was auto detected when I installed Breezy; however I had to modify my mouse a bit so the scroll wheel would work.

---

### Post by Tadhg on 2006-02-07
Haha. I win.It's fixed.


Before i went back to Ubuntu i decided to try fedora 4. I downloaded the wrong iso though and ended up with a dvd image. I dont have a DVD drive on this laptop. So i decided to swap the HD with the one in my other laptop that has a dvd drive, install it and than swap them back. Great i thought. Well, after installation, hardly anything worked (including the touchpad and sound) so i said fup that and tried ubuntu and came to my problems. Thing i didn't notice (until now) was that i had disconnected one of the ribbon cables on my sub-laptop adventure. This is why the touchpad and sounds wasnt working. So went back and reconnected everything and all is well finally!


Anyway,thanks for all the help everyone.

---

