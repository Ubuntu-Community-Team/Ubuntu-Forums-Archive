---
title: "Installing Ubuntu on Compaq Presario CQ71"
date: 2009-09-23
forum: Hardware
---

### Post by e93mro on 2009-09-23
Installing **Ubuntu 9.04** on a **Compaq Presario CQ-71** left me with two problems. First, there was no sound from the laptop speakers - only from the headphones. Second, I couldn't install any restricted graphics drivers from Nvidia for the **G103M** graphics card. But I managed to get it all working. Now I have sound in both laptop speakers and in headphones and I can use Compiz Fusion desktop effects.

Sound
======

In order to get the sound working I basically followed two different posts. First, I looked at this post that explained how to modify the /etc/modprobe.d/alsa-base file. [http://ubuntuforums.org/showthread.php?p=7897428#post7897428]("http://ubuntuforums.org/showthread.php?p=7897428#post7897428")

Note that there was a typo in the description. You should paste the 4 lines at the bottom of the /etc/**modprobe.d**/alsa-base file.

Then I had to upgrade the ALSA drivers following this excellent description [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/")

Then the sound worked!!! 

Graphics
=========

Searching for drivers on the NVidia web site returned nothing for the G103M card. Instead I downloaded the drivers for the G103 card [http://www.nvidia.com/object/linux_display_ia32_185.18.36.html]("http://www.nvidia.com/object/linux_display_ia32_185.18.36.html")

My guess is that the only difference is that the M-model is for notebooks.

First, modify the permissions on the driver file.

```
sudo chmod 777 NVIDIA-Linux-x86-185.18.36-pkg1.run
```

In order to install the graphics driver you will have to leave your desktop and move the console. Close all running applications and press CTRL + ALT + F1. Login and start installing the driver

```
sudo sh ./NVIDIA-Linux-x86-185.18.36-pkg1.run
```

Wait for the driver to install. The installation may ask if you want to download new kernel modules - select yes. The installation also will ask you if you want to run the xconfigs and you should do that. When the installation and configuration is finished shutdown your system.

```
sudo halt
```

Then I restarted the computer and I could set the **Appearance Settings** for **Visual Effects** to **Extra**. I installed Compiz Fusion and it works fine with the desktop effetcs as well.

---

### Post by pingu1 on 2010-03-10
Thank you very much!
May I also ask: Why were you unable to install the restricted drivers for the graphics?

---

### Post by e93mro on 2010-03-11
No restricted drivers were detected from within the "Hardware Drivers" tool that comes with Ubuntu. That's why I had to get the drivers from the NVidia site.

BTW, an easy way to determine your graphics card model

```
lspci | grep nVidia
```

I did a community upgrade from 9.04 to 9.10 and then the restricted driver was detected directly in the "Hardware Drivers" tool (190).

---

### Post by nikkkko on 2010-03-11
Hi,

Just looking at installing 9.10 for a colleague and wifi doesn't work from the live CD.  Does it work ok with the install?

Thanks

---

### Post by e93mro on 2010-03-11
I have never had any problems with the WIFI in Ubuntu (9.04 and 9.10) - but I remember that I forgot to turn on Wifi using the button on the computer.  :-)

It was turned off by default on my machine.

---

### Post by nikkkko on 2010-03-11
Well, the button's definitely on, wifi's definitely not working but I'm not going to worry about it now. As long as I know that it should work without any major hack then I'll just go ahead and install.

Thanks for the help.

---

