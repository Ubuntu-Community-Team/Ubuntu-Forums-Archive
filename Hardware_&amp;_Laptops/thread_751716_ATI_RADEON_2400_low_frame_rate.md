---
title: "ATI RADEON 2400 low frame rate?"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by Penteado on 2008-04-10
Hello community, im kind of new on Linux, just a couple months and im not going back to windows. I'm surprised how good GNU/Linux is. 

  So, heres my problem. I installed my ATI Radeon 2400 HD chip graphic card. And it works just fine.

 But .... When i use command glxgears on terminal and compare with the average frame rate people post here, i'm surprised. I Guess i must have some problem.

```
glxgears
12857 frames in 5.0 seconds = 2571.307 FPS
13211 frames in 5.0 seconds = 2642.046 FPS
13466 frames in 5.0 seconds = 2693.059 FPS

```
     
Pretty low i guess, i saw a guy with ATI posting he had 10000 + FPS. :s

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7412 Release

```

I reinstalled Ubuntu once, installed again following "How-To's"([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) and did it just fine, but my FPS are just low. I guess. 

Regards from Portugal.

---

### Post by overdrank on 2008-04-10
> **Penteado said:**
> Hello community, im kind of new on Linux, just a couple months and im not going back to windows. I'm surprised how good GNU/Linux is. 

  So, heres my problem. I installed my ATI Radeon 2400 HD chip graphic card. And it works just fine.

 But .... When i use command glxgears on terminal and compare with the average frame rate people post here, i'm surprised. I Guess i must have some problem.

```
glxgears
12857 frames in 5.0 seconds = 2571.307 FPS
13211 frames in 5.0 seconds = 2642.046 FPS
13466 frames in 5.0 seconds = 2693.059 FPS

```
     
Pretty low i guess, i saw a guy with ATI posting he had 10000 + FPS. :s

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7412 Release

```

I reinstalled Ubuntu once, installed again following "How-To's"([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) and did it just fine, but my FPS are just low. I guess. 

Regards from Portugal.
HI and you may look at [[COLOR="Green"]ENVY[/COLOR]](http://albertomilone.com/nvidia_scripts1.html) as it has helped other users with this graphics card

---

### Post by Penteado on 2008-04-11
I tried it also, but the drivers dont get setup correctly. :s

---

### Post by Penteado on 2008-04-11
Can someone with ATI RADEON card post their FPS using glxgears?

---

### Post by overdrank on 2008-04-11
> **Penteado said:**
> I tried it also, but the drivers dont get setup correctly. :s

HI and you may have to reconfigure your xorg after installing the drivers with Envy. Have you tried to configure your xorg with the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` after installing the drivers with Envy. Also you will have to uninstall any previous drivers before installing with Envy

---

### Post by Penteado on 2008-04-11
Envy doesnt install my drivers properly.


I ran the reconfigure dpkg command and its the same. :/  ATI .... 

I thinking of buying a laptop, FOR SURE not with a ATI CARD!


Thanks anyway.

---

