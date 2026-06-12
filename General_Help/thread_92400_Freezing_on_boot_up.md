---
title: "Freezing on boot up"
date: 2005-11-19
forum: General Help
---

### Post by jackgnat on 2005-11-19
Hi there, first post.

I'm mostly new to Linux besides playing with Damn Small Linux a bit.

I just received my CD's the other night in the mail and I've been trying to install it on one of my computers. I'm putting it on a small 3.2Gig hdd inside my main system. But after installing, everytime I boot up, it freezes before giving me a login and shows me a black screen with an unblinking cursor. I know that it's not the hard drive, because it installed fine on the same hard drive when it was inside another computer.

Any experience with this problem?

---

### Post by taurus on 2005-11-19
Sounds like it is having a problem with your graphic card/monitor!!!  Try holding down <Ctl><Alt> while hitting F2.  Log in and have a look in /var/log/Xorg.0.log to see what's the problem...

---

### Post by jackgnat on 2005-11-19
Thanks for the quick reply, but like I said, I'm new to this.

I don't know when to press <ctrl>+<alt>+<f2>. Does it bring you to the recovery console? If so, it's already accessible to me through the dual boot menu on startup (I'm running XP on a seperate, bigger drive).

And if that is where I'm supposed to go, what commands do I use to access the file? I tried typing in just /var/log/Xorg.0.log but then it said access was denied.

Any more help would be greatly appreciated.

---

### Post by Trab on 2005-11-19
another idea would be this
after hitting <ctrl><alt>F2 and logging in type 
```

startx

```
u might need to use sudo first, i cant remember...
if it starts and u get some intersting looking terminals (They should all be white) then click on one of the terminals and type 
```

gnome-session

```
good luck!

---

### Post by jackgnat on 2005-11-19
I still don't understand where to press ctrl+alt+f2 and login.

I tried "startx" at the recovery console and somecode whizzed by and I got a black screen. 

Typing in gnome-session only gave me an error.

---

### Post by jackgnat on 2005-11-19
Ok, I've realised that if I remove my Radeon 9200 card, and use onboard graphics, then it will boot normally.

This provides a solution, but obviously I'll want to use my card still. So how would I go about attempting to get the card to work with UbuntU?

---

### Post by taurus on 2005-11-19
You need to install a driver for your ATI video card.  Here is a link that you should check it out, [http://www.ubuntuforums.org/showthread.php?t=75378](http://www.ubuntuforums.org/showthread.php?t=75378).

---

