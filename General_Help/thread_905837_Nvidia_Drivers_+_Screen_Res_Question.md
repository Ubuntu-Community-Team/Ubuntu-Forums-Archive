---
title: "Nvidia Drivers + Screen Res Question"
date: 2008-08-30
forum: General Help
---

### Post by Jinkzt3r on 2008-08-30
I must be annoying you guys :(.

Just a couple of more questions!

I was just curious as to how I would install the Nvidia drivers for my Nvidia GeForce 6800 graphics card? I'm trying to find some guides but I just can't seem to find the right guide for me :(.

Also, I read some where that I can edit the screen res via the Nvidia control panel after I find install the drivers? Right now my computer is stuck on an 800x600 screen res yet in Windows my max resolution can be 1600x1200.

Thanks again,

Jinkzt3r.

---

### Post by drs305 on 2008-08-30
I have a Nvidia GeForce 7600 and have successfully used EnvyNG to install my drivers. Some people prefer other methods, such as using the nvidia-glx series which are also in the repositories.

EnvyNG is available in synaptic and is listed as "envyng-gtk" or you can install it via command line with 
```
sudo apt-get **install** envyng-gtk
```

Once installed, you access via the menus: System Tools, EnvyNG. Select Nvidia and automatic recognition.

Settings can be set via System, Administration, Nvidia X Server Settings and generically, System, Preferences, Screen Resolution.

---

### Post by Jinkzt3r on 2008-08-30
> **drs305 said:**
> I have a Nvidia GeForce 7600 and have successfully used EnvyNG to install my drivers. Some people prefer other methods, such as using the nvidia-glx series which are also in the repositories.

EnvyNG is available in synaptic and is listed as "envyng-gtk" or you can install it via command line with 
```
sudo apt-get envyng-gtk
```

Once installed, you access via the menus: System Tools, EnvyNG. Select Nvidia and automatic recognition.

Settings can be set via System, Administration, Nvidia X Server Settings and generically, System, Preferences, Screen Resolution.

Awesome, will try after I restart, Firefox was freezing for some reason.

---

### Post by jonian_g on 2008-08-30
Use EnvyNG to install the drivers. To install envy:

```
sudo apt-get install envyng-gtk
```

Then go Applications>System tools>EnvyNG and install your drivers. The envy interface is self explanatory.

If you have problems with the resolution, this means that your monitor is not recognized. To solve this problem open a terminal and type:

```
sudo displayconfig-gtk
```

On the window that comes up look if your monitor model is next to "Model:". If its not, click on it and find it in the list.
If its not in the list, instert in the drive the disc that came with your monitor, click "add" and locate the .inf file in the disc. If you don't have the disc choose a generic model with the maximum res your monitor can handle.

---

