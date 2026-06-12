---
title: "built in video driver pavilion 6736"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by gfarcester on 2009-07-11
ok so i am very new to linux the bigest experence i have had with it is at my school where they stop you from doing anything and evrything there making my knowledge minimal for the moment... i have just installed ubuntu on my HP pavilion 6736 desktop and the screen is a little buggy atm i have checked search and not found anything to help me i phoned my father who uses linux {ubuntu} at his work on a regular basis but he cant help me much knows the problem and said to come here so pardon my being a newb but i was wondering if theres any way i could...
 A) find the hardwhere on my box and
 B) if any of you could direct me to the corect drivers i need
 
{additional info}
running on an HP pavilion desktop with intel motherboard {what type i have no clue i think celeron but not sure on that one} using built in video and sound for the machine 

any other info that you may need i am willing to give so long as you give me the way to get it

PS: if this is in the wrong section feal free to move it but send me a PM to where it is if you do as evry time a thred is moved of mine on some other forum it tends to get lost and i cant find it again

---

### Post by QIII on 2009-07-11
Without sending you to the terminal, the easiest thing to do in a graphical environment would be this:

Go to Applications | Add/Remove

In the search box, type "sysinfo" (no quotes)

Select and install it.

You will have a menu selection under Applications | System Tools.

Poke around in that for a bit.  Get back with things like CPU, Graphic Card, Sound Card, amount of memory and the like.

---

### Post by gfarcester on 2009-07-12
ok so when i do this there is a white box that shows up in the middle of the screen and the rest is a translucent gray escape will fix this and i guess quits whatever its trying to do {no details in the box} is there anything i can type in terminal i could type to get this? i have used terminal on my mac i am assuming and hoping it works pritty well the same 
anyways thanks for the help :)

EDIT: i managed to find a forum on the HP site with the specs evrything is stock exept the 512 mb of ram i put in aswell as an eathernet card
LINK: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07170&lc=en&dlc=en&cc=us&lang=en&product=59859](http://h10025.www1.hp.com/ewfrf/wc/document?docname=bph07170&lc=en&dlc=en&cc=us&lang=en&product=59859)

---

### Post by tobiasly on 2009-07-29
> **gfarcester said:**
> ok so when i do this there is a white box that shows up in the middle of the screen and the rest is a translucent gray escape will fix this and i guess quits whatever its trying to do {no details in the box} is there anything i can type in terminal i could type to get this?

That translucent gray with white box is asking you for your password. Ubuntu does that whenever you try to perform an administrative action. Sounds like your screen isn't drawing the box correctly though. So try just typing your password and hitting ENTER.

Or, go to Applications -> Accessories -> Terminal and type "sudo apt-get install sysinfo". It will then ask you for your password.

FWIW, I just installed Ubuntu 9.04 on my dad's Pavilion 6736 and there are some video oddities like the mouse cursor flickering but I haven't seen the problem you describe...

---

