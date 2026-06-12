---
title: "No Audio on a SONY VAIO"
date: 2011-12-31
forum: Hardware
---

### Post by dirtynorth on 2011-12-31
Hello,

I have installed Ubuntu with no problem on a number of home computers and laptops (although I am not an expert by any means) and I have run into a problem with a SONY VAIO PCG-71613L laptop.  Everything runs fine except no sound comes from the speaker.  I am trying to install 64bit 10.04

Also if  it helps the laptop is dual boot with windows 7 where the speakers work fine.

Thanks

---

### Post by lidex on 2011-12-31
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by MoreOrLess on 2012-01-01
I'm just responding to subscribe to this thread. :)

---

### Post by clynn3 on 2012-05-09
hi there

 I dont by any mean to hi-jack but if I am tell me.  I have a sony vaio that I just put ubuntu 10.04 (edit: I am also running 64bit) on as well and the sound is not working.  mine is a PCG-71212L so it is different but it might be the same problem. 

I did what you said and here is the link

[http://www.alsa-project.org/db/?f=e44124494e5e66a30a4e208b5767791dab2538bb](http://www.alsa-project.org/db/?f=e44124494e5e66a30a4e208b5767791dab2538bb)

---

### Post by iMurshaq on 2012-05-09
This may sound stupid but go into your sound options and make sure the volume isn't turned down. Someone else had this problem and that was the solution.

---

### Post by clynn3 on 2012-05-10
haha, thank you.  that was the first step on the official ubuntu sound troubleshooting guide too.  sounds like a common problem!  I have checked alsa mixer the sound preferences the laptop sound and they are all on.  but there might be somewhere else to check.  any other places i should look?

---

