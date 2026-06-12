---
title: "I can't see anything when I boot"
date: 2008-10-15
forum: Hardware
---

### Post by FallenAnzel on 2008-10-15
I was trying to change the dimensions from 640x480 or whatever because that was my only selection so I edited in Xorg and when I restarted I couldn't see anything after I booted obviously because it wouldn't fit my screen but I cant even view the troubleshoot page. I made a backup but I have no idea how to install.

---

### Post by theirishfozz on 2008-10-16
Something you could try is after bootup when you cant see anything and you're sure its done booting up press ctrl+alt+f1. This should allow you to log in without X, old school. Once you're in edit your xorg.conf and change back to 640x480. 

Next step you need to get drivers for your video card for linux. Google your video card and "linux" or "ubuntu" and you'll probably find something. THe nvidia drivers are a good place to start. Make sure you dont have something waiting to be run from the restricted drivers menu. Once you have drivers working you'll be able to change res.

---

