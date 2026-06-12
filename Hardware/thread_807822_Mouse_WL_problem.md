---
title: "Mouse WL problem"
date: 2008-05-26
forum: Hardware
---

### Post by novithor on 2008-05-26
Hi to all i have a Nortek USB wireless mouse  on my laptop with ubuntu, but i can't uderstand why it is not working.

if i do lsusb he saw the mouse 

Bus 003 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

i think i should modify xorg.conf but i don't know how to do it working..

that's actually what i have

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

some one can try to help me?? thanks a lot:KS

---

### Post by novithor on 2008-05-27
up noone had the same problem? tnx

---

