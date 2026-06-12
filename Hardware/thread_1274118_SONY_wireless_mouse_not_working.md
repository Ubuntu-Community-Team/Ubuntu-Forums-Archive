---
title: "SONY wireless mouse not working"
date: 2009-09-24
forum: Hardware
---

### Post by Dragokazov on 2009-09-24
I have Sony LV2SJ and it came with wireless mouse and keyboard (with touchpad). Keyboard is working well except touchpad and mouse is not working too. I tried lspci, dmesg, lsusb. It gave some text with "Sony RF wireless keyboard, mouse, ..) but mouse still not working.
It is not Bluetooth wireless set, but some "RF". Please help me, how I can get mouse (touchpad - it also showed ALPS in lsusb) working. Thank you! :)

[[IMG]http://img200.imageshack.us/img200/6430/screenshot1gv.th.png[/img]](http://img200.imageshack.us/i/screenshot1gv.png/)
[[IMG]http://img197.imageshack.us/img197/3735/screenshotdo.th.png[/img]](http://img197.imageshack.us/i/screenshotdo.png/)

---

### Post by swoody on 2009-09-24
Dragokazov - Well for starters...

1) Have you had this keyboard/mouse working in the past on this computer? If not, have you tried it on another computer?

2) Have you tried rebooting your computer with the Keyboard/Mouse plugged in?

3) In your BIOS, if there is an option for USB Legacy support, try enabling if it is disabled, and vice versa.

4) Have you tried plugging in the keyboard/mouse to other USB ports, and tried it again?

4) Can you post the output of anything that comes up when you run:
```
dmesg | grep mouse
```
and
```
dmesg | grep USB
```

5) Are the batteries in the mouse fresh? Sometimes when they get low, they won't have enough power to work properly.

Hopefully with a bit more info, we can get you on the right track here :)

---

### Post by Dragokazov on 2009-09-24
1) this keyboard/mouse set is fully working in windows (receiver is built into PC)
2) Receiver built into PC (keyboard woking ouf of the box)
3) above
4) above. I would like to post, but no mouse ;)
5) yes, fresh. In WIN is everything fully working.

EDIT:
I add that SONY VGC-LV2SJ is All in one PC which comes with wireless RF mouse and keyboard with touchpad (ALPS). In Windows is everything fully working. A word ALPS is in configuration in Bluetooth, but mouse/keyboard is RF wireless, so why is ALPS in BT configuration menu?

[[IMG]http://img406.imageshack.us/img406/1489/screenshotrootubuntuhom.th.png[/IMG]](http://img406.imageshack.us/i/screenshotrootubuntuhom.png/) (i have borrowed a USB mouse for a minute to make a screenshot)

---

### Post by swoody on 2009-09-24
Well it seems everything is ok with your keyboard, correct? If Ubuntu recognized your keyboard, but not your mouse, its likely that Ubuntu just didn't properly configure your mouse. It seems like there wouldn't be an issue regarding the RF connecting. Would you be able to run:
```
gksu gedit /etc/X11/xorg.conf
```
and then post the contents of that file here?

---

### Post by Dragokazov on 2009-09-24
On keyboard is a touchpad too, touchpad (and its buttons) is not working but keys on keyboard are working.

---

### Post by Dragokazov on 2009-09-26
Still nothing, i do not know what to try...

---

### Post by Dragokazov on 2009-09-27
Please, i need help :(

---

### Post by Dragokazov on 2009-09-30
So as it seems, no chance to run Ubuntu... with mouse

---

### Post by Dragokazov on 2009-10-02
I heard that in open suse is everything fully working! (it was for 4 year old RF wireless mouse and keyboard with touchpad from SONY, but I think that's a same RF). when I put old 10.3 opensuse LiveCD into DVD-ROM, it shows menu, then i press boot and then the screen with progress bar appears, but nothing more.
Ubuntu is the best, so I need to use Ubuntu :)

---

### Post by Dragokazov on 2009-10-02
I have some news...
I downloaded and booted open suse (newest on their site)
Keyboard is working, touchpad recognizes SCROLLING area so I can scroll, buttons for touchpad are working too, but i can not move with cursor.
Second thing is that buttons and wheel on wireless mouse are working too!! But cursor stays on the same place :(
Please, are these information helpful? Does somebody know how to help me it running in Ubuntu? Thank you a lot! :)

---

### Post by Dragokazov on 2009-10-03
Please, can somebody help? :)

---

### Post by jmircha on 2009-11-15
hi, 

First, im sorry, my english is very bad. I've the same problem that you, with RF Sony mouse on Sony VAIO VGC. I tried solve this problem with Suse, Ubuntu, mandrake, debian, etc, etc, and i didn't found the solution... i edited the xorg.conf too... all!

I think that we must buy a new mouse, maybe a bluetooth mouse.  :-(

---

