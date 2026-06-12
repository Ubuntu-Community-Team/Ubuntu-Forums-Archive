---
title: "Xbindkeys not picking up key presses"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by mattgaunt on 2008-02-18
Hey everyone

I used to have xbindkeys set up to work with the multimedia keys for play, stop, fast forward and so one.

Well im tryin to set it up on a new ubuntu install but xbindkeys -k isnt picking up the buttons, although some of them are being picked up by ubuntu and doing some sort of command, i.e. calculator button launches the calculator.

Any ideas how to get it working so i know what key code to use in the xbindkeysrc

My keyboard is a wireless logitech keyboard, dont kno the model soz.

Gaunt

---

### Post by Fokawe on 2008-03-01
Mmmmm. Sounds familiar.

This is my first post. I'm a noob to Linux.
Been running Xubuntu for about 3 months, but have just upgraded to Ubuntu 7.10 Gutsy.
Prior to this I have worked with Windows for 15 odd yrs....:redface:

Anyway, I have enjoyed my experience so far with Linux, albeit I have had my fair share of hiccups. It has been a steep learning curve, but I'm a quick learner. :):)

I'm having a hiccup now! I have just been given a Logitech Wireless Keyboard and Mouse Combo as a gift. Keyboard Model No: Y-RJ20

I plugged in the receiver, and, WooHoo!! It works. Well, almost. I have the following 'Special Function' keys:
[LIST=1]
[*]E-Mail
[*]Messenger/SMS
[*]Webcam
[*]iTouch
[*]Search
[*]Shopping
[*]Favourites
[*]My Home
[*]<< Rewind
[*]>> FastForward
[*]Play/Pause
[*]Stop
[*]Mute
[*]Media
[*]And a Volume spin wheel
[*]Plus a small scroll wheel on the left hand side with a 'Go' button
[/LIST]

I've done an good search of the forums and relevant websites but cant seem to find anything suitable like drivers and applications for Linux, for this combo.

Here is my input device list:

[FONT="Arial"][COLOR="Blue"]
fokawe@Fokawe-Home:~$ cat /proc/bus/input/devices
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/virtual/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/virtual/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=046d Product=c505 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=ff1f

I: Bus=0003 Vendor=046d Product=c505 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:10.1-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:10.1/usb2/2-1/2-1:1.1/input/input6
U: Uniq=
H: Handlers=kbd mouse1 event6 
B: EV=20017
B: KEY=ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff 0 2000000 1878 d800d000 1e0000 0 0 0
B: REL=103
B: MSC=10
B: LED=ff00
[/COLOR][/FONT]

So, what do I need to do to get these buttons linked to the correct functions???
My main desire is for the media buttons (<<, >>, >, etc) and the volume wheel, (which is currently non-functional :( ) to work in the main media applications I use (Amarok and Movie Player, mainly)

Any help or pointers would be appreciated from anybody!!!!

---

### Post by ezramorris on 2008-06-09
> **mattgaunt said:**
> Hey everyone

I used to have xbindkeys set up to work with the multimedia keys for play, stop, fast forward and so one.

Well im tryin to set it up on a new ubuntu install but xbindkeys -k isnt picking up the buttons, although some of them are being picked up by ubuntu and doing some sort of command, i.e. calculator button launches the calculator.

Any ideas how to get it working so i know what key code to use in the xbindkeysrc

My keyboard is a wireless logitech keyboard, dont kno the model soz.

Gaunt

Make sure you have a .xbindkeysrc file (even if it's empty) and don't have a .xbindkeysrc.scm file.

Also try using xev to record key presses.

---

