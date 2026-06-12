---
title: "Need Urgent Help with laptop freaking out"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by jasonpeinko on 2007-09-12
So i installed ubuntu studio on my friends laptop, it boots, get x errors, and go to text login and then so i login and about every 60 seconds an error saying bcm43xx: error: microcode "bcm43xx)microcode5.fw" not available or load failed.

what do i need to do to fix this error and get x working?:confused:

---

### Post by mrsteveman1 on 2007-09-13
My guess is that the bcm43xx module is loaded and the firmware isn't present or in the right place at the moment. For starters if you can type commands, type "sudo rmmod bcm43xx" 


This should fix it for the moment but you will have to either install the firmware or blacklist the module if it keeps happening.  You will need to connect this laptop to a wired network and get that working, then install the firmware you need.

This page should help you get it working. 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty")



If in the end you still have a problem you will want to blacklist that module temporarily:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by mrsteveman1 on 2007-09-13
Once you have the bcm43xx problem fixed or disabled, you will have to post the Xorg error message if you see one so that someone can help you get that fixed, it is likely an error related to drivers.

---

