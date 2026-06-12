---
title: "&quot;scrambled&quot; Monitor resolution"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by Warmaster Ancaris on 2008-04-05
Greetings.  I have a bit of a problem.  Somehow I seem to have scrambled my resolution and I don't know how I did it.

When I first boot up Ubuntu, it seems to be loading like normal, but once I get to the start up/login screen, my display is effectively scrambled.

I am still a terrible noob when it comes to Ubuntu and linux altogether so I have no idea how to fix this.   I'm guessing I need to do stuff from the command prompt in recovery mode, but I have no idea what to enter.

If anyone could please give me some help I'd greatly appreciate it.

---

### Post by overdrank on 2008-04-05
> **Warmaster Ancaris said:**
> Greetings.  I have a bit of a problem.  Somehow I seem to have scrambled my resolution and I don't know how I did it.

When I first boot up Ubuntu, it seems to be loading like normal, but once I get to the start up/login screen, my display is effectively scrambled.

I am still a terrible noob when it comes to Ubuntu and linux altogether so I have no idea how to fix this.   I'm guessing I need to do stuff from the command prompt in recovery mode, but I have no idea what to enter.

If anyone could please give me some help I'd greatly appreciate it.

Hi, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by Warmaster Ancaris on 2008-04-06
This got it working for me.  Thank you very much!

---

