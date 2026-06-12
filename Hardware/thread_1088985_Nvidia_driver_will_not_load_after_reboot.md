---
title: "Nvidia driver will not load after reboot"
date: 2009-03-06
forum: Hardware
---

### Post by shayes on 2009-03-06
Im a super noob when it comes to ubuntu but I work in the IT field networking windows machines so I figured I could learn it. Well i instlled it on this machine, installed nvidia driver 180.11 manually no problem. I built another machine with an AM2 socket board that has the Nvidia Nforce 430 chipset an GeForce 6150 SE on board. The problem is when I installed the recommended Nvidia driver and reboot I get a error message saying the nvidia kernel failed to initialize then it loads low graphics mode. I have been working on this for better part of 2 days and have tried several step by step solutions i have found in these forums. Nothing has worked so far. I checked the synaptic manager and i believe all the files i need are installed. 

System Specs:
Biostar MCP6PB M2+ GeForce 6150 Socket AM2+ MB 
MD Athlon 64 X2 4200+ Socket AM2 CPU 
2GB DDR2 3200
Seagate 80GB HDD ATA-IDE

I attached a copy of the xorg.conf file please let me know any other log files that will help diagnose this problem. This xorg.conf file was remade because the X server would not start up so i used recovery console to fix the x server.

---

### Post by pedja_portugalac on 2009-03-06
No idea what can be problem but I had never any problem with officially recommended driver by Ubuntu, which is still 177. If you have that problem for 2 days, maybe you should uninstall 180 driver and enable the one from System > Administration > Hardware Drivers?

---

### Post by shayes on 2009-03-06
I have tried 177, 173, 96 and they all produce the same effect. Also the 180 showed up as the recommended driver. I even tried a fresh install of ubuntu intrepid and select the recommended driver and still produces this error.

---

### Post by shayes on 2009-03-06
Something I should add. When running the live cd to install it will load because I hear the startup sound file but the display is black. I have run the cd in safe graphics mode. Then I can see the installer dialog box in 800x600 res.

---

### Post by RaiCoss on 2009-03-06
> **shayes said:**
> Something I should add. When running the live cd to install it will load because I hear the startup sound file but the display is black. I have run the cd in safe graphics mode. Then I can see the installer dialog box in 800x600 res.

It could be your monitor, try a different one if you can. I had all sorts of stupid problems, untill I bought a new monitor, so you may want to check that out.

---

### Post by pedja_portugalac on 2009-03-06
Sorry it wasn't an easy issue. Did you try to disable visual effects under System > Preferences > Appearance ? Or tuning with xvidtune inside Terminal? Maybe it's the monitor specific problem. I had one, at home, LG LCD monitor didn't fit well so I had to tun it with xvidtune.

---

### Post by turshu on 2009-03-06
hey,

try using this way. totally worked for me. i'v tried really hard to make it running on my ubuntu but couldnt make it work . firstly it was sayin 180.29 were installed and when restart my pc it forces it self to using generic mode. so try this link here 
[http://samet.kilictas.com/how-to-install-nvidia-driver-18029-on-your-ubuntu/](http://samet.kilictas.com/how-to-install-nvidia-driver-18029-on-your-ubuntu/)

---

### Post by pedja_portugalac on 2009-03-06
> **shayes said:**
> Something I should add. When running the live cd to install it will load because I hear the startup sound file but the display is black. I have run the cd in safe graphics mode. Then I can see the installer dialog box in 800x600 res.
Try xvidtune command if you see any prompt, you could change resolution of your monitor and when it's OK save it to configuration file.

PS. Now I am sure it's monitor configuration problem.

---

### Post by shayes on 2009-03-06
I'll try switching out the monitor see if that helps. As far as using the xvid command line if I install a driver then reboot and I get the kernel failed to initialize error when would use that command? The debugger loads and let's me view logs and change the xorg.conf file but when would I use that command if the kernel already failed.

---

### Post by erudite on 2009-03-06
Firstly you need to remove the ubuntu drivers and also the restricted drivers then follow these instructions.  They worked a treat for me when I was having problems.  nvidia-kernel-common needs to be removed for sure.


[quote=nightcast 2000 from nvidia forums]1)Make sure you have the kernel source and kernel headers
Code:
```

sudo apt-get install kernel-source and sudo apt-get install kernel-headers
```

(enter your password when asked)there are a couple of things that need to be installed,so I would probably run sudo apt-get build-dep nvidia just in case.

2)once you have installed the needed packages,re-boot and then select your latest kernel with single user mode that is in brackets and boot into that.

3)Once you get to the dialogue box,select the root shell option and give your password.
When you get the "#" prompt,type in
Code:

```
sudo telinit 3

```
and wait for it to load up.

4)If you get the GDM login screen,try and press Alt+Ctrl+F3 all at once,that should give you the black and white login asking for your login name and password,if you already get that screen,just go ahead and type them in.

5)When your logged in,the next important command to run first is
Code:

```
sudo /etc/init.d/gdm stop
```

and give your password again.

6)When GDM stops,navigate to where you have downloaded the driver(typing dir should show it up straight away assuming you have downloaded it to your home folder)if not,type in sudo updatedb and then type locate NVIDIA-Linux-x86-XXX.XX-pkg1.run(the X's stand for the driver version you have).

7)When you have found your driver,just type in sudo sh and then the name of the driver and follow the prompts(click yes to everything)and it should say the installation is complete.

8)When you're done you have two options,the first one would be to test it straight away with
Code:

```
startx
```

and it should take you to the desktop.If evertything is sucessful,just select logout.Don't worry about the error messages above the prompt afterwards,just type
Code:

```
init 6
```

and it will go through the re-boot procress.
When you've rebooted just select the latest kernel that you used single mode with and it should boot as normal.
[/quote]

---

### Post by shayes on 2009-03-06
Just got home to try these steps. Thx BTW for all the help this community is great. Also wanted to ask, whats the best method to ensure i remove all the drivers. I removed everything nvidia in the synaptic but Im sure im missing something.

---

### Post by shayes on 2009-03-06
Ive tried to complete the steps but already hit a snag. In the first step it states make sure you have kernel-source an kernel-headers. When i run those lines of code i get this

```
$ sudo apt-get install kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kernel-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-source has no installation candidate
```

I tried adding the nvidia-kernel-source 180 in synaptic and the linux-header that match my kernel but still got same return.

---

### Post by erudite on 2009-03-07
Don't worry about kernel-source or kernel-headers after all.

Just make sure all the things that say "linux-restricted-modules" are removed.

Just type linux-restricted-modules into synaptic uner name search.

Then try the other steps for installing and you should be away.

---

### Post by shayes on 2009-03-07
The monitor was the problem. Switched out monitor and install 180 no sweat. Thx for all the help everyone.

---

### Post by eival on 2010-02-10
> **erudite said:**
> Firstly you need to remove the ubuntu drivers and also the restricted drivers then follow these instructions.  They worked a treat for me when I was having problems.  nvidia-kernel-common needs to be removed for sure.

THIS WORKED!!!:popcorn:

i can reboot an it loads up the latest driver thanks!

---

