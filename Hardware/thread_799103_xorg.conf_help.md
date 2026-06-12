---
title: "xorg.conf help"
date: 2008-05-18
forum: Hardware
---

### Post by evilnone on 2008-05-18
Ok first heres the original problem:
 
basically whenever I go to hold the left mouse button down (ie to highlight text OR move windows) its like it is doubleclicking after a few seconds... so I can highlight like for 1 second or move a window for one second then its like it starts doubleclicking... is this a known problem?
 
 not sure what else is needed but here is my model number and some pc specs...
 
 m8120n (hp cp model number)
 mouse says model number 5189URF
 
 p4 quad 2.4ghz 
 3gb ram
 

I have had someone say I need to edit xorg.conf to make my mouse work.. but I dont know what I am doing... can someone please help me?  I dont know what to edit it to...

here is what I THINK i need to edit... ```

# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier	"Mouse1"
    Driver	"mouse"
    Option	"Device"	"/dev/psaux"
EndSection
```

---

### Post by teaker1s on 2008-05-18
I have a hp 5188-6230 rev b and it has same issue, it's the mouse not ubuntu as a different mouse it's perfect. it my be worth 
```
lspci -v
```
or 
```
lsusb
``` to see the real vendor and product id

---

