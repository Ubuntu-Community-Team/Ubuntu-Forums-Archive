---
title: "Screen Resolution on Asus A3A computer"
date: 2008-12-22
forum: Hardware
---

### Post by ilitheblack on 2008-12-22
hi everybody, i have ubuntu 8.04 but i dont know how to change my screen resolution i am newbie... and when i run this command it says it is the newest version and my video card is intel..(it is a laptop on board video card)... 
```
sudo apt-get install xserver-xorg-video-intel 
```
i think my video card was installed... :S if i am wrong how can i understand my video card installed or not ?
And ofc my main question is where is the menu to change the screen resolution to higher levels..
THX FOR YOUR REPLIES...
P.S.:When i run that command:
```
lspci | grep VGA
```
it says :
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)

---

### Post by canoemoose on 2008-12-22
Errm... What exactly are you trying to do?  Where did you get those commands from?  What have you tried already?

---

### Post by ilitheblack on 2008-12-22
M8 , i have an ubuntu 8.04... And i installed it from its iso file on to my hard drive.. After that its screen resolution was automatically adjusted (or we can say default) to 1024X768... I want to change it into an higher resolution like 1224X768 or etc.. but couldnt have found how i can adjust to the new screen resolution yet... I hope ,i could explain..Also this is the highest resolution in screen resolution preference...But on my windows this is not the highest resolution of my screen...
THX FOR YOUR INTEREST...
BTW i have already tried to change the value in this file. no change...
/etc/X11/xorg.conf

---

### Post by canoemoose on 2008-12-22
Right. From memory, in synaptic there is a package called 915resolution or something similar.  Read about it in synaptic and see if it fits your situation.

---

### Post by ilitheblack on 2008-12-22
yes m8 i have installed it and done what it says here but nothing happens :S

[http://slibuntu.wordpress.com/2007/03/13/using-915resolution-to-change-resolution/]("http://slibuntu.wordpress.com/2007/03/13/using-915resolution-to-change-resolution/")
They say it works but not for mine...(ofc some of them...)..

---

### Post by canoemoose on 2008-12-23
Ok....
Try following what this says: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

If the first bit works (ie setting it manually, try *one*of the triks to make it persistent.

---

