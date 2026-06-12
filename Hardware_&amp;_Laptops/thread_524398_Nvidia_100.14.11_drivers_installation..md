---
title: "Nvidia 100.14.11 drivers installation."
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by damansandhu on 2007-08-13
Hi , i am new to linux , just installed Kubuntu 2 days ago , its good , the problem i am facing is that i am unable to install nvidia graphic drivers for my 7600gs agp card , i read every forum regarding to this , but didn't succeeded in installing drivers , so plz somebody explain me how to install nvidia video drivers , as i am new to linux.

---

### Post by Saner on 2007-08-13
Where are you getting stuck ?

---

### Post by damansandhu on 2007-08-13
first i tried installing drivers by typing in terminal
sudo apt-get install nvidia-glx-new
something download and even installed , but still i didn't get drivers.
then i downloaded drivers from nvidia website
then i pressed ctrl+alt+f1
then i wrote sudo /etc/init.d/gdm stop
then it said that is wrong command , something like this

it will be good if you explain me in detail.

---

### Post by FMaz008 on 2007-08-15
I have trouble installing the NVidia driver under Ubuntu Feisty too.

But to answer your question: to shutdown the X, when you are in it, just do CTRL+ALT+BACKSPACE.

Then, after you have downloaded the .run file from NVIDIA, you can do:
sudo sh NVIDIA[..??..].run

the [..??..] is the rest of the filename that I don,t remember.


My problem is that I have an onboard GeForce 7025, and it seem that I REALLY need this driver.
But when the installation wizard starts, it give me a bunch of error, telling me that the installer will attempt to recompile the Kernel, then that my Xorg is modular and that a path can't be found.

At the end, it tell me that the driver has been installed in a spcific path.

When I try to change my xorg.conf file to set the driver to "nvidia", and then a "startx", I have an error from the NVIDIA driver: Unable to detect a proper device... or something like that. (The driver doesn't detect my onboard video card)


So, what are the possibilities/solutions ?



Question #2: Do I just need to CTRL+ATL+BACKSPACE , then change my xorg.conf, and then "startx" ... or do I need to restart GDM too ?

---

### Post by jijin on 2007-08-23
> **FMaz008 said:**
> I have trouble installing the NVidia driver under Ubuntu Feisty too.

But to answer your question: to shutdown the X, when you are in it, just do CTRL+ALT+BACKSPACE.

Then, after you have downloaded the .run file from NVIDIA, you can do:
sudo sh NVIDIA[..??..].run

the [..??..] is the rest of the filename that I don,t remember.


My problem is that I have an onboard GeForce 7025, and it seem that I REALLY need this driver.
But when the installation wizard starts, it give me a bunch of error, telling me that the installer will attempt to recompile the Kernel, then that my Xorg is modular and that a path can't be found.

At the end, it tell me that the driver has been installed in a spcific path.

When I try to change my xorg.conf file to set the driver to "nvidia", and then a "startx", I have an error from the NVIDIA driver: Unable to detect a proper device... or something like that. (The driver doesn't detect my onboard video card)


So, what are the possibilities/solutions ?



Question #2: Do I just need to CTRL+ATL+BACKSPACE , then change my xorg.conf, and then "startx" ... or do I need to restart GDM too ?

I get the same thing... I gave up until the 710 release

---

### Post by tseliot on 2007-08-23
If you want you can try Envy (**at your own risk**):
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

follow point B of the instructions (otherwise it won't work for you):
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

