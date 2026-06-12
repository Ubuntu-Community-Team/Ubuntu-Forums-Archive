---
title: "Wacom Intuos 5 Relative Mode Timing and Lift Distance"
date: 2013-02-16
forum: Hardware
---

### Post by Kins on 2013-02-16
Hi, you know how if, when using a regular mouse, you try to scroll really far in one direction?  You run out of physical space on the mousepad right?  So you need to lift the mouse off the pad, and put it back down back where it started.  

In relative mode, you need to mimic this process.  But in my very recent install of Ubuntu, fresh out of the box, a 'timer' takes too long.  In other words, I have to lift the pen off the pad, wait, then put it back down or else something interprets this as a single action and resets the mouse position along with the pen.  It's as if instead of lifting the mouse off the pad, you shook it back and forth.  Can someone provide some advice?

Also, the pen responds a very far distance away and xsetwacom <device> CursorProximity gives "Property 'Wacom Proximity Threshold' does not exist on device."  Is there any alternative to this property?

The Wacom capture doesn't seem to have these problems on the same install.

xsetwacom --version returns 0.17.0

Thanks guys, I'm very grateful for Ubuntu's existence.

---

### Post by Favux on 2013-02-16
Hi Kins,

Welcome to Ubuntu forums!


I really don't understand what you are talking about to be honest.

The stylus is in Absolute mode by default with a graphic tablet.  If you had a Intuos5 touch the touch would be in Relative mode.  You can set the stylus mode to Relative with an **xsetwacom set** command using the Mode parameter.

Cursor in linuxwacom speak refers to the tablet mouse or puck.  So the CursorProx parameter only applies to that, and I don't believe Intuos5's have them.

Does that help?

---

### Post by Kins on 2013-02-16
Hey thanks for the welcome and also for the help :D,

Yeah, I can't really find the proper words to describe what I mean.  It's one of those things where its a lot easier to show than word.  

But that's a good point, I'm using the stylus in relative mode through the appropriate setting on xsetwacom. It wouldn't be applicable in absolute mode since the position on the pad determines the position on the screen.  

The goal is to get the mouse pointer from one side of the screen to the other in relative mode.  If you move too quickly, the pointer 'resets' to the original position.

The general wrist flicking motion is like this I think...

A ========> B ----------> A

Where '=' means the pen is lowered down onto the pad '-' means its lifted.

In the end you want your hand back at A, but you want the virtual pointer to be at B in screen coordinates. (But the pointer follows you all the way back to A)
 
Lowering the 'active' vertical distance may have an affect, since the hand would take longer to travel naturally because it isn't so high in the air at rest.

---

### Post by Favux on 2013-02-16
OK, I think I follow.  You like to use the stylus in Relative mode and have a habitual wrist gesture to reset the stylus position without affecting the pointer location.  It works on your BambooPT because apparently its proximity distance is less than what you are seeing on the Intuos5.

Unfortunately I think you'll just have to retrain your gesture, lifting higher vertically, to break proximity on the Intuos5.  At least at the moment I can't think of a way to change proximity since it is hard coded.  I'll think about it a bit.  If the new gesture is just too awkward you could talk to a dev. on linuxwacom-discuss and see if they have any ideas.

---

### Post by Kins on 2013-02-17
Yeah its something that falls into the category of being re-trainable.  I am doing that as well.

I should clarify one last thing though, I mentioned 'timer' because the pointer does hold momentarily on the screen.  So proximity has been broken and could be detected somewhere.

A ===> B ---> A

The pointer holds at point B when my hand is lifted at '---', but returns when the stylus drops back towards the pad nearly instantaneously.

I tried to save some raw xidump output when I perform the gesture to illustrate.  The X coordinate is the focus though.  The output before the spacing is my hand moving towards B, I included so many lines to hopefully show the speed I'm moving.  Then after the spacing, when my hand drops down, the X coordinate shoots back to the original position.  In very few lines, very quickly.  I think the leftmost column shows a gap in time too, when the pen drops down from out of proximity to back into proximity.

I do appreciate very much the time you've taken already, thank you.

```

9.10115290: Motion: x= +8043 y=+13460 p=   0 tx= -42 ty=  +7 w= -900 
9.10631800: Motion: x= +7912 y=+13433 p=   0 tx= -42 ty=  +8 w= -900 
9.11126089: Motion: x= +7773 y=+13406 p=   0 tx= -43 ty=  +8 w= -900 
9.11606884: Motion: x= +7634 y=+13379 p=   0 tx= -44 ty=  +8 w= -900 
9.12104988: Motion: x= +7491 y=+13358 p=   0 tx= -44 ty=  +8 w= -900 
9.12608886: Motion: x= +7356 y=+13333 p=   0 tx= -45 ty=  +8 w= -900 
9.13066196: Motion: x= +7255 y=+13310 p=   0 tx= -45 ty=  +8 w= -900 
9.13588405: Motion: x= +7156 y=+13279 p=   0 tx= -46 ty=  +8 w= -900 
9.14115000: Motion: x= +7083 y=+13234 p=   0 tx= -46 ty=  +8 w= -900 
9.14578485: Motion: x= +7034 y=+13193 p=   0 tx= -46 ty=  +9 w= -900 
9.15097499: Motion: x= +6989 y=+13152 p=   0 tx= -46 ty=  +9 w= -900 
9.15608692: Motion: x= +6994 y=+13097 p=   0 tx= -46 ty= +10 w= -900 
9.16100001: Motion: x= +7035 y=+13060 p=   0 tx= -47 ty= +10 w= -900 
9.16654396: Motion: x= +7120 y=+13007 p=   0 tx= -47 ty= +10 w= -900 



9.34228587: Motion: x= +8997 y=+13052 p=   0 tx= -47 ty=  +9 w= -900 
9.34713888: Motion: x=+10836 y=+13137 p=   0 tx= -46 ty=  +8 w= -900 
9.35229206: Motion: x=+12615 y=+13224 p=   0 tx= -46 ty=  +8 w= -900 
9.35715103: Motion: x=+14326 y=+13339 p=   0 tx= -46 ty=  +8 w= -900

```

---

### Post by Favux on 2013-02-17
> The pointer holds at point B when my hand is lifted at '---', but returns when the stylus drops back towards the pad nearly instantaneously.
So there are actually two issues.  The increased proximity range and the tablet is not acting like it is in Relative mode.  Even though I'm sure when you do an **xsetwacom get "<stylus device name>" Mode** it is telling you mode is Relative.

The not being in Relative mode despite being set that way sure sounds like a bug to me.  The question becomes is it in xf86-input-wacom or is the GNOME Wacom tablet app. somehow involved?  Because if you look at it in System Settings you see it sets Mode to Absolute and doesn't permit a change to Relative.

Looks like you can test if it is the Wacom app. without disabling it.  You'll probably need to install dconf-editor.
```
sudo apt-get install dconf-editor
```
Then run **dconf-editor** in a terminal.  Navigate to org.gnome.settings-daemon.perpherals.wacom and then the Vendor and Product ID you'd get from **lsusb**.  Should see a key saying "is-absolute" with a checked box.  Uncheck it and see what happens.

The xidump coordinates do show the problem clearly.  Thanks.

---

### Post by Kins on 2013-02-17
> 
Looks like you can test if it is the Wacom app. without disabling it. You'll probably need to install dconf-editor.


I installed dconf-editor and followed the instructions but there wasn't any change in behaviour.  I also gave kde a shot too, by playing around with its version of wacom control under system settings.

> 
So there are actually two issues. The increased proximity range and the tablet is not acting like it is in Relative mode.


Yeah there were two questions, I was hoping a proximity setting could work around the same symptom.  In the end as of now, I guess all it amounts to is slowing relative pointer travel a bit.  I'm really happy it works this well out of the box, much better customization than under Windows.  I'm already getting used to it throughout the duration of these postings ;).

I'm not so sure its resorting to absolute though, since it doesn't return to the same position every time.  I can perform the gesture between any two points in screen coordinates using the same physical position on the pad.  Its like the entire operation gets linked together as if the stylus never left proximity, after the fact.

---

### Post by Favux on 2013-02-17
> 
I'm not so sure its resorting to absolute though, since it doesn't return to the same position every time. I can perform the gesture between any two points in screen coordinates using the same physical position on the pad. Its like the entire operation gets linked together as if the stylus never left proximity, after the fact. 
Hmm.  So it may not be what I was thinking.  I wonder what would happen if you messed with pointer acceleration using xinput commands?
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch#In-driver_Two_Finger_Gestures](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch#In-driver_Two_Finger_Gestures)

Otherwise it appears you need to discuss this with a dev. on linuxwacom-discuss:  [http://sourceforge.net/mail/?group_id=69596&source=navbar](http://sourceforge.net/mail/?group_id=69596&source=navbar)

---

### Post by Kins on 2013-02-18
The acceleration settings help make the pen handle the way I like, but the problem still persists.  Maybe some kind of cutoff would help?

I guess I'll try linuxwacom-discuss after checking what versions of things I have and what's available.  Thanks!

---

