---
title: "ctrl alt backspace"
date: 2008-08-25
forum: General Help
---

### Post by mburg23 on 2008-08-25
im new to x i installed ubuntu yesterday and was working really awsome till i tryed install beryl and it stuffed somthing up with the graphics ect. as im a noob i didnt know how to fix it so i decided to just reinstall from the livecd so i did that and have got it working good again. but everytime i press ctrl alt backspace or try and change session by exiting the current session it just goes to a black screen and wont load.  any ideas. when i installed ubuntu this time round i had some troubles downloading some of the updates, it said some of them failed. do you think this may be it.

---

### Post by Crafty Kisses on 2008-08-25
Have you tried reconfiguring X?

---

### Post by marshag63 on 2008-08-25
Ctrl + Alt + Backspace is how you kill an "X" session - it takes you to a console screen (a black screen), so that is working as it is supposed to.  
When you are quitting a "Session," are you using log off or switch user?  If so and you are getting the black screen, then your login manager has a problem (if using gnome, its called "gdm.")

MG

---

### Post by mburg23 on 2008-08-25
kk ty i thought ctrl alt backspace was just a way to change session. im actually using fluxbox and i just rightclick exit to change session and it is doing the same as the ctrl alt backspace just going to the black screen.
when im in gnome and i try and enable the wobbly screen ect cant think what its called off the top of my head the advanced graphics. it says it is unable to enable these graphics. and all that was working till i reinstalled ubuntu after stuffing up with beryl so i dno what ive done i read in another topic that i should try boot into recover mode from grub, and reconfigure graphics, or reconfiguring x like codename said. maybe this would fix both the problems. But i am not sure how to do either of these.

---

### Post by anotherdisciple on 2008-08-26
Just a quick question... why do you want to use Beryl instead of Compiz Fusion? Beryl is a dead project now they Compiz and Beryl have merged. Ubuntu comes with all the effects built in... you only need to install the compiz manager. You do this by opening a terminal (Applications > Accessories > Terminal)and typing"

```
sudo aptitude install ccsm
```


Just a little fyi for when you get some things nailed out or your reinstall.

---

### Post by mburg23 on 2008-08-27
thnx umm i dno like i said i havnt any experience in this kind of stuff so im not sure why im using beryl lol

---

### Post by mburg23 on 2008-08-27
sorry actually i was using compiz fusion wen i first installed ubuntu form the live cd. but then for some reason i decided to try and get beryl dont ask me why well anyone i just followed a guide i found and update or changed somthing with my graphics card and it fuked the whole computers graphics up it changed the resolution ect so i decided just to reinstall ubuntu from the live cd so i did that but it hasnt been the same well the graphic resolution has chnaged bak to normal but i cant get any of the 3d cube or effects to work. i just installed compiz fusion again and its is working well the advanced dektop effects manager is there and installed i can change all the settings ect but they dont seem to take affect i have 3d cube enables and a few other things wobbly screen but none of them work. im thinking maybe when u updated the graphics drivers originally it has done something. is there a way to reconfigure it. any suggestions. just as a test when i go to system/preferences/appearance/visual effects/  it is on none. and wen i try put it on normal or extra it says unable to use effect.  these effects where working wen i first installed ubuntu. so i know it is something ive done wen trying to install beryl the first time, before i reinstalled ubuntu. i think lol.

---

### Post by mburg23 on 2008-08-27
also which i find weird i can put the sabayon live cd in and boot from cd and all the effects work.....im puzzled

---

