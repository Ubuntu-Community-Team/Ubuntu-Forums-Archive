---
title: "Motion M1400 - help needed"
date: 2010-10-22
forum: Hardware
---

### Post by fonix232 on 2010-10-22
So, I just got my "brand new" Motion M1400, model T-003 (1.1GHz CPU, 512MB RAM, 40GB hard drive). I downloaded the netbook version of Ubuntu Maverick, and installed it from a stick. Installation was fine, almost everything works perfectly. Almost.

First of all, the new interface for netbooks (unity) isn't working. It says in a message box (what has no frame, and is in the top left corner) that "No required driver detected for unity. You will need to choose the Ubuntu Desktop session once you select your user name. ETC". How could I make it run?

Then, the sound problem. It can't detect the built in speakers - what is important for me.

Also, do not forget about automatic rotation, and the hardware fastkeys - I can't use any of them.


I've already began reading the other posts about M1400, but they aren't so big help - I am a really beginner in ubuntu sadly.

Could anyone help me?

---

### Post by WebNuLL on 2010-10-30
Sorry for offtopic, but i have a little question for you.

Is touchscreen, video, sound, trackpoint, bluetooth and wireless working for you?

Im going to buy this model, i must know what is working and what isnt.

@topic
You dont have 3D acceleration installed, you must first install drivers to your card, or if there arent any drivers you cant run 3D and Unity interface (it's compiz based).

Try Ubuntu desktop edition and please answer my questions.

Thank you.

-- WebNuLL

---

### Post by fonix232 on 2010-10-30
> **WebNuLL said:**
> Sorry for offtopic, but i have a little question for you.

Is touchscreen, video, sound, trackpoint, bluetooth and wireless working for you?

Im going to buy this model, i must know what is working and what isnt.


Touchscreen, video works (even in the installer, WACOM drivers are automatically loaded. Install from USB!), I could not get Ubuntu to recognize the soundcard and BT modules. Wireless is perfect.

> 
@topic
You dont have 3D acceleration installed, you must first install drivers to your card, or if there arent any drivers you cant run 3D and Unity interface (it's compiz based).

Try Ubuntu desktop edition and please answer my questions.

Thank you.

-- WebNuLL

Yea, sadly it could not find automatically the 3D accel drivers, and I don't know how to install them manually (Intel released the binaries). Fortunately Ubuntu Netbook Remix has the original Ubuntu desktop :D (Also the separately downloaded 2D version worked flawless, except that it loaded the base Desktop version under the overlay menu).

---

### Post by WebNuLL on 2010-10-30
Can you post **lspci** and **lsusb** output?

I will search for sound and bluetooth drivers.

-- WebNuLL

---

