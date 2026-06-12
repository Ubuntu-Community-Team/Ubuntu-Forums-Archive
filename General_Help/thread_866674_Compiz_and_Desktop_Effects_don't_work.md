---
title: "Compiz and Desktop Effects don't work"
date: 2008-07-22
forum: General Help
---

### Post by sirostr on 2008-07-22
Hello
I have a problem
When I type
```
glxgears
```
The gears are working, so I have 3D drivers.
But when I want to turn Desktop Effects on I get the warning:
[IMG]http://i168.photobucket.com/albums/u195/Drzamich/Fora/Screenshot-1.png[/IMG]
When I type
```
compiz
```
I get
```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```
I installed Advanced Desktop Effects with
```
sudo aptitude install compizconfig-settings-manager
```
But when I want to open it in System->Preferences->Advanced Desktop Effects I get this
[img]http://i168.photobucket.com/albums/u195/Drzamich/Fora/Screenshot-4.png[/img]

**What should I do? I really take care of this.**

---

### Post by uberlube on 2008-07-22
install xgl from the repos and reboot.

---

### Post by sirostr on 2008-07-22
I'm lame in Linux :)
So could you tell me exactly what I have to do? :)

---

### Post by Kevbert on 2008-07-22
What's your graphics card make and model ?  If you go to Accessories-Terminal and enter the command line
```
lspci
```
the last line of the text that is displayed should tell you the information.
Please post it here by highlighting it with the mouse and selecting Edit-Copy from the terminal window and using Ctrl+P to paste it here.

---

### Post by sirostr on 2008-07-22
Well, I'm not SO lame - I know how to copy and paste text :)
I have nVidia GeForce 8800GT
```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
```

PS: i used copizcheck and I get this:
```
drzamich@drzamich-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GT (rev a2)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) Y

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) Y
drzamich@drzamich-desktop:~$ WARNING: modinfo for module nvidia_new failed: modinfo: could not find module nvidia_new

WARNING: modinfo for module nvidia failed: modinfo: could not find module nvidia

WARNING: modinfo for module nvidia_legacy failed: modinfo: could not find module nvidia_legacy
```

---

### Post by sirostr on 2008-07-22
bump... can ANYBODY help?

---

### Post by SunnyRabbiera on 2008-07-22
This can depend on the video card, as some vid cards dont like compiz.
But your Nvidia might not work, some of them are twitchy.

---

### Post by Flimm on 2008-07-22
Is there a restricted driver for your graphics card? Click System, Administration, Hardware Drivers and see if any drivers are listed there.

---

### Post by SunnyRabbiera on 2008-07-22
Also try envy too, though its not guaranteed.

---

### Post by sirostr on 2008-07-23
> **Flimm said:**
> Is there a restricted driver for your graphics card? Click System, Administration, Hardware Drivers and see if any drivers are listed there.
[IMG]http://i168.photobucket.com/albums/u195/Drzamich/Screenshot-1-1.png[/IMG]

---

