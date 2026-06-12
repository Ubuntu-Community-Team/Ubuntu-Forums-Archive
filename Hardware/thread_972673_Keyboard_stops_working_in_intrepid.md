---
title: "Keyboard stops working in intrepid"
date: 2008-11-06
forum: Hardware
---

### Post by allspiritseve on 2008-11-06
Lately I've had some odd things going on with my laptop... I installed Intrepid a couple of days ago, and I've noticed that if I leave the computer running for a while and come back to it, my keyboard does not work, I can't click on any menus, and the right-click doesn't open any menus. I can click on icons, and my power button works. I haven't noticed it happening with any regularity, and I haven't noticed any particular trigger. Could somebody please help me run the right tests and stuff so I can find out what is wrong? I am happy to provide more information, I just don't know how to go about finding the problem.

Thanks,

Cory

---

### Post by TechieAu on 2008-11-06
I have the same problem on Dell XPS M1330 after upgrading to Intrepid. Can't see any trigger either, nor can I see anything related in the sys and user log files...

---

### Post by valahul on 2008-11-06
The similar problem for me on Dell Inspiron 1501. My keyboard not work properly: for example down key produce screen capture! Help, please!

---

### Post by allspiritseve on 2008-11-06
I posted a bug in launchpad, maybe you guys could respond with your problems and we can get some help in fixing this:

[https://bugs.launchpad.net/ubuntu/+bug/294791](https://bugs.launchpad.net/ubuntu/+bug/294791)

---

### Post by LadyOfTheLake on 2008-11-07
Something similar is happening to me, except I can't get into Ubuntu at all because my keyboard doesn't work to login. This started just after I upgraded to Intrepid. There were some issues updating  so I had to boot through recovery mode to finish upgrading. Could this have been the issue? I have an HP Pavilion laptop with a windows partition (that I am using now). I'm a complete beginner at this so I don't know what other information to give but I hope I can fix this! I miss my linuxes....

---

### Post by LadyOfTheLake on 2008-11-07
a

---

### Post by TechieAu on 2008-11-08
I figured out the source of my problem. 

I had followed an advice on how to make brightness adjustment smooth and blacklisted the "video" module in /etc/modprobe.d/blacklist. After that, once I made an brightness adjustment using Fn+Up/Down, the keyboard and menus stopped working.

---

### Post by LunaEqualsLuna on 2008-11-09
This happens to me as well on a fresh install of intrepid on a dell m1210.
My other laptop with hardy never has this problem.

Suddenly the keyboard will stop working and the GUI menus no longer work. It seems to do so at random as well, sometimes it will do it after a few minuts sometimes after a few hours.

I suspect it may have something with the media buttons.

---

### Post by Narshada on 2008-11-09
I have the same problem, although I think it might be linked to the Fn keys and adjusting the brightness as I think it only happens when my laptop is running on battery and that's the only time I alter the brightness in order to conserve power. I guess the answer for now is not to adjust the brightness or at least try it when I'm on AC power to see if it does it then.

---

### Post by damers21 on 2008-11-10
I am having identical problems--a non-responsive keyboard and menu.  It is so frustrating!  I will be clicking that Launchpad link above in just a bit.  For what it is worth, I have a Dell Inspiron 1501.

---

### Post by bijanafx on 2008-11-11
Me too! Intrepid update triggered it on my Dell Inspiron 600m. Can confirm that it is related to the Fn key (outlet & battery, btw).

FYI, temporary fix: pressing Ctrl+Alt+ANY F KEY 1-12 will reverse the locked screen. Still, very annoying.

---

### Post by damers21 on 2008-11-11
I installed an update to xorg yesterday and the problem was cured for when I was on battery power!  Is there a way that I can find a list of all of the updates I have installed so that I can recommend "install update xyz" to alleviate said problem?

---

### Post by slapshots on 2008-11-13
I have an HP dv 9000, and intrepid worked perfectly for the first week, then all the sudden i changed the logon screen to the gnome option, and now whenever i turn on the computer my mouse works, but my keyboard doesn't. since i can't type my password, i can't even access ubuntu right now (i'm working in my visa partition) any clues on how to make it so i can at least get into ubuntu to figure out what's wrong?

---

### Post by the12nv on 2008-11-13
i am having this same issue. i think it is linked with the fn+up or fn+down key combination. I have found that one way to get the keyboard to work again is to simply left click on the battery icon on your task panel.Its annoying but it works for me at least.

---

### Post by emid on 2008-11-24
I have the same issue, the only temporary fix is to do the "Ctrl+Alt+ANY F KEY 1-12" maneuver.  It is definitely related to adjusting brightness on my laptop.

---

### Post by thealsir on 2009-02-19
Same problem here. It seems to spring up whenever I try to adjust the brightness using fn+up/down on my Dell D600 laptop. Brightness adjustment works, but then the graphical interface stops responding to keystrokes and some menus don't expand when clicked. It seems to be limited to X since ctrl+alt+f keys still work and the command shell still responds perfectly well.

I've found that ctrl+alt+backspace (resetting X) fixes the problem without rebooting. Unfortunately, it also logs you out.

---

### Post by trooperchix on 2009-03-16
*Bump*

---

### Post by trooperchix on 2009-03-19
Still having this problem, and from what I read in Launchpad, it is most prevalent in Dell Laptops.  I can't find my old link to that particular thread.  I'm at the point where I have no keyboard upon boot, and limited function of the mouse.  Help!!  I'm sitting on a $2000 boat anchor...

---

### Post by ryodoan on 2009-03-31
Just wanted to throw my hat in the ring.  I am running Intrepid on a Dell Inspiron 6000.

I just installed it over the weekend (its now tuesday) and I am having the same problem.  When I use the Fn key and adjust my brightness (Fn + Up Arrow) my keyboard stops working. 

Also, when I return from hibernation or standby the keyboard does not work.

I will try some of the methods suggested above to regain control and report back.

*edit* ctrl-alt-f(#) works for me.

---

