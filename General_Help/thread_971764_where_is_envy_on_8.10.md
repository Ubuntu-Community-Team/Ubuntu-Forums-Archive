---
title: "where is envy on 8.10?"
date: 2008-11-05
forum: General Help
---

### Post by sickman666 on 2008-11-05
Hello everyone! Love ubuntu so much had to get the upgrade. the problem is i am having problems with my graphics card...ATI radeon 9600. I wanted to use envy to config my card for me because every thing is HUGE and low resolution but when i look.....i cant even find the damn thing. envy is installed so it says but i can not find it? anyone else have the same problem or know how to fix it? thanks a lot:confused::guitar:

---

### Post by renzokuken on 2008-11-05
why use envy? is the Restricted Drivers Manager not working?

if you really must use envy and you already have it installed you can invoke it from the command line

```
envy
```

---

### Post by sickman666 on 2008-11-05
The hardware driver section is there but I enable the ati driver, restart the computer and it goes right back to the generic crap. I try typing envy in the terminal but that isnt working either. I also noticed that the PLACES tab with my folders in it(music,pictures,videos,etc....they arent working either. Thanks

---

### Post by TyTiger on 2008-11-05
> **renzokuken said:**
> why use envy? is the Restricted Drivers Manager not working?

if you really must use envy and you already have it installed you can invoke it from the command line

```
envy
```

Becuse Envy is awsome beyond human interpitation :P it sets xorg up correctly the way the should be and auto compiles the driver kernel so you dont have to do it..

but yea type 
```
sudo envyng -t
``` 
in youur command line. 

I too had problems with finding envyng on 8.10 untill i realised it was staring me in then face :) but be warned, i also had problems using it on my Toshiba Satellite Pro, ive since downgraded that to 8.04 and having to put up with the vesa generic driver since the new nvidia one for geforce 4 is a total fail :(

---

### Post by sickman666 on 2008-11-05
Thanks for the quick response. I tried it but computer states envy cannot be found....its installed though.

---

### Post by DJ_Peng on 2008-11-05
Envy is now called [EnvyNG]("http://www.albertomilone.com/nvidia_scripts1.html"), and has been since Hardy, and it's in he Universe repo. But if you need the legacy Nvidia drivers check Alberto's blog. There are some issues that are partially resolved in intrepid-proposed.

---

### Post by jdackle on 2008-11-05
Is envy installed from a .deb package (i.e. through synaptic/adept/apt-get)?

If so, at a terminal:
```
dpkg -L envyng
``` should list it's installed files.
If envyng is NOT the name of the actual package, then try:
```
dpkg -l envy
``` which should give you a list of all packages containing "envy" in their names.

NOTE 1: I may have switched the uper and lowercase meaning of "-l"/"-L"... But you'll figure it out... :mrgreen:
NOTE 2: You can also use e.g. synaptic to look for the package and get its list of files.

---

### Post by sickman666 on 2008-11-05
Well i got the command to work but when i restart the computer it goes right back to the same settings. i went in and removed the video card drivers and tried again but still the same. the difference is now when i go into hardware drivers ati isnt listed at all...boy what a pain.

---

### Post by superm1 on 2008-11-05
The 9600 is NOT supported by the proprietary driver in 8.10 atm.  You won't be able to install a functional driver even with envy.

Follow this bug for more information:

[https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

---

### Post by TyTiger on 2008-11-05
> **sickman666 said:**
> Well i got the command to work but when i restart the computer it goes right back to the same settings. i went in and removed the video card drivers and tried again but still the same. the difference is now when i go into hardware drivers ati isnt listed at all...boy what a pain.

Thats EXACTLY the problem i was having, aswell as weird resalution settings. (nVidia Geforce 4 Go (Legacy :) ))

---

### Post by sickman666 on 2008-11-05
I may have to go back to 8.04 to get my stuff working better. Is that what you said you did?

---

### Post by superm1 on 2008-11-05
> **TyTiger said:**
> Thats EXACTLY the problem i was having, aswell as weird resalution settings. (nVidia Geforce 4 Go (Legacy :) ))
Similar problem, NVIDIA doesn't have support for the legacy cards in their binary drivers yet.  I don't have that bug handy though.

---

### Post by sickman666 on 2008-11-05
okay. i did something..ha ha.I uninstalled all the video drivers...fglrx,xorg and used envyng to install driver. here is where it gets weird. i restarted my laptop(gateway 7305) and when it rebooted my resolution was at 1280x800. compiz wouldnt work. so i went into appearance and clicked on advanced effects and it told me to enable 3d acceleration....I did....oh good gravy it had to restart. as soon as it restarted i was back to square one again.

---

### Post by Roasted on 2008-11-16
> **superm1 said:**
> The 9600 is NOT supported by the proprietary driver in 8.10 atm.  You won't be able to install a functional driver even with envy.

Follow this bug for more information:

[https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.edge.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

Uh.. it's not? I have the 9600 with 177 drivers running and it's fine... and considering that I need the proper drivers to run compiz (which I have running) I'm going to take a stab in the dark here but I'd say it's supported...

---

### Post by 3n1gm4 on 2008-11-29
> **Roasted said:**
> Uh.. it's not? I have the 9600 with 177 drivers running and it's fine... and considering that I need the proper drivers to run compiz (which I have running) I'm going to take a stab in the dark here but I'd say it's supported...

How did you do? I hate this 800x600 :O

I upgraded then i got this crap :(

---

