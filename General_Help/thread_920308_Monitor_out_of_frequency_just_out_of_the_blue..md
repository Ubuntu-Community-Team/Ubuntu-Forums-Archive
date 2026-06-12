---
title: "Monitor out of frequency just out of the blue."
date: 2008-09-15
forum: General Help
---

### Post by SrEstroncio on 2008-09-15
Hello everyone, good day, I have been running ubuntu on my laptop for more than a year now but some months ago I installed ubuntu 7.10 on my desktop computer and now I am getting problems with my monitor giving me a OUT OF FREQUENCY message, here's the story:
After I installed ubuntu whenever I chose Ubuntu from the GRUB menu a message saying OUT OF FREQUENCY appeared during the ubuntu loading time, it lasted about 10 or so seconds according to a timer that came with the message and then it seemed as if the monitor catched on and I saw the ubuntu login screen (the screen goes black during the frequency message) everything went fine after that, I mean, everything seemed well and things went like that for some months. Recently I had some hardware issues with my PC (it's was built by a friend) so I had it taken to a place to check it out and fix whatever it had, it results there were some wrongly connected cables, I got my PC back and when I plugged the monitor in and got into ubuntu I saw the OUT OF FRECUENCY message, but it just kept there for the whole 20s the message lasts, and after that the screen just kept black, I know ubuntu is still running cause I can still hear the login sounds, I just can't see anything past selecting ubuntu from the grub menu, windows hasn't given me any problems with that. 

I would really appreciate if someone who had the same problem or knows how to fix this could help me, thanks.

I am running Ubuntu 7.10 with a Gateway LCD monitor (model: FPD1520) whose max resolution is 1024x768 (kinda old), and it's connected to the socket of a nVidia graphics card.

Note: I can't see ANYTHING in ubuntu, so I can't use it right now

---

### Post by ianhaycox on 2008-09-15
Try booting into recovery mode from the Grub menu and see if that works.

Sounds like an NVidia driver/config problem. have you got any ModeLines in your /etc/xorg.conf file that may have changed ?

---

### Post by SrEstroncio on 2008-09-16
I don't think so because I haven't been messing with ubuntu around before that happened, and after that, well, I can see anything, so I'm pretty sure I haven't used not to mention modified anything in ubuntu.
Uh, any suggestions about what to look for in my /etc/xorg.conf file? or how to check if it was a problem with the nvidia drivers or stuff? thanks

---

### Post by ianhaycox on 2008-09-16
Can you post your xorg.conf file here and the output from

```
$ lspci | grep -i nv

```
Did you install the proprietry Nvidia drivers ? If so, was it via the restricted drivers manager, or using the download from the nvidia site ?

---

