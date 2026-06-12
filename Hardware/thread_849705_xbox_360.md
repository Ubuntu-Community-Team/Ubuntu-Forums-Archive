---
title: "xbox 360"
date: 2008-07-04
forum: Hardware
---

### Post by asmugone on 2008-07-04
Im having trouble getting my xbox 360 wired controller working, it dosent register left and right triggers, I installed per the ubuntu guide??!!

---

### Post by flytripper on 2008-07-04
did you install the config program too?

---

### Post by starcannon on 2008-07-04
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

### Post by asmugone on 2008-07-05
I followedthat tutorial to the letter, when I installed the pad, as for the program are you sayin jscalibrator, because yes and the buttons dont sense in that either, also is there a way to bind the second (right) joystick, i cant get to seem to make it work in games, but r3 and l3 work fine as does the left joystick.

---

### Post by asmugone on 2008-07-05
bump, really need some help on this one guys

---

### Post by starcannon on 2008-07-05
For my saitek p2500 I had to install this driver as well:
```
sudo apt-get install xserver-xorg-input-joystick
```
I'm not sure if that will help with the xbox 360 game pad or not, but it may be worth a try, I also had to unplug and replug my controller for changes to take effect.

I wrote a guide for my saitek controller, I don't know if it will be of any use for your controller but you can look it over here:
[http://ubuntuforums.org/showthread.php?t=846907&highlight=p2500](http://ubuntuforums.org/showthread.php?t=846907&highlight=p2500)

GL and if you get it going write us a guide :)

---

### Post by asmugone on 2008-07-05
ill have to try it when I get back near my computer, (writing from my phone while im on the road) I tell you first things first, im gonna write a batch file to automate this whole process!!!

---

### Post by asmugone on 2008-07-13
Im at the system in question and still having the same issues, also in joystick calibrator the right and left trigger are acting like axis and not registering as buttons.

The right analog stick is registering but I cant seem to get it to be useful for anything when playing grand theft auto vice city

---

### Post by bigdee973 on 2008-07-14
> **asmugone said:**
> Im at the system in question and still having the same issues, also in joystick calibrator the right and left trigger are acting like axis and not registering as buttons.

The right analog stick is registering but I cant seem to get it to be useful for anything when playing grand theft auto vice city

im having the problem where i press buttons, triggers, joysticks and yet none of them work..joystick calibrater sees my controller loads it just fine but when i press buttons i get no effect even on zsnes.  i dont understand. it use to work

---

