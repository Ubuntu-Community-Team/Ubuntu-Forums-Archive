---
title: "Quad Display won't work 2nd card won't activate"
date: 2013-06-28
forum: Hardware
---

### Post by shanep-server on 2013-06-28
K i'm over here cuz you guys always been great help. I'm using linux mint 15 cinnamon.. pretty much 13.04 ubuntu if i'm not mistaken. I have a desktop with quad 23" LCD's running a geforce 460 GTX an a geforce 7600 GS. Now I have 2 23" acer lcds hooked up too the 460 GTX (primary pcie) and  2 23" samsung lcd's hooked up to 7600 GS for top 2 monitors. Now the recommended driver for 460 GTX is nvidia 3.10.. the 7600 GS is nvidia 304. If I try to install any drivers for 7600 GS then i crash xorg. If I install 3.10 drivers then only the 460 GTX an 2 lcd's are displayed in Nvidia settings. If I go into display settings for linux from system settings and I unclick mirror option it will register all 4 displays. It won't however active the top 2 displays hooked up too the 7600 GS if i click apply. I've tried manually editing the xorg.conf file but got no where.. I don't think I know enough to edit it myself. I know the top 2 lcds an graphics card work.. when I installed mageia it registers only the 7600 GS an 2 23" lcds and I can't get it too register the 460 GTX an other 2 lcds. Its backwards lol. How do I go about getting this to work. Right now the 2 lcd's hooked up too the 7600 GS appear to be on with black screens.. the lcd lights aren't flashin like they are in standby but i have no picture its just black.

---

### Post by shanep-server on 2013-06-28
Ok well i download each 319 and 304 nvidia drivers.. while attempting to install 319 it said that this driver won't recognise my 7600 GS.. so i installed the 304 driver.. Nvidia settings are now recognizing both cards.. however when I active both the other 2 lcds on the 7600 GS to run 2 xorg servers with twinview clone and I copied the xorg generated script an pasted it too my xorg.conf to save it logged out an logged back in nothing.. the 460 gtx an 2 lcds still work just fine.. the top two still show black but monitors are acting like they are working. When i open nvidia settings it shows all 4 lcds working... confused why they are black screen still.

---

### Post by shanep-server on 2013-06-28
Ok so it appears as though the 7600 GS card has broke something or is error somehow.. the screens are black but when I move my cursor from the bottom 2 lcds too the top 2 lcds the mouse cursor travels too the top 2 lcds hooked up too the 7600 GS but the cursor is a black X and the space up there is invalid.. i tried to use shutter to capture the background and got an error about invaild space. Not sure what is happening.

---

### Post by jp734 on 2013-06-28
Do some research on what options can you use for your driver. I am using radeon cards and  -   Option "colortiling2d" "off"  - did the trick for me.

---

