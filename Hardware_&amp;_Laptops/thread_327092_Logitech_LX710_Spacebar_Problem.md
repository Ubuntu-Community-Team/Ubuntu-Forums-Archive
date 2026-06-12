---
title: "Logitech LX710 Spacebar Problem"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by spyke01 on 2006-12-28
Hey guys, i just picked up a new wireless keyboard mouse combo for the holidays, and it seemed to work perfectly at first but then i noticed the following:

[LIST=2]
[*]When you press the spacebar it sometimes doesnt pick it up
[*]When you press the spacebar it sometimes adds extra spaces on its own(you can press it, see the first space and then watch as it adds the others on its own)
[/LIST]

Seems like it has to do with debian heres a link to another case: [http://www.unixadmintalk.com/f60/logitech-wireless-keyboard-issues-141918/](http://www.unixadmintalk.com/f60/logitech-wireless-keyboard-issues-141918/)

Does anyone know how to fix this problem?

---

### Post by spyke01 on 2006-12-29
Found a fix seems to be the only one for now. 

**To Fix the Multiple Space Problem**
Open keyboard prefrences
Increase delay for multiple keystrokes
Decrease speed of repeated key

---

### Post by Chicken_Man on 2006-12-29
Don't know whether this may help or not, but when I first installed this same keyboard under winxp 2 days ago, I plugged the receiver straight into a usb slot at the back of my case. I had this exact problem that you're describing but then I decided to try and use the stand that comes with the package and placed it closer near the desktop. This fixed the problem for me and it hasn't reappeared under ubuntu either.

---

### Post by wampirek on 2006-12-30
Hello, 

I'm thinking about buying the same combo (keyb. + mouse), but first I'd like to know: 
1) when you put the USB receiver in USB port and turned on the computer - did Ubuntu find keybord and mouse without any problems, or maybe you had to modify some config files first? 
2) what about multimedia keys on the keyboard? do they work at once? do you have to install some drivers to make them work? 

Sorry if these are simple quetions, but I'm not experienced much in my Ubuntu ;) 

Best Regards, 
Wampirek

---

### Post by spyke01 on 2006-12-30
Hey no prob mate, heres your answers:
1) I had another logitech keyboard and both it and this one picked up fine, i plugged it in, restarted and it worked great, i think you can just plug it in and do the connect buttons and it should also work
2) For the multimedia butons i had to go into: System->Preference->Keyboard Shortcuts and then assign the keys manually, the buttons i dont have working are:
Shuffle
Button Above Rotate
Rotate
Zoom
Function Keys
100%

Other than that all my keys are setup


_**How to Fix Spacebar Problem(Or what seems to be the fix) - From Logitech Support**_
1) Disconnect the receiver from the current port and connect it to a different USB port.
2) Remove the batteries from the keyboard and press keys on the keyboard repeatedly (as if typing) for approximately two minutes. This will clear out the capacitors.
3) Press the Connect button on the receiver and hold it for 10 seconds. This will reset the connection between the devices.
4) Press the Connect button on the mouse.
NOTE: You may need a pencil tip or other small tip to press the connect button.
5) Press the Connect button on the receiver.
6) Insert the batteries back into the keyboard.
7) Press the Connect button on the keyboard.

---

### Post by wampirek on 2006-12-31
Thank you very much! I think in a few days I will buy this combo :) 

Happy New Year! 

Greets, 
Wampirek

---

### Post by wampirek on 2007-02-20
Hi, 

I finally bought this set, but what makes me very angry is that **e** stops to respond very often :-/ It helps to do exactly the same as with spacebar problem, but it helps only for some short time (one day maybe) :( 
Besides it is great, beautifull and so on ;) 

I wish you not to have these problems :) 

Regards, 
Wampirek

---

### Post by Haegin on 2007-08-28
I have just brought this set and it is very very nice. I have the same buttons all set up and they work fine. I tried using showkey to find the keycodes for the buttons that I couldn't get working (view image, rotate image, zoom in, zoom out, scale to 100% and shuffle) but they don't report a key so I doubt it is possible to use these keys. Slight annoyance but they don't sound useful unless you do lots of image editing and it does mean you can pick your keyboard up by the left side.

I also found a guide to using the extra mouse buttons in firefox which I haven't tested yet. Below that guide there is information on using the mouse buttons in other programs.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Activate_side-mouse-buttons_in_FireFox)

---

### Post by Haegin on 2007-09-17
I just recently got fed up of the / key repeating on me so went looking for a proper fix and found a firmware update for the receiver that seems to have fixed it.

Linky:
[http://www.logitech.com/index.cfm/433/147&cl=gb,en?softwareid=658&osid=1](http://www.logitech.com/index.cfm/433/147&cl=gb,en?softwareid=658&osid=1)

Only problem is that you need to update it in Win XP or Vista so either boot that gaming partition like I did or phone a friend.

---

### Post by elloit on 2007-12-27
ya I bought the key board and mouse set a couple of weeks age and had the same problems as you. Spacebar advancing, help windows opening oh lots more, it came to a point where I wanted to take this peice of junk back.
 
My solution: you will find a red connect button on all three components. I pressed the connect button on the receiver which started to blink, then I pressed the connect button on the key board which caused the led to light up for a couple of seconds and then out.
 
wella no more probems, works perfect like a hardwired board. Hopefully this will solve your greiff.
 
chris

---

