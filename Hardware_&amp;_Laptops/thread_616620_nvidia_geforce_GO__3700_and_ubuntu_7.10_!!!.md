---
title: "nvidia geforce GO  3700 and ubuntu 7.10 !!!"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by kayzar03 on 2007-11-18
hi all !

i am a new user of ubuntu 7.10 and what !! :confused::confused:

when i want to activate my graphic card  ( nvidia geforce go 7300 ) ihave this message when i want to activate effects on desktop 


The software source for the package

   nvidia-glx-new

 is not enabled


this is the configauration of my pc TOSHIBA SATELLITE 

produal core 2*1.6
NVIDIA GEFORCEGO 7300

i think that you will help a noob like me:popcorn:

---

### Post by kayzar03 on 2007-11-18
is there a driver for my card  !!!  plz heelp

I have a lot of work to do !

---

### Post by kayzar03 on 2007-11-18
is there no one who can answer me :(:(

---

### Post by dfreer on 2007-11-18
No need to bump so much, it's only been an hour :( 
When you go to System > Administration > Restricted Drivers Manager, does it list your nvidia card? You should be able to select the checkbox and install the correct driver that way.

---

### Post by kayzar03 on 2007-11-18
First i want to thank you  second

the problem that i have not the driver ans my card is not listed

plz plz HELP

---

### Post by dfreer on 2007-11-18
Ok, since it's not listed in "Restricted Drivers Manager", you can try this:
```
sudo apt-get install nvidia-glx-new
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
sudo nvidia-xconfig
```

Then reboot. If for some reason X server crashes, you can restore your backup of the xorg.conf file with this command:
```
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
```

Assuming X server didn't crash, you should now be able to use 3D graphics:
```
glxinfo | head
glxgears
```

---

### Post by kayzar03 on 2007-11-18
snif

hey i am not a professional

plz can you show me where to put this or install this on grphic mode

thank you again

---

### Post by kayzar03 on 2007-11-18
bon ca yé j'ai reussi a activer ma carte grace a ce lien

[http://doc.ubuntu-fr.org/nvidia](http://doc.ubuntu-fr.org/nvidia)

maitenant pour les effects du bureau

comment eput ton voir le bureau en 3D (CUBE ) ??

---

### Post by madsmeg on 2007-11-18
i have a 7300GT and it worked OOTB (out of the box)

BUT what defreer is telling you to do is open up a terminal (Applications > Accessories > Terminal)

from there follow his guide, typing in each command (everything in the "Code" box) line by line (pressing enter after each line)

PS, I am not french so if you could translate what you want from your last post i can see what i can do to help.

---

### Post by dfreer on 2007-11-18
Ok :D
Basically, when someone tells you to enter something into the terminal, they are referring to *Applications > Accessories > Terminal*. It is similiar to a DOS prompt, if you are used to Windows operating Systems. Once the terminal opens, you should see your username, the computer's name, the current directory, and a symbol that is called the **prompt**. It'll look something like mine shown below:
```
daniel@danpc:~$
```

In this case, daniel is my username, danpc is my computer's name. and ~ represents my /home/daniel/ directory, where all of my documents are stored. The prompt is $.

So in order to get your video card working, I want you to open the terminal, and install the correct video driver for your video card. The command you need to copy+paste into the terminal is this:
```
sudo apt-get install nvidia-glx-new
```

This first time you use the sudo command, it will ask you to enter your user password, so go ahead and do so. This sudo command basically lets your normal user account have administrative powers, and it will not ask you for your password again for certain amount of time (like 5-15 minutes).

It'll download and install the driver, but we will still need to enable it. So first, we'll backup your old configuration file, with the following command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
```

Then, we will use a utility nvidia provides us with to create a new configuration file. 
**EDIT** I've added some extra arguments to this command for compiz-fusion to work correctly, highlighted in bold below:
```
sudo nvidia-xconfig **--composite --add-glx-with-composite --add-argb-glx-visuals -d 24**
```

Now, everything should be ready, and you should be able to restart your computer. Just in case anything goes wrong with the new configuration file, you can use the old one to fix things. Once the computer reboots, if everything is working correctly you should be able to log in as normal. 

If it doesn't work, it'll probably bring up an error message, and then dump you to a virtual console (which is basically another terminal). You can login there, and from the prompt enter the following command to restore your config file:
```
sudo cp /etc/X11/xorg.conf.original /etc/X11/xorg.conf
```
You'll probably want to write that down, before your reboot since you probably won't be able to use the GUI to get online.

If everything worked ok from the beginning, and you are able to login, you can run those last two commands in terminal just to make sure your driver installed correctly:
```
glxinfo | head
```
```
glxgears
```
The last one is a sort of framerate test, it'll just show a graphic of gears spinning, and after a few seconds it will show in the terminal the average amount of frames you are getting. With my Geforce Go 7400, I can get anywhere from 2400-3500 FPS.

Hope this helps!

---

### Post by kayzar03 on 2007-11-18
oh sorry

i want to say that i succeded to activate my card with this link

[http://doc.ubuntu-fr.org/nvidia](http://doc.ubuntu-fr.org/nvidia)

and now i want to see my desktop to 3D MODE (CUBE) ?? how can i do this !! i have alredy activated extra mode from effects

thanks to all of you

---

### Post by dfreer on 2007-11-18
If you notice, the link you just posted pretty much covers exactly the same steps I just led you through. The only difference really (as far as I can tell, with a translator) is that they are wanting to add --add-argb-glx-visuals -d 24 to the nvidia-xconfig command, which will probably be needed to get compiz fusion borders set correctly. I've updated my instructions in the previous post to reflect this.

Just follow my previous post's instructions, and then once it's setup I'll guide you through getting compiz-fusion working. ;)

---

### Post by kayzar03 on 2007-11-20
thank you

---

### Post by dfreer on 2007-11-20
So does that mean everything is working kayzar03? You're welcome!

---

