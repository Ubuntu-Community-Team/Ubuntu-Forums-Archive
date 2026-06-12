---
title: "Newbie with old probs"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by Dapo Alla on 2007-10-24
Goodday sirs,i am very new to ubuntu so i satrted with the 5.10 LTS on an IBM 600e think pad,and for sure i have issues,pls i'd have to do  a list of the  issues...
(1.)first,i have the 5.10 LTS and win Xprunnin ,i'd have loved to boot with win Xp,but by defualt my grub had 5 lines,i managed to remove 1 but i'd love to have only two,and XP booting up first.

(2.)I have issues with..
	a. sound(no sound at all),
	b.Infrared(dont know where to find it,
	c.usb mouse(not working well) 
	d.and usb LAN interface (my laptop doesn't have a NIC)

(3.)how do i tweak the OS to run faster on my machine as i have only 128mb RAM installed
4.iheard about wine but i dont know if theres any installation guide for newbies,that has a step by step guide(thas is step 1. do these ,step 2 do these...etc)
5.igot some linux game but dont know how to install them.

Please dont say this fella got a lot of issues,i was wondering if you could make it easy by just making the files i would have to add codes to and sending them to me,(that is Grub file(menulist),Alsa etc)
thanks

---

### Post by Sef on 2007-10-24
1) You need to use [xubuntu]("http://xubuntu.org") because it is made for computers without much memory.  That will take care of your speed problems.  

2) Once you update to Xubuntu, then we will help you with any problems that you have.

---

### Post by Dapo Alla on 2007-10-25
thank you but getting the xubuntu is the biggest challenge,im a nigerian student with no internet access,i was so lucky to have found the ubuntu 5.10 lts from shipit,that is practicaly the only linux i can lay my hands on,and my machine is what i have please if you could help with my list of probs you'd save me a whole world of problems. thank you so much.
Dapo

---

### Post by Sef on 2007-11-17
> a. sound(no sound at all),
b.Infrared(dont know where to find it,
c.usb mouse(not working well)
d.and usb LAN interface (my laptop doesn't have a NIC)

a.) Applications > Accessories > Terminal

cat /proc/asound/cards

copy and post the results here.


c) What exactly is happening with the mouse?

---

