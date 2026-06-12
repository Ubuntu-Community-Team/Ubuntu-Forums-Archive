---
title: "new guy, need help installing graphics driver"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by dangerousmouse on 2009-09-11
i got myself an asrock ion 330 for my lounge at the start of the week.  wanted to try linux for  while, so figured i would put it on here before i wipe my main pc!

so, ive been looking around and some of the compiz stuff looks pretty neat.  only problem i have is that i cant enable the visual effects.  im guessing due to the fact that i havent been able to update the bundeld graphics driver to the nvidia one.  im REALLY struggling with this, and finding it quite hard to understand everything i keep reading from google searches.

ran compiz check and this is the result
```
Ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation Device 087d (rev b1)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```running the hardware drivers thingy doesnt throw anything back, so not sure if im doing something wrong!?

i attempted to download and run the drivers from the nvidia site, but double clicking the driver doesnt seem to work for me.

i would really appreciate it if anybody can help, and make it as easy as possible. 

thanks,

---

### Post by theozzlives on 2009-09-11
You could go ```
chmod +x <nameoffile>
```
Reboot, Log in to recovery mode (root shell). change directories to the file and ```
./<nameoffile>
```

---

### Post by dangerousmouse on 2009-09-11
so, this is what i have downloaded [COLOR=Purple]NVIDIA-Linux-x86-185.18.36-pkg1.run[/COLOR] [COLOR=Black]

```
chmod +x [/COLOR][COLOR=Black]NVIDIA-Linux-x86-185.18.36-pkg1.run[/COLOR] [COLOR=Black]
[/COLOR]
```[COLOR=Black]

i do this in terminal, correct?


Reboot, Log in to recovery mode (root shell). [COLOR=Red]change directories to the file[/COLOR] and ```
./[/COLOR][COLOR=Black]NVIDIA-Linux-x86-185.18.36-pkg1.run[/COLOR] [COLOR=Black]
[/COLOR]
```[COLOR=Black]

the bit in red makes no sense to me.  what exactly do i need to do?

thanks.
[/COLOR]

---

