---
title: "Radeon hd4850 compatibility issue?"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by gator50 on 2008-12-06
ok,  i recently built a computer and chose the radeon HD 4850 chipset for my video card. 

when i when to install ubuntu, everything went fine until i was finished.  It goes to a white screen and will not go anywhere from there.  i have had several people try to help me out unsucessfully.  none of us can figure out how to fix it.  i dont much know what i am doing.  i was told that it was the video card that was doing this.  

i need help to get my computer up and running.

i dont know if i need a patch or drivers or what.  i need a step by step instruction on how to do this.

---

### Post by inobe on 2008-12-06
first give us the make and model of your pc/ motherboard ....

also are you still experiencing the white screen ?

edit: if you still get that screen' when starting up choose recovery mode and select root shell, in there run this command

```
sudo dpkg-reconfigure xserver-xorg
```

that should help to get you to a gui.

after that' you will need to install your graphics driver, here is a howto

[https://help.ubuntu.com/community/Video#ATI](https://help.ubuntu.com/community/Video#ATI)

---

