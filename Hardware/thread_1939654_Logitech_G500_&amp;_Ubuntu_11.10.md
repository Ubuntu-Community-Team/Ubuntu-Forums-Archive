---
title: "Logitech G500 &amp; Ubuntu 11.10"
date: 2012-03-12
forum: Hardware
---

### Post by SpindizZzy on 2012-03-12
Hi guys,

I'm trying to get my new G500 working under Ubuntu 11.10. More precisely, I want to map my three thumb buttons to shortcuts in Firefox, namely 'back', 'forward' and 'open new tab'.

I've been messing around with this issue for quite a while now (editing xorg.conf, using xkeybinds, trying to fix it with CCSM,...), but didn't succeed so far ... :(

So I turn to the Pro's :D

Is there a 'quick and dirty way' to fix this issue, or do I really have to add lines to my config-files ? And what would those lines look like then  ???

Thx !!

---

### Post by ajgreeny on 2012-03-12
I am not sure if this will help with your specific needs, but I offer it just in case it works for you with FF back/forward etc etc.  It certainly works for me in nautilus where I can go back and forwards easily with the side buttons of my Trust multi-button Ami-scroll mouse.

Entries to enable forward & backwards navigation in nautilus with mouse buttons.
```
sudo apt-get install xvkbd xbindkeys x11-utils
```
```
xev | grep ', button'
``` Press mouse buttons and note output, eg

state 0x10, button 8, same_screen YES
state 0x10, button 8, same_screen YES
state 0x10, button 9, same_screen YES
state 0x10, button 9, same_screen YES

Back in terminal, we need to create a new file for configuration of xbindkeys.
```
gedit ~/.xbindkeysrc
```
This will load up Gedit to add content to the new file. This file needs to contain the following:

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

Notice the “b:8&#8243; and “b:9&#8243; portions of the text. This is where I configure my mouse buttons. So, if your mouse #buttons are 6 and 7, then you need to change “b:8&#8243; and “b:9&#8243; to “b:6&#8243; and “b:7&#8243;, respectively.

Set xbindkeys to autostart at session start in System->Preferences->Startup Applications, or wherever that is now in 11.10.

I hope it works for you.  I thought mouse buttons had been recognised by FF for some time now with no further action being needed, but perhaps the change to gnome-3 and gtk3 has stopped that happening by default.

---

### Post by SpindizZzy on 2012-03-12
Thx ajgreeny for the quick reply !! Really appreciated ! :p

I'm afraid my 3 thumb buttons don't generate output when i click them while hovering over that square...

All other buttons work just fine though. Do I have to activate these buttons somewhere ? Or tell Ubuntu that my mouse has more buttons ??

My device is however recognised as USB-mouse ...


> lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 007 Device 002: ID 046d:c068 Logitech, Inc. G500 Laser Mouse

---

### Post by ajgreeny on 2012-03-12
> **SpindizZzy said:**
> Thx ajgreeny for the quick reply !! Really appreciated ! :p

I'm afraid my 3 thumb buttons don't generate output when i click them while hovering over that square...

All other buttons work just fine though. Do I have to activate these buttons somewhere ? Or tell Ubuntu that my mouse has more buttons ??

My device is however recognised as USB-mouse ...
Sorry, no idea at all about that.  I just threw in the post in the hope that it might help you.

---

### Post by JoZ3 on 2012-03-13
Try with this - [http://www.bohemianalps.com/blog/2011/gnome-3-activate-overlay-and-more-by-mouse-button/]("http://www.bohemianalps.com/blog/2011/gnome-3-activate-overlay-and-more-by-mouse-button/")

---

