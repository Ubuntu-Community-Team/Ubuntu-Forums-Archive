---
title: "Proprietary ATI Driver fglrx kills my Video"
date: 2013-05-16
forum: Hardware
---

### Post by Galya on 2013-05-16
So, I'll explain the problem, but first I want to cry aloud PLEASE HELP!


  I've used Ubuntu 12.04 for more than half an year and everything is  set up just the way I want it. But I did a stupid mistake - I installed  Proprietary ATI Driver fglrx.
  Now the system boots normally, but after I choose to launch Ubuntu  the screen goes black and my monitor doesn't receive any signals.


  I tried some guides in recovery mode, but it's not working. Finally I  started live cd and replaced files in /usr/share/X11/xorg.conf.d/ with  original files. Still not working.
  Please give me any ideas how to remove this killer!

---

### Post by marianoa on 2013-05-16
Choosing the recovery mode takes you to a terminal session? If it does, did you try removing the proprietary drivers? You can also try to follow this guide
[http://blog.danfego.net/2009/11/fixing-nvidia-driver-issues-on-ubuntu-karmic/](http://blog.danfego.net/2009/11/fixing-nvidia-driver-issues-on-ubuntu-karmic/)
to disable the proprietary driver without removing it, it requires jockey-text, if it's not installed you can install it from the terminal. 
Recently ubuntu-drivers has replaced jockey-text, check which one you can find as an option to install, the syntax should be similar but I can't find the documentation for ubuntu-drivers at the moment

---

### Post by Galya on 2013-05-16
Thank you for answering. In the meantime I found an answer to my question:

It was really annoying because when you boot without video, you have to shut down in inappropriate manner, so in recovery mode you get first some errors. 

But the whole point is to get in recovery mode and type two lines:

    mount -o remount,rw /
    sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

---

### Post by marianoa on 2013-05-16
Perfect, so you can mark the post as solved

---

