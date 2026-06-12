---
title: "Video driver screwed up!"
date: 2010-02-18
forum: Hardware
---

### Post by jratzlaf on 2010-02-18
I've installed Ubuntu 9.10 on a Thinkpad T42. Works great! But I tried connecting it to a large LCD TV and in the process evidently screwed up the video driver. I was trying to get it to run the TV in its native resolution of (I think) 1360x768, and at one point before it would switch the TV into that mode, Ubuntu said something about rewriting the video config file (or something), and would I please log out and back in, and after that the video has been messed up. Specifically (connected to the TV or not), if I drag a window around the screen, it will leave garbage behind. And many other examples of video problems. I confirmed that it's not the hardware by booting from the live CD.

So how do I update or reinstall the video driver? If I go to System|Administration|Hardware drivers, it simply says "No proprietary drivers are in use on this system." I suspect I merely need to reset some defaults... maybe not... help! BTW, this has the infamous ATI 7500 GPU. Thanks - JR

---

### Post by nos09 on 2010-02-18
If you dual-boot your computer with Windows, you’ll need to select the “Ubuntu [...] (recovery mode)” option from the menu that appears just after your computer boots. If yourcomputer has only Ubuntu installed on it, you’ll need to press a key to enter the boot menu when prompted. Then select the “Ubuntu [...] (recovery mode)” option.
   
       Eventually, a command prompt will appear, and you’ll see root@ubuntu:~#, followed by a
   cursor. Type the following:
  
>  dpkg-reconfigure xserver-xorg 

it will solve your problem hopefully..

---

### Post by jratzlaf on 2010-02-18
Thanks for the response, but it didn't seem to change anything...

---

### Post by buzz1170 on 2010-02-18
I think I'm having a similar problem. I'm using a Mobile Intel® 965 Express Chipset. It started doing this after I uninstalled CompizConfig in xterm. I can't get CompizConfig to work and my visual effects keep reverting to 'none'.

---

### Post by jratzlaf on 2010-02-19
Let me try this one more time. In Windows if there is a driver problem it is fairly simple to go to the Device Manager, remove the driver, and then restart, whereupon Windows will detect the device without a driver and attempt to re-install the driver. How do you do that under Ubuntu?

---

### Post by nos09 on 2010-02-20
> **jratzlaf said:**
> Let me try this one more time. In Windows if there is a driver problem it is fairly simple to go to the Device Manager, remove the driver, and then restart, whereupon Windows will detect the device without a driver and attempt to re-install the driver. How do you do that under Ubuntu?


ok tell me what happened  when you type the command i've gave you yesterday ???

with description ..

---

### Post by nos09 on 2010-02-20
ok i just found the code of replacing compiz with metacity after this compiz will not start again.

edit ~/.gnome/desktop/session/required_components/%gconf.xml 

i'm not sure about this code though but give it a try..

---

### Post by jratzlaf on 2010-02-22
> ok tell me what happened  when you type the command i've gave you   yesterday ???

No response whatsoever. After about a second the command prompt returns.  - JR

---

