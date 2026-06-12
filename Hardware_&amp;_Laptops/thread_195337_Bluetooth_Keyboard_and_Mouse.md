---
title: "Bluetooth Keyboard and Mouse"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by rjr1049 on 2006-06-12
Has anyone sucessfully used a Microsoft Bluetooth keyboard and mouse in Dapper?  If so I'd like to know of any probelms you encountered.  Thanks.

---

### Post by x64Jimbo on 2006-06-16
I'm using the MS BT suite right now, but there are a lot of little finnicky things I haven't resolved yet. The good news is that the BT stack in Ubuntu handles the dongle that comes with the MS package quite well and even adds some services that the windows driver claims not to support. A second chunk of good news is that both the keyboard and mouse work just fine when you run sudo hidd -s --search right after punching the little buttons on the bottom of the devices... 
The bad news: but as soon as they disconnect to save battery, you lose the connection for good and you have to run that command again. I have set up a shell script that I can run whenever I get disconnected, but I'm hoping for a more complete solution. 
There is hope. This is linux. Chances are that the solution is already out there, and that if it isn't yet, someone will make it soon.

---

### Post by Dilligaf on 2006-06-16
Change /etc/defaults/bluez-utils to 1 to autoconnect and they will reconnect

---

### Post by nakko on 2006-06-16
[QUOTE=Dilligaf]Change /etc/defaults/bluez-utils to ! to autoconnect and they will reconnect[/QUOTE]

How? My /etc/defaults/bluez-utils has the following lines:
```
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
HIDD_OPTIONS="--connect 00:99:95:01:92:0A --server"
```
However, if my bluetooth keyboard is turned off or goes to sleep, it will not autoconnect. What should I edit or change?

**Update:** It appears that it will reconnect, it just takes it ten seconds or more, not sure why. *However!!*  It's unusable because I get the repeating key problem. Typing "h" once will net me "hhhhhhhhhhh". This does *not occur* if I type `sudo hidd --search` to reconnect. Same distance from my computer, nothing else has changed that I can determine. What is a solution around this..?

---

### Post by boakes on 2006-06-30
[QUOTE=Dilligaf]Change /etc/defaults/bluez-utils to ! to autoconnect and they will reconnect[/QUOTE]Care to clarify that a little?

---

### Post by rjr1049 on 2006-07-02
I finally got the Microsoft BT keyboard and mouse and they were defective.  Replaced them and they seem to work fine but I would be grateful if somebody could post the relevant sections of xorg.conf that seem to allow the mouse and keyboard to work reasonably well.  I can't seem to get the wheel to work on the mouse.  Here is what I am using.

Section "InputDevice"
     Identifier "MSMouse"
     Driver "mouse"
     Option "Protocol" "IMPS/2"
     Option "Device" "/dev/input/mice"
     Option "ZAxisMapping" "4 5"
     Option "Buttons" "5"
     Option "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"MSMouse" "SendCoreEvents"
EndSection

Thanks.

---

### Post by BatteryCell on 2006-07-02
Um I think:
```
Option "Emulate3Buttons" "false"
```
that needs to be true for the wheel to work.

---

### Post by rjr1049 on 2006-07-03
Thanks for the suggestion but I tried it and no joy.

---

### Post by tetsuo316 on 2006-08-27
Can someone who's gotten their keyboard/mouse combo to work elaborate a bit on how they did it?

I'm a total noob as far as linux goes and would love to stop using my old crappy kb/mouse combo and go back to the bluetooth...

Thanks!

---

### Post by bersace on 2006-10-11
Ok, i got it working, at boot time.

I use HIDD_OPTIONS="--server". Seems i had to wait a bit before the mouse works. I don't know if the bt-applet does anything in that.

---

