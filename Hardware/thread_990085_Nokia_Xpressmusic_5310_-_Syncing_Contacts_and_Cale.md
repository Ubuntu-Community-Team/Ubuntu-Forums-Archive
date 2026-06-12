---
title: "Nokia Xpressmusic 5310 - Syncing Contacts and Calendar"
date: 2008-11-22
forum: Hardware
---

### Post by jharbert on 2008-11-22
I am having trouble connecting to the Nokia Xpressmusic 5310 and accessing the calendar (over the USB cable).  I'd like to eventually be able to sync it with evolution.  I can connect to the micro-SD card (for transferring music) just fine by changing the USB connection type on the phone to "Data storage," but I've had no success in accessing the calendar or contact list.  I've tried various configurations of gnokii and wammu.  Any ideas?

---

### Post by jharbert on 2008-11-30
Anyone have any ideas?

---

### Post by video500 on 2008-12-05
Hello,

I tried to connect my 5310 to gnokii 0.6.22. After intall and test some options I got a basic connection to get the contact list. the main problem is that this phone use a normal usb cable, but i can't get no model cable, so I used the more basic setups.

I made a copy of /etc/gnokiirc to my home and rename to .gnokiirc
then I set this values:
model = AT
port = /dev/ttyACM0
connection = serial

I got that port watching dmesg when I connect the phone into pc.

I test with "model=series40" and all kind of connection with no sucess. Most of time get stuck in "setting rts lo low and dtr to low"

This is not the solution, but a start. I think WE need the connection setting for this phone. Also, i din't test "model=5310"

---

