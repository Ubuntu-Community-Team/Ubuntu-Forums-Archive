---
title: "cant get nvidia 8800 to wont work with gutsy!"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by amik on 2008-01-22
i got a completly new computer a while ago and freshly installed xp on it and successfully dual booted it with ubuntu and now when i boot into ubuntu it cannot start x. loads of people are saying to go to restricted drivers manager but i cant as it doesnt start x. i have tried using envy and i know people have got their nvidia 8800 working with envy but when i tried it, it didnt seem to find my card or was not able to install it.please please please ... help!

---

### Post by renzokuken on 2008-01-22
boot up your PC and when it goes black/refuses to startx press

```
Ctrl + Alt + F1
```

to get to a TTY terminal. login and then run the following command

```
sudo dpkg-reconfigure xserver-xorg
```

run through the wizard till you get to the drivers screen and select the **"vesa"** driver.

carry on and exit the wizard, reboot with

```
sudo restart
```

and see if your xsession now starts. if it does, you will probably have a crappy resolution, but now you have X running, you can use the Restricted Drivers Manager to install the proper nVidia drivers and use your 8800 in all its linux glory.

NOTE: if "vesa" doesnt work, you could always try "nv" (but not sure how well "nv" supports the newer 8800 cards.

---

### Post by msemtd on 2008-01-22
I have the same here on the PC of an elderly friend - I booted the 7.10 disc in "Safe Graphics Mode" and got a perfectly usable 1280x1024 desktop with the VESA driver. The Restricted Modules Manager doesn't recognise the card so next time I visit I will try the latest nvidia binary

---

### Post by msemtd on 2008-01-22
> **renzokuken said:**
> NOTE: if "vesa" doesnt work, you could always try "nv" (but not sure how well "nv" supports the newer 8800 cards.

The nv driver segfaults on these cards for me :(

---

### Post by amik on 2008-01-22
ok i did the sudo dpkg-reconfigure xserver-xorg and i tried selecting vesa and nv and nvidia but vesa seems to be the best one as the other two give a crap resolution but with vesa and can select up to a high resolution..... now my problem is..i want to get compiz working but when i try to enable it it says they cant be enabled... i also cant run the restricted drivers thing it says i dont need it or something but its definitly installed. i have tried to properly configure to NVIDIA not vesa with envy but it does NOT work.. please help.. thanks for the reply

---

### Post by renzokuken on 2008-01-23
try removing the nvidia driver installed by envy, then use the official Restricted Drivers Manager to install nvidia driver

---

### Post by amik on 2008-01-23
when i run the restricted driver manager it says my hardware doesnt need any restricted drivers????

---

### Post by cooltd825 on 2008-01-23
i have the same problem, low resolution or sometimes a blank screen.  it was working for one day under the restricted driver manager, full 3D effects and everything.   i'm brand new to Linux, and so far it's been a pretty crappy experience.  i've tried installing the drivers through Envy, Nvidia.com, and just using the restricted drivers manager.  it seems like whenever i try to enable a driver and reboot, it just resets all my settings and keeps the driver disabled. 

makes me glad i chose to dual boot with Vista.  definitely a more stable OS.

---

### Post by cooltd825 on 2008-01-23
oh, and i'm using the 8500GT.  the little baby brother of yours.

---

