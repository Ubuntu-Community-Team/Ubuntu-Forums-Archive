---
title: "Radeon 9600xt drivers"
date: 2011-09-28
forum: Hardware
---

### Post by nutomg on 2011-09-28
Hello guys.I had 11.04 natty ubuntu, i tryed installing drivers but none of them dont work.I tried additional drivers,fglrx and all of that.So, i thinked i need to downgrade to 10.10 ubuntu, but it still dont work.What ubuntu version support 9600 xt radeon video card?I heard i need to downgrade

---

### Post by nutomg on 2011-09-29
I still need help, should i downgrade version of ubuntu?

---

### Post by MG&amp;TL on 2011-09-29
Typically downgrading does no good. Less progress, after all. When you say none of them work, how so? Can you boot after installing them, do they  provide the 3d acceleration?

---

### Post by nutomg on 2011-09-29
Yes, as i seen in radeon page ubuntu, it sayed that radeon 9600 support 3d acceleration.So, what should i do?I tryed installing with additional drivers, binary in terminal but none worked

---

### Post by nutomg on 2011-09-29
So do you guys knowjj how to fix itjj?

---

### Post by mastablasta on 2011-09-29
First off the proprietary ATI drivers don't work for this card, because ATi dropped support for it. 
 
What you do use is opensource drivers. They do support this card. so if you only install the sysetm these opensoruce drivers come preisntalled. as you can see display is working.  Why are you trying to install ATI drivers?
 
You can (if you need to) upgrade the opensoruce drivers to testing or higher version by using a ppa called Edgers PPA, but you need to read all the info about it and how to remove them if they cause crashes etc: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
 
As i know 9600XT works perfectly well with the opensource drivers that are preinstalled on system installation. saying "they don't work" doesn't give people much to work on. What exactly doesn't work? Have you tried running some 3d testing utilities (for example try running glxgears)? have you tried running some 3D game (for example Cube, Urban Terror or something)? If they can't run what exactly is the error message?

---

### Post by nutomg on 2011-09-29
Im just trying to install graphic drivers to play simple games, this video card works on xp good oblivion good setting, so i need drivers for ubuntujj

---

### Post by MG&amp;TL on 2011-09-30
run:

```
sudo apt-get install mesa-utils
glxgears
```

wait for a while, then it should tell you how many frames a sec you are running at. That should give us an idea of what you're up to.

---

### Post by reboskyz24 on 2011-10-08
I have the same issue with Radeon 9600XT, mainly that Amazon Video and youtube are choppy.
glxgears averaged ~600 frames every 5 seconds

---

### Post by snafu006 on 2011-10-08
Here are some better drivers then Edgers PPA i have a few older Ati cards and this drivers work better [http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers) . Install them and watch your video card fly.

---

### Post by reboskyz24 on 2011-10-08
That actually caused a decrease in frame rate when run in full screen ~380/5 sec.
So I upgraded to an old Radeon X300 I had sitting around.  glxgears are ~1000/5sec, but Amazon Video/Youtube still choppy at full screen.
What're some supported AGP8X cards out there that can improve my visual experience?

---

