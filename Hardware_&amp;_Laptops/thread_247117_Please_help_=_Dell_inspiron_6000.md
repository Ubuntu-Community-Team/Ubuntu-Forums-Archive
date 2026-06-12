---
title: "Please help = Dell inspiron 6000"
date: 2006-08-30
forum: Hardware &amp; Laptops
---

### Post by londonhelper on 2006-08-30
A friend of mine is using Dell Inspiron 6000 first he cant seem to get any refrence of my bluetooth in the device manager eventhough the led is on,second he cant seem to find any indication of wireless in the system tray and the led light is off, the FN F2 key dosent do anything as well and lastlly his mouse touch pad is very jumpy and slow but the external mouse works fine.
Hope you could help me with this.
Any software i need to install or information you need to help me with this 
thanks

---

### Post by XProgrammer on 2006-08-30
Hi, 

Regarding wireless LED on inspiron 6000, you have to change a file 
( file name  : led ) in wireless device drive folder to 1.. by default it will start with led=0....thats why it wont turned on... Once you modify to 1...led will be on..However on reboot, you got to do the same to turn on the led as the file is removed and created freshly.... I hope there should be a way to on always..

Regards,
Xprogrammer..

---

### Post by londonhelper on 2006-08-30
Thank you - but lets pretent for a second that I do not know where you are meaning this file is located and how to edit it?
could you perhaps give a more step by step guide to doing the led?

as for the stuff working - how do I check ? and how about the other problems
thanks again

---

### Post by londonhelper on 2006-08-31
anyone please?
please help me try get this sorted?
thanks

---

### Post by londonhelper on 2006-09-01
If no one knows out there how to help this issue, could you refer me to a mailing list that could help me out pleasE?
I would like to fully resolve these issues.

many thanks

---

### Post by Optimus Prime on 2006-09-01
I have an Inspiron 6000 and the "Alternate Method" described [here]("http://knowledge76.com/index.php/Wireless_LED_on_Ubuntu") enables the WIFI led to light up appropriately.

Regarding the touchpad, the following is my configuration in /etc/X11/xorg.conf
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```
Using the Ubuntu 6.06.1 the Inspiron 6000's touchpad should function correctly (including the side scroller) with no extra work needed.

---

### Post by quayman on 2006-10-04
Just installed ubuntu 6.06.  How do I configure my wireless card.  I have the 2200.  I have to use my ethernet wire to connect.  What drivers are needed or how to config.  Thanks quayman

---

### Post by quayman on 2006-10-04
Just installed ubuntu 6.06.  How do I configure my wireless card.  I have the 2200.  I have to use my ethernet wire to connect.  What drivers are needed or how to config.   I have the dell 6000.  Thanks quayman

---

### Post by KingArthur10 on 2006-10-04
You shouldn't need any drivers (I have an IPW2200 on an Inspiron 6000, also).  Just go to network in the system/admin menu.  It should show your wireless card there, doubleclick on it and it should have a drop down menu with wifi networks.  Installing network-manager from synaptic will give you an easy to use Wifi monitor in your sys tray.

---

### Post by bigken on 2006-10-04
for the wifi led look [here]("http://www.ubuntuforums.org/showthread.php?t=200017") ;)

---

### Post by Woodyballz on 2006-10-22
huh... it turns out i am having the same problem...

So i just installed ubuntu, it found my drivers for the Intel Wireless 2200BG 
wireless adapter. So then i go to put in my essid and wep then when i try to connect to google it will just hang is there newer drivers or a new program line that i have to enter.... i just really don't know if someone can help me that would be awesome.

---

