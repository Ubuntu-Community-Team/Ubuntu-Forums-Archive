---
title: "Touchpad bug on Acer aspire"
date: 2012-05-23
forum: Hardware
---

### Post by rasmus91 on 2012-05-23
Hello everyone.

i have an acer aspire 5745G. this computer is almost 2 years old by now, and i have had ubuntu 11.04 on it, as well as 11.10 and now 12.04.

I am very, very satisfied with Ubuntu 12.04, once again the guys developing this have not failed to impress me.
there is however, one small thing that haven't seemed to work properly at any point in Ubuntu on this laptop;

sometimes when i boot it, the touchpad works in the login screen, but doesn't work after logging in. if i hit fn+f7 (the button combination to switch the touchpad on and off) Ubuntu registers it, and shows the icon in the top right corner, that the touchpad has been switched either on or off, but the touchpad isn't. it does not react at all. then sometimes when i start the laptop, the touchpad isn't active in the login, so i hit fn+f7 to turn it on, it does, and it works once im logged in.

luckily i have my mouse with me most of the time, so it isn't really a biggie, but it still serves to annoy me. if there is a way to fix this, please do tell.

---

### Post by dimamali on 2012-06-06
Exactly the same problem! It came up up suddenly about a week ago and I can't see any workaround yet.

---

### Post by N0oki3 on 2012-06-06
This is solution, that have worked for me:


> 
sudo -i
rmmod psmouse
modprobe psmouse proto=imps

to make it permanent:
edit:
> gedit /etc/modprobe.d/options

and add line:
> options psmouse proto=imps

This fix will make the touchpad be recognized as a mouse instead, which might remove some features specific to touchpads such as disable while typing.

---

### Post by dimamali on 2012-06-06
N0oki3's solution worked for me.  Thanx mate!
EDIT: Edge scrolling still works, so i bet it is not recognized as a typical mouse.

---

### Post by rasmus91 on 2012-06-11
> **dimamali said:**
> N0oki3's solution worked for me.  Thanx mate!
EDIT: Edge scrolling still works, so i bet it is not recognized as a typical mouse.

im gonna check it out, thanks.

---

