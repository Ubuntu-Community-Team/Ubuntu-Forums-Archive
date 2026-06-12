---
title: "quake3 and mouse problem"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by catch33 on 2008-02-23
Hi, I'm new in Ubuntu
I'm a quake3 player, I play always with windows because I have an ati card and untill these new ati drivers I was unable to play at a good fps number.
With new drivers I can play in linux and I want to leave from windows. I yet delete windows now:)

But there is a big problem now, I have a config file for the game with different sensibility for every guns, and if I switch to a gun with different sens I see the light of the hardisk for a moment and a very little but bad block of the game (the block its very fast but fastidious).
So with debian I never see this problem, or I dont tested it too much, but when i had a logitech mouse (mx1000) i had same problem also in debian but only with kde (no with gnome), but now I have this problem in ubuntu with the razer lachesis and gnome.

Wath problem is it?
I need help guys :(

this is my xorg.conf

> 
Section "InputDevice"
        Identifier     "Configured Mouse"
        Driver         "mouse"
        Option         "Name" "Razer Lachesis Optical Mouse"
        Option         "CorePointer"
        Option         "Device" "/dev/input/mice"
        Option         "Protocol" "ExplorerPS/2"
        Option         "Buttons" "9"
        Option         "Resolution" "4000"
        Option         "ZAxisMapping" "4 5"
        Option         "ButtonMapping" "1 2 3 6 7 8 9"
        Option         "Emulate3Buttons" "true"
EndSection

thanks

---

### Post by catch33 on 2008-02-24
nothing know:confused:confused:
up:lolflag:

---

### Post by catch33 on 2008-02-24
I try another mouse but same problem
also with no mouse (only touchpad).
I think its a problem from gnome or xorg

---

### Post by konungursvia on 2008-02-24
The new ati drivers are buggy.

---

