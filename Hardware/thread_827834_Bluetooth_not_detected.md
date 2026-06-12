---
title: "Bluetooth not detected"
date: 2008-06-13
forum: Hardware
---

### Post by harunoyo on 2008-06-13
I have a problem with bluetooth not working on my Lenovo X60 laptop. I've installed all the relevant packages (bluez-* and bluetooth, etc) but I still get the same basic problem: my bluetooth adapter doesn't seem to show up. Could I have it disabled somewhere? Here is the output of some basic commands:

$ sudo /etc/init.d/bluetooth restart 
 * Restarting bluetooth                         [ OK ] 

$ sudo hciconfig
< no output >

$ sudo hciconfig hci0 up
Can't get device info: No such device

$ sudo hciconfig hci0 restart
Can't get device info: No such device

$ lsmod | grep blue
bluetooth              67748  4 rfcomm,l2cap

$ sudo hcitool scan
Device is not available: No such device

$ sudo hcitool dev
Devices:

I don't have the wireless switch set to off (it controls both Bluetooth and wifi, and I'm connecting through wireless internet).

thanks!

---

### Post by ectospasm on 2008-06-13
I'm having the same problem with my Broadcom-based Rocketfish Bluetooth dongle.  It marginally works, the keyboard works, and the mouse works through it.  But unless I get the Bluetooth stack fully involved, the scroll wheel on the mouse doesn't work.  I know the dongle works (and creates /dev/hci0 properly) on my aging POS Thinkpad R32.  This Compaq Presario works great otherwise...

---

### Post by raymondvillain on 2008-06-18
Am using a rocketfish bluetooth mouse and keyboard.  The mouse scroll wheel does not work.  If I query the system from a terminal window, I get exactly the responses shown in the first post in this thread, by harunoyo.

---

### Post by ectospasm on 2008-06-20
I've given up on that Presario, it has other issues I was unaware of when I posted last.  I tried upgrading the BIOS to no avail, it actually made the system much more unstable, where USB refused to work, and more than half the time it would fail to boot at all at various stages of boot.

Well, that's what I get for trying to be cheap and using a computer my roommate found at a house he was working on.

---

### Post by jcam on 2010-02-08
hi guys,

sorry to digg this old thread but recently i had the same problem with my LG E50, for me it was has simple has Fn + F1 ~ F12 (in my case is F11)

i also don't have any indication or switch to turn on the bluetooth, but since the bluetooth switch in my other laptop is Fn + F4 so wy shouldn't i try some combinations? and voila, it worked.

i hope that works for you guys.

ps: just wait a few seconds before each try and focus your site on the appearance of an hypothetical bluetooth icon in the notification area.

---

