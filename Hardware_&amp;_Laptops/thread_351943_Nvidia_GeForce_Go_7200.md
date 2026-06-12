---
title: "Nvidia GeForce Go 7200"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by brainslug on 2007-02-02
Hello everyone
I recently bought a HP pavilion dv6000, it has a nVidia Ge Force Go 7200
graphics card. I have tried installing both Fedora Core 6 and Ubuntu but
I still get the same problem and am about to give up on Linux. After both installs and after I reboot the Laptop both distros start to load but just before the GUI is about to load I get a blank black screen and nothing hapens anymore. I'm gesing there is a problem with linux recognizing my graphics
card or maybe I'm doing something wrong. Can anyone help me?

Thanks!

---

### Post by mikewhatever on 2007-02-02
Is there a black screen with no log in option?

---

### Post by Heerm on 2007-05-08
I've got the exact same problem!! And were hoping for some answers in this thread :)
Please people!

Have installed latest Ubuntu 7.04 - but after the splash screen and some load time, the screen goes black.. I get no further.. I actually lot the PC be up all night, but same screen next morning.. 

So, whats the problem people? In the xonf.comf file the nvidia driver says "nv" - so thats OK.. 

Cant figure this one out!.. 

-Heerm

---

### Post by Heerm on 2007-05-27
Bump :)

---

### Post by cptcrunch on 2007-05-27
That's really odd. Can I ask did you manage to get the Live CD that uses the vesa drivers working?

I have a Nvidia GeForce Go 7300 and used this how to to install the latest drivers


[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

Note: In that last step, in order to install the beryl manager just type

sudo apt-get install beryl-manager

---

### Post by gopoo on 2007-05-27
i got my go 7400 working in no time....

probably you can go to console (cntrl + alt+f1) , login , edit /etc/X11/xorg.conf , change in device section to vesa , change resolution to somewhere lower ( like 1024x768) , install nvidia card ( adminstrator -> restricted driver) , change the resolution in xorg.conf to the default you required.


hope this helps. 

:D

---

### Post by tesserakt on 2007-05-30
This problem has been KILLING ME!

I've got a hp dv2000t w/ a GeForce Go 7200 running 7.04.  I'm mediocre when it comes to Linux and I can follow directions, so the fact that the card doesn't appear on this [list]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") makes it a bit out of my league.

The card works fine as a basic display controller, but the key is that on the laptop there's an extra GPU head that I can use to connect to a larger monitor.  Without the special drivers, I can't configure this external head resolution.

The hinge pin of my whole interest in posting this is that I know it can be done.  I had it working ONCE.  Just one time, and the second I disconnected everything I had to start back from square one.  

> 
grant@hephasteus:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)


---

### Post by nbayiha on 2007-06-04
Hej guy i have the same graphics card on  hp dv6040us 
graphic card is Geforce go 7200.
Installing the nvidia driver in Feisty is as easy as My Grandma can do it. Just open synaptic and look nvidia-glx-new and install it. that it's :-D.

Or open a new terminal and paste
```
sudo apt-get install nvidia-glx-new
```
you can test if ur driver are install by 
```
glxgears
```
you should be able  to see three wheels

Hope i help you all

---

### Post by Brinstar on 2007-06-04
don't give up on Linux. At least give Zenwalk a try and make sure you download and install (sh NVIDIA-****.run while in superuser mode or root) the official Nvidia drivers from their site. My Geforce Go 6200 works beautifully.

---

### Post by haythoo on 2007-11-19
Please Heme, I have the same problem with same card....

How I can install ubuntu with this bad card :S

Should I check " Install with driver update CD "?
And from whete I get this CD?

---

### Post by haythoo on 2007-11-19
> **nbayiha said:**
> Hej guy i have the same graphics card on  hp dv6040us 
graphic card is Geforce go 7200.
Installing the nvidia driver in Feisty is as easy as My Grandma can do it. Just open synaptic and look nvidia-glx-new and install it. that it's :-D.

Or open a new terminal and paste
```
sudo apt-get install nvidia-glx-new
```
you can test if ur driver are install by 
```
glxgears
```
you should be able  to see three wheels

Hope i help you all

But How I can Install ubuntu first?
In your way you talk about instaled ubuntu, but our problem is that we can not get the welcome screen on live cd?
how could you install it with your?

---

### Post by slafko on 2008-01-10
> **haythoo said:**
> But How I can Install ubuntu first?
In your way you talk about instaled ubuntu, but our problem is that we can not get the welcome screen on live cd?
how could you install it with your?

You have to load LiveCD with "noapic" option in GRUB.

See [https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)") for help.

---

