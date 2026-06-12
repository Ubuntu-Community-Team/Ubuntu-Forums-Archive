---
title: "Xbox 360 Wired Controller driver problems, Ubunti 9.04"
date: 2009-04-22
forum: Hardware
---

### Post by Necis on 2009-04-22
I followed the guide on the wiki for installing the drivers but on the last step were I get it to compile from the makefile, I run into errors. Ive tried over and over and can not get it to work. The guide on the wiki was written for Ubuntu 7.10 so I guess it will not work for 9.04.

*edit*

I also tried the commands:

xinput list
xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0

in xinput list, it doesnt even show the 360 controller. It did show a device called bcm5974, so I figured that might be it, but nope its not.

**edit**

Also im using a Macbook pro 4.1

I guess the 360 wired controller doesnt work with Ubuntu 9.04 =/

---

### Post by ChodeOfDoom on 2009-04-22
hold on-- ur installing it on a 360??  what a waste... next time do it on a PS3 instead... but about the controller, why do you need one??? use a usb keyboard and mouse and ditch the controller, that is unless you are gonna be playin games and usin ubuntu, but as i have never seen this done in real life, i have absolutely no expertise in this area... i mean really... nobody likes the ps3.  what a waste...

---

### Post by tom66 on 2009-04-22
No, the 360 is a PPC type architecture. Ubuntu dropped PPC support a while ago. I think he is trying to install it on a PC.

---

### Post by ChodeOfDoom on 2009-04-22
but still, why in the world would you even need the controller?  it is a waste of his time, if u ask me.

---

### Post by tom66 on 2009-04-22
As a game controller possibly? It would be pretty cool, actually, to play a FPS with an Xbox/PlayStation controller. But anyway, this is getting a bit off topic.

---

### Post by ChodeOfDoom on 2009-04-22
yeah that would be rlly cool... i wonder how much a wired contrller costs.  my sony vaio is connected to my 55 inch panasonic widescreen tv so playing halo would be just like using a 360.  ima go check it out on amazon.

OMFG 30 BUCKS ONLY
WORKS XP sp1 and up + VISTA
I LOVE AND HATE YOU BILL GATES
(i hate windoze)

---

### Post by Necis on 2009-04-23
Im talking about installing the xbox 360 wired controller drivers on ubuntu 9.04 on my macbook pro 4.1 model.

Ive tried everything that every wiki and guide has said but none of it worked. I guess the 360 wired controller wont work on Ubuntu 9.04 currently.

---

### Post by schwally on 2009-04-25
The guy asks for help, and you guys have a discussion about what controller he should use?  I thought this was a forum to help users, not tell them to live with the systems limitations.

Does anyone know how to get the guitar to work on ubuntu?:guitar:

---

### Post by cloud858rk on 2009-04-26
The 360 controller works fine for me out of the box. Tested with ZSNES.

---

### Post by Shwan.c on 2009-04-26
> **Necis said:**
> I followed the guide on the wiki for installing the drivers but on the last step were I get it to compile from the makefile, I run into errors. Ive tried over and over and can not get it to work. The guide on the wiki was written for Ubuntu 7.10 so I guess it will not work for 9.04.

*edit*

I also tried the commands:

xinput list
xinput set-int-prop THATDEVICENUMBER 'Device Enabled' 32 0

in xinput list, it doesnt even show the 360 controller. It did show a device called bcm5974, so I figured that might be it, but nope its not.

**edit**

Also im using a Macbook pro 4.1

I guess the 360 wired controller doesnt work with Ubuntu 9.04 =/

It works fine for me , had a problem with X grabing it , you dont need to install any driver . 
take a look here 
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)   you cant find all you need here , remember skip installing driver. 
you maybe want a fdi file you can find in the link above , 
[http://ubuntuforums.org/archive/index.php/t-982579.html](http://ubuntuforums.org/archive/index.php/t-982579.html)
[https://help.ubuntu.com/community/Joystick_lshal_outputs_done](https://help.ubuntu.com/community/Joystick_lshal_outputs_done)

please always search before asking

---

### Post by Monkey of Rage on 2009-11-10
[https://help.ubuntu.com/community/Xbox360Controller#Updating%20the%20drivers]("https://help.ubuntu.com/community/Xbox360Controller#Updating%20the%20drivers")

I followed all instructions but when it comes to the 'make' funciton, i just get a bunch of errors..

---

