---
title: "[mouse]Wireless mouse doens connect to ubuntu 8.04 on macbook"
date: 2008-07-18
forum: Hardware
---

### Post by cyril_hoi on 2008-07-18
Hello,

I have installed Ubuntu 8.04 on my 2nd gen MacBook 2 days ago.
Well I looked over the internet for drivers and I already found the wireless internet driver. My bluetooth worked already when I installed Ubuntu. Well the problem is, is that I have a V470 Cordless Laser Mouser from logitech. Its a bluetooth mouse. But when I go to bluetooth>browse device, then he see's the mouse, but when I want to connect to it, it says:

Couldn't display "obex://[00:07:61:BA:94:60]/".
Error: Host down
Please select another viewer and try again.

can someone help me please?

---

### Post by NilsE on 2008-07-18
The way you are trying to connect it is for file transfer not input devices.

Try the following:

Right click on the bluetooth icon

Select preferences

Go to the Services tab

Make sure Input service is checked

Single click Input service

Single click the add button

Check show all devices

Make your mouse discoverable by pressing the reset button or turning it off and on.  It will eventually show up in that window then you can select it and connect.

---

### Post by cyril_hoi on 2008-07-18
he man! thank you very much!

---

### Post by NilsE on 2008-07-18
I may have the steps out of sequence but the add button should show up as soon as you click on the input service line (not the check box).  You need to click directly on the words Input Service to highlight the line then it should show up.

---

