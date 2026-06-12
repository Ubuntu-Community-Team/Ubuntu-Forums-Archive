---
title: "unable to change the appearance settings from none to extra - vicious cycle"
date: 2008-10-05
forum: General Help
---

### Post by allholy1 on 2008-10-05
When I change the visual effects from none to either normal or extra, I get a message saying that it has to install the NVidia driver (which I have a x1950gt).  I figured sure, why not do that.  So I did that, screen resolution got messed up and real big.  Then I went to switch it to extra, and now it's asking me to install the ATI accelerated graphics driver.. I do that, and everything looks fine, but when I go to switch it to extra again, it tells me to install the NVidia accelerated drivers.

I have an ECS GF7050VT-M motherboard, which I'm pretty sure has some NVidia stuff inside of it. 

How do I fix this?

Thanks in advance


** edit ** it appears to be working now... but when I still click on extra, it still asks me to install the accelerated graphics drivers for nvidia.. which i've done like 10 times..

---

### Post by Blackwolf_Oz on 2008-10-06
You need to know what kind off graphics card you have, as installing both ATI & Nvidia display drivers will mess some thing up !

---

### Post by jualin on 2008-10-06
Can you please go to the terminal and type > lspci
lshw -C video and post the output here.

---

### Post by Alpha-geek on 2008-10-06
> **allholy1 said:**
> 
** edit ** it appears to be working now... but when I still click on extra, it still asks me to install the accelerated graphics drivers for nvidia.. which i've done like 10 times..

That's most likely due to your video card being an ATI, NOT an Nvidia. (x1950gt has ATI GPU) Remove the Nvidia driver & install the ATI driver. (You could use Envyng) Then set appearance to extra. It will hold then.

---

