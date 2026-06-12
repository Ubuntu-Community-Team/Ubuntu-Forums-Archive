---
title: "Trackpoint scrolling"
date: 2008-04-27
forum: Hardware
---

### Post by dsmorgan6922 on 2008-04-27
I have a Lenoco T61 running Ubunut 8.04 and am having problems with the trackpoint scrolling vertically. I have done a lot of searching on the thinkiwiki website ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_(Hardy_Heron)_on_a_ThinkPad_T61)) and on this forum and everything I have tried changing my xorg file has caused the xserver to crash upon restarting it and I have to reconfigure it (really just restoring a backup). 
I find it odd that I have to do this (it asks for screen driver and dimension information) since I am only changing the mouse section but w/e. 

My current xorg file is the following:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

```

I would be extremely appreciative of any help, not being able to vertically scroll is extremely annoying (this worked in Gusty just fine).

Thanks,
Doug

---

### Post by homeriq5 on 2008-04-27
I was having the same problem on my old sony, and I ended following this guys directions and it solved my problem:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411/comments/17](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411/comments/17)

basically you add a few lines to the modules, serverlayout, and touchpad sections of your xorg.conf file and you're good to go after a reboot.  Hope this helps!

---

### Post by dsmorgan6922 on 2008-04-27
I tried the things suggested and none of them helped :\

---

### Post by k2cl on 2008-04-30
Hi!

I'm having exactly the same problem :( The only difference is that I'm using Thinkpad r61 but except this, everything looks exactly the same. I wasn't able to get trackpoint scrolling working, doesn't matter how many different things I wrote in xorg.conf...
Maybe that whole thing has something to do with new Xorg version, that came with Ubuntu 8.04??? In 7.10 it was really easy - after adding three lines in xorg.conf everything was OK. Now in 8.04 it simply doesn't work.
Next thing I'm going to do is to check xorg documentation... maybe I'll find something there?

---

### Post by dsmorgan6922 on 2008-05-01
If you figure it out let me know! Everything else worked perfectly in this version (more so than 7.10) but this is just a killer since I use the scroll button constantly.

---

### Post by tscholl on 2009-02-04
Trying to get this to work myself with no luck.  Anyone else make any progress with this?

---

### Post by napstr007 on 2009-03-25
lol i have the same problem, r61 no scrolling at all, this really needs to be fixed!!!

---

### Post by bofphile on 2009-04-06
You should try this:
**[http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html]("http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html")**

"Scrolling with the Thinkpad's TrackPoint in Ubuntu 8.10 Intrepid

Ubuntu Intrepid (8.10) switches to evdev for X server input, which has the unfortunate side effect of breaking old EmulateWheel configurations. So scrolling using the middle button + TrackPoint (which I absolutely love) was broken for a while. However, the version of evdev in Intrepid has now caught up and supports these features. Instead of modifying your xorg.conf, create a new file called /etc/hal/fdi/policy/mouse-wheel.fdi with the following contents:

<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>

Same instructions apply for Ubuntu Jaunty (9.04)."

It works with my T500 on Jaunty. ;)

---

### Post by phubai on 2009-04-19
@bofphille

Excellent tip...thanks! Some time ago I had configured the trackpad, middle button to work, and like you, I really preferred that method, but at some point, during some upgrade that disappeared. Now thanks to your explanation I understand why. I now am able to scroll with the middle button and trackpoint again!

openSUSE has enabled that feature by default, but it isn't a very friendly distro for my T42p for some reason. Now I have to try this solution in Fedora and Gentoo.

Thanks!

---

### Post by Sherlock19 on 2009-08-10
for some reason i could not create a file or move one into this destination it said permission denied, can anyone help me with this?

---

### Post by jnie on 2009-11-10
> **Sherlock19 said:**
> for some reason i could not create a file or move one into this destination it said permission denied, can anyone help me with this?

I'm comfortable with a gui, so I did this.

Press [Alt]+[F2]

in that "Run Application" command window write:

gksudo gedit /etc/hal/fdi/policy/mouse-wheel.fdi

And insert the text from above, and the hit [Ctrl]+[S] for save.

*J*

---

### Post by NavBob on 2009-12-17
I just installed Ubuntu 9.1 on my Thinkpad adn was trying to figure out how to get the Trackpoint scroll button to work and found this thread. I followed your advice and it worked like a champ. As a total noob, this is awesome. Nice to know I'm not the only one who had this problem and thanks a million. :)

---

