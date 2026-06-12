---
title: "desktop interface problems"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by High Mage on 2007-11-02
Hello everyone :), i am quite amazed how fast and good Ubuntu is.

Now for my problems:
i cant see the titles from the windows and i cant type commands of any kind in the terminal..it just shows a white screen when i open it.
I just installed some sound drivers from this site: [http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/#gutsysound](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/#gutsysound)
i followed every instructions from that site but i didnt do anything else from there after reboot since i dont have a terminal to do commands :s

i also changed a variable from the xorg.conf in attempting to change the color depth of linux 
in "Screen" DefaultColorDepth 16 (before it was 24) those were the only changes i did before i rebooted and everything started working bad.

I would name my sound card here but im not even sure myself..if anyone tells me how can i list hardware components it would be great (remember that i dont have anywhere to do any comands :s)

Currently installed linux: Ubuntu 7.10

What i know from the laptop:
Intel core2 duo T7700 2.4 GHz (is intel drivers needed?)
HDD: 160 gb SATA partitioned about 90 gig (swap at 509 mb, root at 10 gig) the rest is still unused
Mem: 2 Gig
NVidia 8600GT 512 mb (im not even sure if the nvidia drivers are working correctly..is there a way i can do that?)

if anyone could help me i would be much appreciated :)

---

### Post by londoner on 2007-11-02
it alos just happened to me? maybe it was the new updates i installed 10 mins ago?

---

### Post by High Mage on 2007-11-02
so u had the same problem with those updates? :s

---

### Post by londoner on 2007-11-02
exactly the same
i rune the advanced desktop settings and exactly the same error you just described

I can't move or resize the windows terminal is white

No wobble or moving of the windows

and i didnt' change drivers just accepted the the new updates

---

### Post by High Mage on 2007-11-02
well you should say what updates did that to you, if you dont know then..i dont know, i hope some Ubuntu guru answers this thread

---

### Post by londoner on 2007-11-02
Can't remember i just pressed the update.

I am rebooting and reinstalling the whole thing I can't get it to work

it a bit of a pain.. 

and now my monitor wont get picked up..

---

### Post by High Mage on 2007-11-02
ok i managed to fix it, linux isnt good if u lower to less then 24 bit depth color.
But since you had that problem from updating i think the way i did it wont make it work for you..but ill tell you anyway

you have to reboot..try writeing down the steps in a papper..
1st you have to reboot and start in "recovery mode" by pressing "ESC" when the countdown begins before Ubuntu starts..
2nd u type cd /etc/X11
3rd sudo nano xorg.conf and try finding the "Screen" Section of that file..this is how i have it:

> Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection


after u make the change press ctrl + X he will ask u if u want to save..u say yes
then for leaving you type sudo reboot and this time let him start normally

hope it helps :)

---

### Post by londoner on 2007-11-02
i found another solution to the white terminal.

i have advanced desktop[ settings and i couldn't see the titlebar 

by some reason the place windows had been disabled when i clicked it everything worked again.

---

