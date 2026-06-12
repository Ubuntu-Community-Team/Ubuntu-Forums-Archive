---
title: "Issues with new version"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by gemone on 2009-05-26
Hello,
I have been having issues with the new version of Ubuntu. Every time I try to select something on the desktop with the mouse. There is no response from my selection. Does anyone know what the problem may be?

Thanks

---

### Post by CadetD on 2009-05-26
Describe "no selection". 

I have been trying to troubleshoot a problem since the upgrade whereas there is a 2-3 second delay between a mouse click and actual action. 

I upgraded to the latest ATI drivers (there doesnt seem to be any FGLRX with 9.04...) but that was not the problem. 

AMD 64 Ubuntu Studio if that makes a difference.

---

### Post by gemone on 2009-05-26
> **CadetD said:**
> Describe "no selection". 

I have been trying to troubleshoot a problem since the upgrade whereas there is a 2-3 second delay between a mouse click and actual action. 

I upgraded to the latest ATI drivers (there doesnt seem to be any FGLRX with 9.04...) but that was not the problem. 

AMD 64 Ubuntu Studio if that makes a difference.

Everything on the desktop. Ex; Mozilla and places.

---

### Post by gemone on 2009-05-27
Does anyone know what the problem may be? As I stated before I cannot select anything on my desktop. No matter how many times I press the button on my mouse.

---

### Post by Sef on 2009-05-27
> gemone 	 		 Does anyone know what the problem may be? As I stated before I cannot select anything on my desktop. No matter how many times I press the button on my mouse. 

Can you select something from Applications, Places, or System?

If not, then maybe your mouse is bad.   Do you have another mouse that you can plug in or another computer that you could try the mouse on?

---

### Post by hal8000 on 2009-05-27
This maybe some option in the /etc/X11/xorg.conf file relating to input device.
Try booting with the live jaunty CD, if that works ok, save the xorg.conf file for comparison with your installed installation, there may have been some subtle changes.

I never upgrade, always run an old and new version in parallel, this way I can thoroughly test my system before deleting the old one.

---

### Post by gemone on 2009-05-27
> **Sef said:**
> Can you select something from Applications, Places, or System?

If not, then maybe your mouse is bad.   Do you have another mouse that you can plug in or another computer that you could try the mouse on?
It's not the mouse I already tried that option yesterday.

---

### Post by gemone on 2009-05-27
> **hal8000 said:**
> This maybe some option in the /etc/X11/xorg.conf file relating to input device.
Try booting with the live jaunty CD, if that works ok, save the xorg.conf file for comparison with your installed installation, there may have been some subtle changes.

I never upgrade, always run an old and new version in parallel, this way I can thoroughly test my system before deleting the old one.
I don't have the jaunty cd. I probably will uninstall and use the earlier version.

---

### Post by Grafixx01 on 2009-05-27
Did you do a fresh install or upgrade? I had XP Pro on my OQO and then put on Ubuntu and I didn't have any issues. When I did the same on my Dell Desktop, I had issues but then I just swapped to two separate hard drives and then the problems were gone, after the updates of course.

---

### Post by gemone on 2009-05-28
> **Grafixx01 said:**
> Did you do a fresh install or upgrade? I had XP Pro on my OQO and then put on Ubuntu and I didn't have any issues. When I did the same on my Dell Desktop, I had issues but then I just swapped to two separate hard drives and then the problems were gone, after the updates of course.
I tried a fresh install and update and I got the same results. I most likely will have to go back to the previous version.

---

