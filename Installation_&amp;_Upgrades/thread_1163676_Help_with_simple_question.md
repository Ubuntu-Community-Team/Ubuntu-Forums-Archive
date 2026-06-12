---
title: "Help with simple question"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by newbie34 on 2009-05-18
So I installed Ubuntu..  I'm completely new so this may be a simple question.   The wifi seem slow.  

GS-27USB-50

So I want to install the linux driver that come with the wifi CD.  How do I do that?  when I open the driver folder in the CD and look at the readme.txt it  I got no idea what all that mean, how do you do all of this... thank for the help...


< Installation >
Runing the scripts can finish all operations of building up modules 
from the source code and start the nic.
    1. Build up the drivers from the source code
      ./makedrv

    2. load the driver module to kernel and start up nic
      ./wlan0up
          Note: when "insmod: error inserting 'xxxx.ko': -1 File exists" comes out
                after run ./wlan0up, please run ./wlan0down first, then it should 
                be ok.

< Set wireless lan MIBs >
This driver uses Wireless Extension as an interface allowing you to set
Wireless LAN specific parameters.

---

### Post by cariboo on 2009-05-19
Before trying to install the driver from the cd, I would check what driver is already loaded. To do this open an Applications-->Accessories-->Termnal and type:

```
sudo lshw -C network
```

the above command will print the details of your network devices on screen. Could you paste the output in your next post.

---

### Post by newbie34 on 2009-05-22
Thank cariboo907 for the reply.

When I was checking for the driver as you suggested, I notice that the update manger was doing a update.  After that, the whole computer work faster, :D including the WiFi problem.  As a XP user I got used to putting in the CD and install every driver when I reformat.  So this is better.  The add/remove application is also very useful too.  

Is there a good Linux for dummy out there?   I have never use the DOS window in xp, so the terminal is a little intimidating.  

Thank..

---

### Post by Marvin666 on 2009-05-22
<disregard this post, my browser messed up on me>

---

### Post by Sef on 2009-05-22
>  Is there a good Linux for dummy out there?   I have never use the DOS window in xp, so the terminal is a little intimidating.  

Easiest way to use it is to copy and paste commands.   The terminal is not needed very often.

---

