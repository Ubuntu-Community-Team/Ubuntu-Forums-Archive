---
title: "Bluetooth"
date: 2014-05-22
forum: Hardware
---

### Post by cybuss on 2014-05-22
Hello im having problems connecting my ps3 bluetooth,
i got it to work last night turned it off went to bed no changes made woke up turn on the laptop and bluetooth headset and it connects pairs but i cant get sound out of it,

when i look into the pulseaudio pannel it says its unplugged


i can detect it in terminal and everything heres some codes i pasted in

:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

:~$ dmesg | grep tooth
[    2.222085] usb 1-1.1: Product: Bluetooth USB Host Controller
[   14.967157] Bluetooth: Core ver 2.17
[   14.967180] Bluetooth: HCI device and connection manager initialized
[   14.967188] Bluetooth: HCI socket layer initialized
[   14.967191] Bluetooth: L2CAP socket layer initialized
[   14.967195] Bluetooth: SCO socket layer initialized
[   19.043337] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.043341] Bluetooth: BNEP filters: protocol multicast
[   19.043347] Bluetooth: BNEP socket layer initialized
[   19.047711] Bluetooth: RFCOMM TTY layer initialized
[   19.047719] Bluetooth: RFCOMM socket layer initialized
[   19.047723] Bluetooth: RFCOMM ver 1.11
[   20.588388] usb 1-1.1: Product: Bluetooth USB Host Controller
[ 2725.583091] usb 1-1.1: Product: Bluetooth USB Host Controller
[ 2730.952345] usb 1-1.1: Product: Bluetooth USB Host Controller
[ 3209.728792] usb 1-1.1: Product: Bluetooth USB Host Controller
[ 3219.434903] indicator-bluet[2120]: segfault at 0 ip 000000000040d880 sp 00007fff6d508450 error 4 in indicator-bluetooth-service[400000+2b000]
[ 3243.942166] usb 1-1.1: Product: Bluetooth USB Host Controller

 uname -r
3.13.0-24-generic

as you can see theres a error in the third code. 
any help is much appreciated

---

### Post by cybuss on 2014-05-22
Also when i run this 

pactl load-module module-alsa-sink device=btheadset
pactl load-module module-alsa-source device=btheadset

all i get is

Failure: Module initialization failed
Failure: Module initialization failed

also when i connect to the bluetooth the bluetooth icon in the toolbar is just a B no background with a lock

---

### Post by cybuss on 2014-05-22
alright i got the problem fixed by removeing blueman bluetooth manager
now a new problem creeps from the shadows

i hear crackling and popping sounds in the background lol

---

### Post by cybuss on 2014-05-22
ok i uninstalled pulse audio.
that did not solve the crackling sound and the default system recognizes my bluetooth now

before i uninstalled pulse i reearched and most poeple was having crackling sounds with it. i tryed the solutions before i uninstalled
so its not pulse

---

### Post by cybuss on 2014-05-22
alright when i uninstalled pulse it removed unity control center with it, so i reinstaled unity control center and it brought back pulse audio and now i cant get sound from the headset now. back to square 1

---

### Post by cybuss on 2014-05-22
is it possible to remove pulse and keep unity control center?

i believe this is related

[http://ubuntu-bluetooth.gmang.org/2014-April/014758.html](http://ubuntu-bluetooth.gmang.org/2014-April/014758.html)

---

