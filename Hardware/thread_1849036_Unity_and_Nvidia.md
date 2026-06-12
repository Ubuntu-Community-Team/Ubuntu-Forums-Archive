---
title: "Unity and Nvidia"
date: 2011-09-23
forum: Hardware
---

### Post by al1x on 2011-09-23
Hello, I just installed 11.04 and I have a wierd issue. When I install the proprietary driver from additional hardware after the reboot the unity plugin disappears and the /usr/lib/nux/unity-support-test -p command give this result ```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

```Then, when I remove the proprietarary driver the unity works fine and the previous commands give a possitive result with all the modes being  "yes".Furthermore, when I remove the prop. driver another driver appears saying that it is experimental. What should I do? 
Thanks.

---

### Post by al1x on 2011-09-23
Nobody have any solution to propose?:(

---

### Post by papibe on 2011-09-23
My guess is that you are not using yet the Nvidia driver yet.

First let's make sure you don't have [Optimus]("http://www.nvidia.com/object/optimus_technology.html") (which would mean another course of action). Could you post the result of this command?
```
$ lspci | grep VGA
```
Regards.

---

### Post by mikewhatever on 2011-09-23
Unity in 11.04 doesn't work with older Nvidia cards. Since you haven't posted the model, I can only guess that you have one of the Geforce 7000/6000 or older ones.

---

### Post by bichiliad on 2011-09-24
I have the same issue, but I DO have optimus (or rather, the graphics card has "optimus technology." Not sure if my linux half actually uses it yet). What course of action would you recommend?

---

### Post by papibe on 2011-09-24
For Optimus, check this [thread]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") (specially from post #7 to the end).

Regards.

---

### Post by al1x on 2011-09-25
Sorry for not posting sooner but I was away for 2 days. In fact, I was trying to install ubuntu 11.04 to another computer(not mine) which indeed has Optimus enabled(It's a nvidia GTX 400M family chip). Then, I installed the restricted driver and unity stopped working. So I removed it and installed the experimental driver and it seems to work fine !(Although, GUI crashes sometimes when you're making changes through CCSM). Soon, I'am going to install ubuntu to my new laptop which has a GTX 560M chip and probably I will face the same driver's problem. 

>  Could you post the result of this command?
     Code:
     $ lspci | grep VGA 
 I don't have the laptop right now (as I mentioned it's not mine) but I can assure you that it has optimus enabled and that it's a chip of GTX 400M or 500M family.

---

### Post by al1x on 2011-09-25
> **papibe said:**
> For Optimus, check this [thread]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") (specially from post #7 to the end).

Regards.

I checked the thread and I got the information, thanks! This tip ->** Using acpi_call module to switch on/off discrete graphics card in Linux **

   
  seemed very usefull for laptop users. But, I'am not sure what's better now, keep the experimental driver or just remove them all(from additional hardware) ?

---

### Post by al1x on 2011-10-01
Well, now, I installed 11.04 to my new laptop with nVidia GTX 560M[COLOR=Black] [COLOR=Red]which has Optimus [/COLOR][/COLOR]and the proprietary driver works perfect.. I have unity and the compiz features working smoothly and I can play games via wine.. Also when I disable the propr. driver unity and compiz stop working.. So, things are not so straightforward with Optimus.(I mean you don't have to uninstall the propr. driver in some circumstances..)

---

