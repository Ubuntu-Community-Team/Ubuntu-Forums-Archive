---
title: "Errors with Ubuntu X Configuration"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by ShizZy on 2005-12-27
Hello - I am having some difficulties here. I install Ubuntu fine, and then when I start to run it, it loads, then I get the blue screen (like the installer screen) that says "Failed to start the X server (your graphical user interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?"

I click yes, and it says my X version (6.8.2). Click ok, asks me to view the detailed server information, clik ok again, shows basically the same stuff, then it says "The X server is now disabled. Restart GDM when it is configured correctly."

And it goes into a command prompt. Any ideas? 

It's a Compaq Presario Notebook, with 512mb of RAM, Athlon 2800 Sempron, and a Radeon 200M video card.

Help is appreciated...

---

### Post by stuporglue on 2005-12-27
You can try reconfiguring the xserver. Log in then run 

$ sudo dpkg-reconfigure xserver-xorg

There are about 20 screens of questions that will result in a new xorg.conf for you. 

If that doesn't work, and you have a network connection, try doing updates, then running dpkg-reconfigure. 

$ sudo apt-get update 
$ sudo apt-get upgrade
$ sudo dpkg-reconfigure xserver-xorg

---

### Post by Imexius on 2005-12-27
ok once you get into the terminal log in screen, log in. Then type:

sudo pico /etc/X11/xorg.conf

look for BusID

under busid type Option          "noaccel"

press ctrl o-->press enter --> press ctrl x
then type startx

i have a similiar setup to your box, and had the exact same problem, the former solved it.

---

### Post by ShizZy on 2005-12-27
Wow... thanks for the quick response.  After a ton of searching before I saw these posts I found the fix you posted Imexius.  Works great, huge thanks!

---

### Post by harisund on 2005-12-27
Could you please tell me what is the make of the laptop that you have? I have a compaq presario v2000z (Amd64 processor, but same graphics card as yours.) I have simply not been able to get Ubuntu working on this, even with the HP customized version of Ubuntu. 

Thanks a real lot !!

---

