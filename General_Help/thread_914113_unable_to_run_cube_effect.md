---
title: "unable to run cube effect"
date: 2008-09-08
forum: General Help
---

### Post by shantanu kulkarni on 2008-09-08
I use ubuntu 8.04 

but i am unable to use cube effect
i have checked all the necessary options in compiz config setting manager 

i am able to run every other effects life pain fire on screen, water effect etc

my computer config is

AMD X2
1gb ram
on board graphics card 


plz help

---

### Post by Infinite Indefinite on 2008-09-08
Have you got four workspaces?

(If not, then just right-click on the desktop spaces at the bottom right corner, select preferences, and then set workspaces to four.)

Also, have you gone to Preferences > Advanced Visual Effects (or ConfigCompiz Manager )> General Options > Desktop Size and set the number of horizontal spaces to 4?

---

### Post by Therion on 2008-09-08
> **shantanu kulkarni said:**
> ... on board graphics card 
Can you be more specific?  

An onboard graphics chipset may or may not support Compiz.

---

### Post by shantanu kulkarni on 2008-09-08
thank you it worked

can u tell me how to apply different wallpaper in different sides

---

### Post by ubunt_user on 2008-09-08
You can even right click on the bottom right hand corner of the desktop and specify the no. of workspaces.

Thanks Infinite Indefinite. I didn't notice that its possible through Preferences also :)

---

### Post by BenAshton24 on 2008-09-08
Just triple check that you have rotate cube checked, it's a common mistake. i forgot to check it when i last installed compiz and was baffled by why it didn't work for about a week. also another big thing, don't forget to run the compiz replace command
> compiz --replace

hope i helped :D

---

### Post by shantanu kulkarni on 2008-09-08
but it is not forming a 3d cube 
it is like a strip

---

### Post by ubunt_user on 2008-09-08
I guess the procedure will be same to change the wallpaper. In this case you would have to got to each workspace and specify the wallpaper (Right clk on desktop).

---

### Post by Infinite Indefinite on 2008-09-08
> **shantanu kulkarni said:**
> thank you it worked

can u tell me how to apply different wallpaper in different sides
I haven't tried it myself, but here's a link that deals with it:

[http://forum.compiz-fusion.org/showthread.php?t=6199](http://forum.compiz-fusion.org/showthread.php?t=6199)

---

### Post by shantanu kulkarni on 2008-09-08
cube is forming a 3d structure

it is formed like a straight line

---

### Post by Therion on 2008-09-08
> **shantanu kulkarni said:**
> cube is forming a 3d structure

it is formed like a straight line
[This tutorial](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion) will show you how to set up the Desktop Cube.  See: **Getting the Cube**.

If your onboard graphics do not support 3D graphics, or the chipset does not have sufficient memory, however, you won't be able to get the Cube.  That's why I asked what integrated graphics chip-set you have.

---

### Post by shantanu kulkarni on 2008-09-09
on pressing shortcut for cube i get all desktops in linear order
there is no 3d effect plz help

---

### Post by Infinite Indefinite on 2008-09-09
First off, make sure that you go to System > Preferences > Advanced Visual Settings (or CompizConfig Settings Manager) > General Options > Desktop Size.

Set Horizontal Virtual Size to 4, and leave Vertical Virtual Size and Number of Desktops at 1.

Go Back and make sure that both Desktop Cube and Rotate Cube are enabled. 

Ensure that nothing else in the Desktop Category is enabled.

That should normally suffice.

---

### Post by Pablo Pablovski on 2008-09-09
> **shantanu kulkarni said:**
> on pressing shortcut for cube i get all desktops in linear order
there is no 3d effect plz help

Sounds like you've got the Expo plugin working, rather than 3d cube - maybe you could check the settings in CCSM?

---

### Post by Idefix82 on 2008-09-09
You might be using the wrong key short cut. Have a look at the "key bindings" section in the configuration of the rotating cube. Or just try ctrl-alt-left and ctrl-alt-right. If I remember correctly, you get the strip by pressing ctrl-alt-down.

---

### Post by ellalan on 2008-09-09
Hi
1.Cube Reflection &Deformation-Deformation is- none
2.Desktop Cube-Opacity during rotation=0, Opacity when not rotates=0
3.Rotate Cube-Bindings--Enable(mouse)-see whether you see like this-
<control><Alt><left click>
To get the rotating cube you have to press ctrl+Alt+left mouse button.

HTH.

---

### Post by lik2writ on 2008-09-09
This was very helpful, I'm enjoying the effects for the first time.

---

### Post by greyowl on 2008-09-12
I got the cube working ... sort of.
It works fine w/o any windows open. Once I have one open though the whole system crashes and I taken back to the login screen.......

Fresh wubi install of Hardy on new HP desk

---

### Post by EnGorDiaz on 2008-09-13
enable cube on ccsm (if you dont have this installed then install it buy synaptic

then press

ctrl alt left mouse button

---

### Post by greyowl on 2008-09-13
Sorry about my unclear post.
Cube is working ctrl-Alt mouse does the trick when NOTHING IS OPEN, but as soon as I have any window, (mozzilla etc) open and I try to change desktops using (ctrl-Alt mouse), hardy crashes and I am sent back to the log in screen. It changes desktops fine with the wheel on my mouse and by clicking on the bottom right corner thing ..... with windows open

I ran Gutsy and went through all the problems with cube ... I am lovin hardy. I had nice resolution and the cube up in like an hour.
 I can handle the command line .... give it to me!

---

