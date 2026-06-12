---
title: "[SOLVED] Compiz. Cube Caps utility missing"
date: 2008-10-06
forum: General Help
---

### Post by chriskin on 2008-10-06
i am running on ubuntu 8.10 and a heavily customized environment via compiz

i would like to make an image of mine take the place of the cube caps
but the cube caps utility is missing :S

I found while searching that i need both the cube caps and the desktop cube utilities to make a custon image get on top of my cube

can someone help me regain the cube caps utility?

---

### Post by thon0925 on 2008-10-19
How did you solve this? I am also using 8.10 and have the exact same problem. I can set a image at the top of the cube, but the bottom remains untouched.

---

### Post by chriskin on 2008-10-20
i do not remember where it is exactly, but i **think** it is in cube deformation or whatever it is called (the one that can make your cube into a sphere etc)
sorry for being so abstract, i am running vista right now and i cannot reboot cause i am downloading something, i will come back with more details in about one hour that the download will complete ok?

---

### Post by thon0925 on 2008-10-20
Ok, I found it. Thanks. :)

---

### Post by Stonedancer on 2008-11-06
For anyone who's still unable to find it. Once you have activated your cube (my default came up as a cylinder?) in the compizconfig settings manager click on the cube options button to enter cube settings. Cube caps are located under the appearance tab.

Now I've found it I suppose it makes sense to start to amalgamate all the different cube functions into one interface.

---

### Post by chriskin on 2008-11-06
if that is a question about the cylinder, all you have to do is go to the deformation options and choose "none" instead of "cylinder" on the last tab

---

### Post by chriskin on 2008-11-06
i do not know, as well , if what you said is true, as there is the choice for the TOP cube cap, not both of them

at least that was the last time i checked, i haven't updated since i installed 8.10

---

### Post by cKGunslinger on 2008-11-09
> **chriskin said:**
> i do not know, as well , if what you said is true, as there is the choice for the TOP cube cap, not both of them

at least that was the last time i checked, i haven't updated since i installed 8.10

Enable the Cube Reflection and Deformation plugin and then go to its properties.  Go to the Deformation tab and select "none" to keep the cube (instead of cylinder/sphere.)  Then to to the Cube Caps tab and enter your images.

This should have you working just like Desktop Cube + Rotate Cube + Cube Caps from before.

---

### Post by Scubidus on 2009-05-12
This actually does not solve this particular problem of actually getting the cube caps functionality, With this solution you do not have the effect such as being able to leave the cube on the actual cap displaying only the picture. But none the less this will put pictures on the caps of the cube if that is all you wanted

---

### Post by Won1der on 2010-04-28
Cube reflection and deformation option was missing in Lucid, after a bit of searching I came upon a solution from [https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

Run the following in a terminal and hopefully it will solve your issues too.

sudo apt-get install  compiz compizconfig-settings-manager  compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra  emerald librsvg2-common

and then

compiz --replace

I know you probably don't need all of these but I didn't have time to sort through them and find the one that made the change.

---

### Post by zcahfg2 on 2010-10-17
> **won1der said:**
> cube reflection and deformation option was missing in lucid, after a bit of searching i came upon a solution from [https://help.ubuntu.com/community/compositemanager/compizfusion](https://help.ubuntu.com/community/compositemanager/compizfusion)

run the following in a terminal and hopefully it will solve your issues too.

Sudo apt-get install  compiz compizconfig-settings-manager  compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra  emerald librsvg2-common

and then

compiz --replace

i know you probably don't need all of these but i didn't have time to sort through them and find the one that made the change.

Just applied your method - it brings up all the options but none of them are working on Ubuntu 10.0.4

---

