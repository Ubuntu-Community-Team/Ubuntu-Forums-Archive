---
title: "[SOLVED] 8600GT drivers DONT WORK in ubuntu"
date: 2008-07-24
forum: Hardware
---

### Post by cowboyup6983 on 2008-07-24
i hope someone here can help me out, im trying not to give up on ubuntu, but i cant get drivers for my 8600GT i have two of these with bridge connection. whenever i go to system>admin>hardware drivers if i enable the "NVIDIA accelerated graphics drivers" and after the reboot, my screen resolution drops to like 640X480 and i cant work like that. so i just dont enable, there must be something wrong with the drivers its trying to install because they dont work propertly. im new to ubnutu and i dont know how to install anything except add/remove options under applications. 

please help or direct me in the right place, i read somewhere about using ENVY but dont even know how to install that. and how to use it.

---

### Post by tackfurlo on 2008-07-24
I would just like to mention that I have a desktop (a system that was custom built as a streaming media server bot never used) with a single 8600GT and it works fine - Compiz, Beryl, etc all run great at 1440x900 res on a dual screen (TwinView) setup and at 75Hz.  The desktop is back to running Windows now (it's a gaming box and it stays offline 24/7 - I would NEVER but a windows box on the net, no matter how much AV it was running.)

I think your problem may be with SLI (the system NVidia uses to bridge the cards together), which the drivers may not support yet.  Anyone have an NVIdia with SLI or maybe even an ATI with Crossfire working?  My card is just a dual head card so I don't know if SLI would work.

Other than that...I have no clue.

---

### Post by Neo0351 on 2008-07-24
pull one of you cards out, then install the drivers using envy.  then run
```
nvidia-settings
```
make sure your settings are right and your card is detected.  make sure everything runs, then install your second card.  im not sure how to enable SLI but i think its through nvidia-settings.  if sli isnt working right, try flipping your cards.

---

### Post by Neo0351 on 2008-07-24
you can install envy like this
```
sudo apt-get install envyng-gtk
```

---

### Post by cowboyup6983 on 2008-07-24
> **Neo0351 said:**
> you can install envy like this
```
sudo apt-get install envyng-gtk
```



dude...i did exactly what u said, i open a terminal type that in. it install the program, then i used the program to auto detect my card, and it install drivers. it ask me to reboot and TADA!!! its working now. I have my drivers and enchance settings are on and now im good. 

now all i have to do is learn how to watch a DVD movie, i downloaded and install VCL media player, cause i use to use for windows, but nothing happens when i say open disc. oh well another nightware, patience. patience.

---

### Post by Neo0351 on 2008-07-24
remember to make this thread as solved.  take a look at this thread for multimedia.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by tackfurlo on 2008-07-24
Glad someone could help him.

As for watching a DVD, you should be sure you have all the gstreamer plugins packages installed and then use totem (the default Ubuntu movie player) to watch them.  The only format I have ever not been able to open with Totem once I installed the "bad" and "ugly" plugins was realmedia, and I didn't need to watch southpark THAT badly anyhow.  Plus the Helix player can decode those.

---

### Post by cowboyup6983 on 2008-07-25
> **Neo0351 said:**
> remember to make this thread as solved.  take a look at this thread for multimedia.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

OMG thanks to everyone for all the help. i had my best night ever with Ubunut. I got my nvidia cards working with the right drivers, was able to add programs and codecs for watching my DVD's and even spent last 2 hours setting up VMware Serve for XP just for when my school stuff needs to be done on IE. i hate that so much. 

other than IE for school, i dont think im going back to windows. i am so happy with my experience today and look forward to happiness in my new OS. 

again thanks to all!!!

---

