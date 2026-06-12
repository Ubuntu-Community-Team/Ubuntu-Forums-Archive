---
title: "Can't use keyboard and mouse at the same time"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by flakzeus on 2007-05-16
I'm not sure if this is a specific problem to my laptop or what but it is very annoying. I have a MacBook Pro that I've got 7.04 installed on. Whenever I try to move my mouse while hold down a key the mouse stops working. It's as if the keyboard locks the mouse from moving. 

I've tried a USB mouse and a Bluetooth mouse and I get the same thing on both.

Does anyone know how to fix this?

---

### Post by vxbinaca on 2007-11-10
Even though I know thread bumping gets you absolutely nowhere on Ubuntu Forums, I'm also curious as tto the solution as I have a LAN party to go to tomorrow and this problem is going to essentially keep getting my killed and laughed at at this party.

It's really annoying to have to stop running in order to move to either side or shoot because the mouse does not work when using the keyboard.

I'm willing to bet a significant sum of money that this thread will go unanswered and unread, yet remain at the top of Google's search results for the problem I'm having.

---

### Post by xur17 on 2007-11-12
> **vxbinaca said:**
> Even though I know thread bumping gets you absolutely nowhere on Ubuntu Forums, I'm also curious as tto the solution as I have a LAN party to go to tomorrow and this problem is going to essentially keep getting my killed and laughed at at this party.

It's really annoying to have to stop running in order to move to either side or shoot because the mouse does not work when using the keyboard.

I'm willing to bet a significant sum of money that this thread will go unanswered and unread, yet remain at the top of Google's search results for the problem I'm having.

I actually found this same article by a google search.  I am having the same issue, with a logitech mx3100 keyboard/mouse wireless combo.

I also found [this]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/32415") if it is of any interest.

---

### Post by vxbinaca on 2007-11-29
Thats not the issue OP and I are having.

I have a USB keyboard and mose hooked into a Desktop and am still havingthis problem. I still have the problem with PS2 mice and keyboards too.

So Bluetooth really has little to nothing to do with this as the guys keyboard internally in his laptop is a safe bet it isn't Bluetooth.


I guess I'm waiting 4 months for the next version to fix this. In the meantime I'm gameless, as theres is literally nothing on Google (aside from this thread that people uselessly bump with "me too" posts)  on how to fix this or that anyone else is even having this problem that him and I are having.

Not being able to game sucks. Really bad.

---

### Post by gninnes on 2008-04-19
I too am having this problem. At first I thought the problem was a cheap logitech wireless mouse and keyboard combo (maybe only one wireless device can talk at any one time). I then substituted the keyboard for a corded ps2 keyboard. 

This did not fix the problem. I still can't use the mouse and keyboard at the same time. The mouse movement and buttons seems disabled when keyboard buttons are being pressed. 

Very frustrating!

Has anyone found a fix for this yet?

I hope there is a fix in Hardy.

---

### Post by flakzeus on 2008-04-19
There is an option in xorg.conf that needs to be changed to fix this. Unfortunately, I can't remember what it is at the moment. I'll look and see if I can remember what it was.

---

### Post by gninnes on 2008-04-20
Thank you!!!

Any help would be much appreciated.

---

### Post by gninnes on 2008-04-20
Further clarification of my problem:
I noticed that the Shift, ctrl, or alt keys don't stop the mouse working.

All alph-numeric keys, function keys, insert, delete, end page up/down, arrow keys.... they all stop the mouse working.

Does anyone know what is going on here?

I had a look in my xorg.conf. Nothing appeared obviously out of place to me:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
        screen         "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

```

Cheers for any help.
Gerard

---

### Post by gninnes on 2008-04-26
I upgraded to Hardy and the problem is still there. 

I downloaded the live CD of Hardy and the problem does not exist when running live hardy. So that would point to some sort of software issue. 

There must be a config file somewhere that is causing this issue!

Any ideas anyone?

---

### Post by paranic on 2008-04-28
same problem here on mac mini 1.66 and hardy

---

### Post by loopofpoop on 2008-04-28
I could not use the arrow keys and the mouse at the same time because the
arrow keys were moving the mouse cursor around.

To turn this off:

1. System Menu
2. Preferences Menu
3. Select "Assistive Technologies"
4. "Keyboard Accessibility" Button
5. "Mouse Keys" Tab
6. Uncheck "Allow to control the pointer using the keyboard"

This feature was turned on by default when I installed Hardy Heron.
Hope this helps.

---

### Post by gninnes on 2008-04-30
Unfortunately that is not the same issue I am having. 

I can't use any the majority of the keys on the keyboard at the same time as my mouse.

Is there any help out there for this one?

---

### Post by gninnes on 2008-05-09
I did another search on the forums and found this page. Not sure how I missed them the first time.

Give [this ]("http://ubuntuforums.org/showthread.php?t=545244") suggestion a try.

I am about to try it myself, but it sounds promising. 

Good luck with it!

-- EDIT --
This totally fixed my problem!! Ya!:popcorn::-D

---

