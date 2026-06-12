---
title: "Sony Vaio FZ Ubuntu Linux &amp; Microsoft Bluetooth Mouse. Scrolling not working. Help."
date: 2008-10-01
forum: Hardware
---

### Post by rostovtsev on 2008-10-01
Dear guys,

I am new to Linux and have been trying to make my scrolling in Microsoft Bluetooth Notebook Mouse 5000 work correctly. Besides I also would like to make to work the side button (back button).

I have tried editing xorg.conf but it wasn't successfull. Something I am doing wrong. I don't understand well enouh yet the whole prosseses so it is hard for me to figure out. It has been 2 days already! I have read many threads and tried many solutions but unsuccessuflly.

So here is what in my xorg.conf at the moment:

--------------

Section "InputDevice"
	Identifier "Mouse1"
	Driver "mouse"
	Option "Protocol" "IMPS/2"
	Option "Device" "/dev/input/mouse1"
	Option		"Emulate3Buttons"  "false"
	Option 		"ZAxisMapping" "4 5"
	Option 		"WAxisMapping" "8 9"
        Option      "VertScrollDelta" "6"
EndSection


-------------

Mouse is working but only two buttons and only the wheel for closing the tab window if you click on it. Scrolling and 4 button on the side (go.back.function) doesn't work.

Please help me, I have stuck!

Thank you,

Ilia

P.S. I tried logitech USB mouse it worked and scrolling too, but no side buttons, but for me it is not important.

---

### Post by rostovtsev on 2008-10-02
> **rostovtsev said:**
> 

--------------

Section "InputDevice"
	Identifier "Mouse1"
	Driver "mouse"
	Option "Protocol" "IMPS/2"
	Option "Device" "/dev/input/mouse1"
	Option		"Emulate3Buttons"  "false"
	Option 		"ZAxisMapping" "4 5"
	Option 		"WAxisMapping" "8 9"
        Option      "VertScrollDelta" "6"
EndSection


-------------


Could anyone help me??

---

### Post by maven5 on 2008-10-10
BUMP!

I have exactly the same problem. I have tried many different configurations but none got the horizontal scrolling wheel to work.

Please help.

---

### Post by bigjig on 2008-10-12
Hey, I've got the same problem as well! I am using the MS Bluetooth 5000 notebook mouse. Any of you found a fix for the scrolling and theback btn issue yet?

---

### Post by rostovtsev on 2008-10-13
Nope, I didn't but I have just changed the mouse and now enjoying it even more! I got Logitech VX Nano - great mouse and works find in Ubuntu and Windows ;)

---

### Post by bigjig on 2008-10-14
well thats fair but it defeats the whole purpose of using the bluetooth mouse.
U are blocking one of the USB ports and thats exactly what I don't intend to do.... m sure there must be a silly fix but i haven't come across it yet!

---

### Post by aska786 on 2008-10-14
Earn money for clicking The Ads [sign up]("http://bux.to/?r=aska786") Here

---

### Post by rostovtsev on 2008-10-14
> **bigjig said:**
> well thats fair but it defeats the whole purpose of using the bluetooth mouse.
U are blocking one of the USB ports and thats exactly what I don't intend to do.... m sure there must be a silly fix but i haven't come across it yet!

My friend why do you need these ports all the time? in my case it is alright as it is. so little receiver of vx nano that it is not even seen. these mouse are faster reacting than bluetooth.

---

### Post by bigjig on 2008-10-14
I know what u mean, but u see mate my laptop is a desktop replacement. 
I've got a usb HDD and a cam plugged in, the other one i frequently use for pen drives etc. and its a pain to unplug a device when u want to use another one.

I am quite satisfied with that bluetooth mouse, it serves the purpose right... I am still not giving up on that scroll to function in linux...lol

---

### Post by rostovtsev on 2008-10-14
> **bigjig said:**
> I know what u mean, but u see mate my laptop is a desktop replacement. 
I've got a usb HDD and a cam plugged in, the other one i frequently use for pen drives etc. and its a pain to unplug a device when u want to use another one.

I am quite satisfied with that bluetooth mouse, it serves the purpose right... I am still not giving up on that scroll to function in linux...lol

:) sure it is. if you find solution, post it here.

---

### Post by CrazyDesi on 2008-10-14
This is kind of off topic, but does your Vaio FZ work with Ubuntu otherwise?  I am looking to buy an SR and it has a similar build.

---

### Post by rostovtsev on 2008-10-14
> **CrazyDesi said:**
> This is kind of off topic, but does your Vaio FZ work with Ubuntu otherwise?  I am looking to buy an SR and it has a similar build.

iT WORKS greatly well. even buttons for sound, mute (and play stop I think too) work in my case.

---

### Post by bigjig on 2008-10-14
well, I have a cr42z/r and 2 issues i am not able to fix..

1, webcam - which i kinda know can be fixed but no luck atm.
2, suspend/resume-hibernate - cant seem to get this going for me, not sure if its the ATI drivers, etc....

and ofcourse the bluetooth mouse works but without the scroll and its doin my head in!

---

### Post by CrazyDesi on 2008-10-14
> **bigjig said:**
> well, I have a cr42z/r and 2 issues i am not able to fix..

1, webcam - which i kinda know can be fixed but no luck atm.
2, suspend/resume-hibernate - cant seem to get this going for me, not sure if its the ATI drivers, etc....

and ofcourse the bluetooth mouse works but without the scroll and its doin my head in!

Err that is gonna b ea problem if I can't get my Sr to do that because i have to drag it from class to class and the stupid school I am at has very few power outlets per classroom.  Bigjig have you gotten yours to work?  Also if anyone knows anything about the SR190 with an 3470M graphics card let me know :(.

---

### Post by bigjig on 2008-10-16
problem with webcam sorted!

[http://ubuntuforums.org/showthread.php?t=821343](http://ubuntuforums.org/showthread.php?t=821343)

However the suspend/resume, hibernate and the bluetooth scroll still dont seem to work. I suppose there is a relation between ati proprietary drivers and the suspend problem but it didn't work when i disabled them either.

Bluetooth mouse scroll is a silly thing but can't seem to find a fix for it!

---

### Post by jesseosby on 2008-12-26
> **rostovtsev said:**
> Section "InputDevice"
	Identifier "Mouse1"
	Driver "mouse"
	Option "Protocol" "IMPS/2"
	Option "Device" "/dev/input/mouse1"
	Option		"Emulate3Buttons"  "false"
	Option 		"ZAxisMapping" "4 5"
	Option 		"WAxisMapping" "8 9"
        Option      "VertScrollDelta" "6"
EndSection
I found your post in the process of trying to find a way to get the back button to work.  I can't help you there, but I thought I'd share that I have the same mouse running on Linpus Lite and it works with a pretty similar configuration to yours.  The ZAxisMapping is the relevant setting, I think, and mine is "4 5" too.

Maybe Ubuntu has your physical buttons mapped to different button codes.  Try running "xmodmap -pp" in a terminal window and make sure each physical button number it shows is the same as the button code number.  Here is mine:
--------------
There are 10 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9
       10             10

---

### Post by jesseosby on 2008-12-26
Ok, I now have both the up/down scrolling and the back button working on mine.  Here is the relevant section of my xorg.conf:```
Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "no"
EndSection
```Here are the relevant log entries from my Xorg.0.log file:```
(**) Option "Protocol" "auto"
(**) Option "Device" "/dev/input/mice"
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(**) Mouse0: Device: "/dev/input/mice"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) Mouse0: Setting mouse protocol to "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
```Let me know if there is any more info I can provide to help y'all get yours working!

---

