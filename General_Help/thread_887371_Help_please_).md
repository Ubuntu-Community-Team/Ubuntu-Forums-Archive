---
title: "Help please :)"
date: 2008-08-12
forum: General Help
---

### Post by Landara on 2008-08-12
Sorry to be "that guy" here but I have a really quick question here.  As someone using an Nvidia 9600GT am I 100% screwed?  I can't use Desktop Effects at all.  When I click on Normal or Extra on the Visual Effects tab, it locks up for a few secs then tells me it didn't work.  

I tried to download the latest driver from Nvidia(the Linux 64bit one) and it's sitting on my desktop.  It says to then type:
sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run
to install the drivers.  But when I do that it says:
sh: Can't open NVIDIA-Linux-x86_64-173.14.12-pkg2.run

So basically, the whole point of running Ubuntu to me was it's amazing looks.  But as we sit here it looks worse than windows 95, and I'm wondering if this is my fault or if my video card wont work with it at all.

---

### Post by rudihawk on 2008-08-12
I had a similar problem. You need to login as root. Change the property of the file (something about running as an executable), and then it should work.

---

### Post by houbysoft.xf.cz on 2008-08-12
Before running the sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run, do a sudo chmod +x NVIDIA-Linux-x86_64-173.14.12-pkg2.run, then sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run. It will both ask for your password, just type it and then hit enter.

---

### Post by Landara on 2008-08-12
Does anyone know if this video card will ever work at all?  I still cannot get this driver to install.  I changed it to be able to run as a program but it still says it must be run in root.  However, I tried sudo sh and all of that, many times and many google searches worth of commands, but still it simply refuses to run this file.

I wanna use Ubuntu but this is getting pretty ridiculous :(

---

### Post by damis648 on 2008-08-12
The reason it cannot open it is because it cannot find it. You said this file was on your desktop? If it is not, copy it there and rename it to
```
nvid.run
```
and then fire up a terminal. In terminal type:
```
cd ~/Desktop
sudo sh nvid.run
```
and that should do it. :popcorn:

PS. Make sure that you are only installing the 64-bit driver if you are also running 64-bit ubuntu.

---

### Post by blazercist on 2008-08-12
First of all your Thread Title is absolutely USELESS, you should consider making the title more relevant and explanatory of your problem next time and maybe you will get more help.  Second, you should probably do a search in the forums before posting with your problem as it has already been solved countless times by myself let alone others in this forum.

This video card works just fine, I have dual monitors with 1280x1024 each and desktop effects running with this card.
I have a suggestion, lets do a hard clean of all the crap that you've screwed up already.

This will remove the old driver packages 
```
sudo apt-get remove nvidia-glx nvidia-glx-new nvidia-kernel-common
```

This will remove the actual driver file from its directory.
```
sudo rm /lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko
```

Now lets blacklist all the bad stuff.

```
sudo gedit /etc/modprobe.d/blacklist
```
add "nv" to the list there.


Now its time to install the driver the PROPER way.
*Download the driver from NVIDIA.com to your home folder.

This installs the files needed to build the driver file with the installer and also makes the driver file executable.
```
sudo apt-get install build-essential
sudo chmod +x NV*
```
CTRL+ALT+F1 (This will drop you to virtual terminal.)

This stops X-server and runs the installer, the NVIDIA driver cannot be installed while the X-server is running.
```
sudo /etc/init.d/gdm stop
sudo sh NV*
```
Accept, yes, yes yes.

This restarts X-server
```
sudo /etc/init.d/gdm start
```

Now everything should work just fine.  Keep in mind that when there is a Kernel update you will need to reinstall the driver.  Don't panic, this is easy.


Instructions for reinstall after kernel update.
Leave the installer as is in your home directory.
CTRL+ALT+F1
```
sudo /etc/init.d/gdm stop
sudo sh NV*
Accept, yes yes yes.
sudo /etc/init.d/gdm start
```

---

### Post by sayakb on 2008-08-12
Please give descriptive titles to your threads rather than just "Help please" or "n00b here".
Thank you!

---

### Post by dacorr on 2008-08-12
i just used envy

---

### Post by ArtF10 on 2008-08-12
different NVIDIA video card, but I too just used Envy.

---

