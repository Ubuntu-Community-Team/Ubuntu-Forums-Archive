---
title: "New Nvidia Drivers do not work with my nvidia 6150 le"
date: 2009-01-06
forum: Hardware
---

### Post by cheeseburgerman1 on 2009-01-06
Heres the problem. I have an hp a1748x. it has onboard nvidia graphics and the graphics "card" is labeled as an nvidia geforce 6150 le. I was using the hardware drivers application from add/remove to enable the driver it thought worked best with my Graphics card. Heres where the bad stuff happened. after i upgraded to hardy heron, and chose the restriced driver hardware drivers said would work, which was invariably the New nvidia driver, i would be asked to restart. After a restart id get my login screen with what was probably 1440 x 900 display resolution which is the max my monitor allows. I would login though, and i would get a black screen with my monitor saying input not supported. I tried installing different drivers but every time id enable a driver in hardware settings itd go right back to not working. What i then realized after i unistalled all my window managers including compiz, was that every time i used hardware settings to change to the restricted driver it would unload whatever driver i had loaded and change it back to the new. So i got rid of the hardware drivers program and then loaded up the nvidia legacy drivers from add remove, and not finding anyway to select them i just simply tried a restart to see if it did anything. and boy did it. Ubuntu started up in something called low graphics mode and i had to select my graphics card and everything just to get it to work. so im like ****, i screwed up. so i do a little searching and this guy talks about this app called envyNg which installs graphics card drivers. I go get it from synaptic and run it. I have it just install the nvidia drivers using automatic detection. It does it, says i need a restart, and it gets back up i log in, boom same problem. Also, i forgot to mention, every time the screen would turn black and say input not supported, id have to load recovery ubuntu and reset the xserver driver settings. which was kind of a pain in the *** but hey it worked and it didnt require much thought. So then i get it back up and i try envyNG again and i set it to let me choose the driver i want. i know it installed the newest one, so i try the oldest one thinking its old, tried and true so it must work. Wrong, i get the whole ubuntu is running in low graphics mode thing again. so i realize that the old drivers really are too old for my system. so i get it all back up, and load envyng again and try the middle option. there were only three and i had tried the new and old so maybe this was the current. well whatever i chose it, let envy load the drivers and restarted. Presto it works just as i had it set up in fiesty fawn. but now i wanna know, how to i get either the new drivers to work, or get the current drivers to allow me the maximum resolution that i know both my card and monitor support? sorry about the brick of text i dont really know how to make it better though. thanks.

---

### Post by cariboo on 2009-01-06
The drivers aren't the  problem, it is your monitor that isn't getting detected properly. It may be that the modules isn't being built properly. Have you got the latest kernel and restricted modules? you should have have build-essential installed before installing the latest drivers. I have the same graphics adapter on my motherboard and have never had a problem with it, from Dapper up through Intrepid.

Jim

---

### Post by cheeseburgerman1 on 2009-01-06
> **cariboo907 said:**
> The drivers aren't the  problem, it is your monitor that isn't getting detected properly. It may be that the modules isn't being built properly. Have you got the latest kernel and restricted modules? you should have have build-essential installed before installing the latest drivers. I have the same graphics adapter on my motherboard and have never had a problem with it, from Dapper up through Intrepid.

Jim

ah, im kinda new, so how would i find out these things, and what is build essential?

---

