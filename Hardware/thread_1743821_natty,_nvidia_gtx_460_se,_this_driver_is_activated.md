---
title: "natty, nvidia gtx 460 se, this driver is activated but not currently in use"
date: 2011-04-29
forum: Hardware
---

### Post by Pikkolo on 2011-04-29
Hello :)

After installing natty, I got this message

this driver is activated but not currently in use


on the bottom of the Additional Drivers gui.

On the header, it says : No proprietary drivers are in use on this system


I must say that I have found the Nvidia Control Panel being already installed after the first boot after installing, that looks strange.

But I want to have the proprietary drivers working fine, may I ask for your help ?


Cheers

Marco

---

### Post by crustyBarnacle on 2011-04-29
Pikkolo,

I'm getting the exact same message. Just upgraded to Natty.

```
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GS] (rev a1)
```

*NVIDIA X Server Settings* is installed and works. :-/

---

### Post by spikoley on 2011-04-30
There is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207") on this issue.  Add your details to the bug report, so it will get fixed sooner.

It looks like this issue is caused by jockey (Additional Drivers).

---

### Post by Pikkolo on 2011-04-30
Posted my same post here as a comment to that bug report, thanks you all :)

---

### Post by crashed111 on 2011-04-30
Looking at the bug report this may have something to do with issues a few are experiencing with Unity (Including myself) 

Lets hope it gets resolved.

---

### Post by marek_online on 2011-04-30
You might try Khodeir's instructions here

[http://ubuntuforums.org/showpost.php?p=10744546&postcount=9](http://ubuntuforums.org/showpost.php?p=10744546&postcount=9) 

There seems to be a problem with nvidia drivers not being able to compile due to lack of kernel headers on the system.

Note though that you should check which headers your own system needs by checking your kernel version at the command line with : ```
uname - r
```

---

### Post by Lorribot on 2011-04-30
I am also seeing this on a Dell Latitude D620 with nVidia 7600 go chipset.

I tried the fix but it made no difference.

I am using the recommended version will try and get the Version 173 ones and see if they make a difference.

---

### Post by MatNewman on 2011-04-30
Have exactly the same issue.

Uninstalled and reinstalled NVIDIA drivers (270.41.06) several times, reset **/home/usr/.nvidia-settings-rc** reinstalled headers as suggested in [khodeir]("http://ubuntuforums.org/showpost.php?p=10744546&postcount=9")'s thread ([http://ubuntuforums.org/showpost.php?p=10744546&postcount=9](http://ubuntuforums.org/showpost.php?p=10744546&postcount=9) DONT forget to drop the **-pae** at the end of these commands for the current version), killed and reinitialised **/etc/X11/xorg.conf **numerous times with **sudo nvidia-xconfig**.

Still have "nvidia_current" reported in "Additional Drivers" as "This driver is activated but not currently in use".

Ran **/usr/lib/nux/unity_support_test -p**
________________________________________
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro FX 3800M/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
________________________________________

Running Lenovo W701ds with the Quadro card listed.  Also having issues with external monitors, but can configure Main screen and slide-out screen (normal separate X with Xinerama - still no compiz under 11.04 with this conf).

Display performance very sluggish, nowhere near as responsive on graphics intensive apps as 10.10 was so I'm positive that the NVIDIA card's features and drivers are not being used.

Oh - and unlike Maverick, choosing System-Prefs-Monitors does not report that another driver is in use and would I like to use that config app.  

Also blacklist.conf includes 

#NVidia
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

---

### Post by spikoley on 2011-05-01
> **marek_online said:**
> You might try Khodeir's instructions here

[http://ubuntuforums.org/showpost.php?p=10744546&postcount=9](http://ubuntuforums.org/showpost.php?p=10744546&postcount=9) 

There seems to be a problem with nvidia drivers not being able to compile due to lack of kernel headers on the system.

Note though that you should check which headers your own system needs by checking your kernel version at the command line with : ```
uname - r
```

Didn't work for me too.

---

### Post by Agencyman on 2011-07-21
Same here on the thread starter.

On the good side, I just successfully loaded the F@H6.41 client!  I thought it was going to be impossible after trying so many potential fixes using 1.2 before finding out about the new one, but Wine 1.3 (.x?) just cruised right through it.

Now if the NV drivers for my GTX460SE will get updated, (v2.75 now ),perhaps with some instructions for Linux file structure mods or adds, I can fold SMP2 and GPU3, as in Windoze.

That would go a long way toward keeping me from always feeling compelled to boot Win.

BTW, even Wine 1.3 seeminly cannot deploy GPU Tracker into the operational form after decompressing.  The icon looks like it is ready, but something is still not ready.

Bruce Hinton

---

### Post by Aerogate on 2011-07-26
Same problem here as subject of thread, will post on official bug report too

---

### Post by doogiekd on 2011-07-26
friends,

a temporary fix to this problem that worked for me is to install UNITY 2D from the repositories. using unity 2d does not use the accelerated features of the graphics card. it looks exactly like unity 3d and also runs faster.

1. install unity 2d is in the repositories (synaptic package manager)

2. after installing you should restart your computer.

3. at the login window, select your account. you may have to switch the interface from ubuntu to unity 2d in the menu at the bottom of the screen in the login window AFTER you click on your account name.

4. your computer should boot to unity 2d. you will loose all accelerated 3d graphics - bad for gaming - but it makes the computer work for general purposes.

k.

---

### Post by ZaHACKieL on 2011-07-26
Hi. I'm not completely sure about your card but if if works with Optimus technology then you will not be able to use it on Ubuntu. You will have to stick to the intel gpu. BUT there's an open source solution for that:

[https://github.com/MrMEEE/bumblebee#readme](https://github.com/MrMEEE/bumblebee#readme)

---

### Post by Blitzskee on 2011-07-27
> **ZaHACKieL said:**
> Hi. I'm not completely sure about your card but if if works with Optimus technology then you will not be able to use it on Ubuntu. You will have to stick to the intel gpu. BUT there's an open source solution for that:

[https://github.com/MrMEEE/bumblebee#readme](https://github.com/MrMEEE/bumblebee#readme)

I have the same issue as everyone else when I go into additional drivers it says Driver is activated but not in use.  I have an Dell Laptop that has Optimus NVidia 525m.  I can't even open unity but I can open classic. 

I want to try this solution but how do you even get the intel gpu to select in the first place?

---

### Post by ZaHACKieL on 2011-08-17
> **Blitzskee said:**
> I have the same issue as everyone else when I go into additional drivers it says Driver is activated but not in use.  I have an Dell Laptop that has Optimus NVidia 525m.  I can't even open unity but I can open classic. 

I want to try this solution but how do you even get the intel gpu to select in the first place?

Hi, sorry I'm answering so late! Well...I believe Ubuntu should recognize it automatically.

Do this, go to your terminal and type glxgears, then press enter to run it. If it says that you don't have that package it will say how to install it with apt-get (i.e. follow the instructions)

If you do have it and your gpu is working fine and it has been detected you will get a windows with three gears.

Try that and let me know what happens

---

