---
title: "NVIDIA/GeForce"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by mulle on 2007-05-07
I have a NV43 [GeForce 6600/GeForce 6600, and I am unable to install.
System>preferences>desktop effects don't work when I reboot, it comes with X-Server isn't configured right.

---

### Post by EXCiD3 on 2007-05-07
Have you enable the restricted drivers for the Nvidia card yet?

Download and install Automatix2 and run it. Choose to install the Nvidia driver through it. It will take care of EVERYTHING that needs to be done. You should then be able to use Desktop Effects (as known as Compiz).

You might try Beryl. It is a branch of the Compiz project that is MUCH better. It has many more options/features, but it is slightly less stable. It works very well on Nvidia cards. [http://www.beryl-project.org](http://www.beryl-project.org)

For installation instructions: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)
You need the Nvidia restricted driver (from Automatix as I explained above) BEFORE you go installing beryl. It makes it much easier and will cause less problems.

---

### Post by martijn_bakker on 2007-05-07
I am using a GeForce 6600 GLS with no problems.

When I used the standard installer, the screen resolution was fixed to 1024x768 (which is not exactly pretty on my 1280x1024 TFT). I needeed to install nvidia-glx for higher screen resolutions to be supported (although you can probably get it to work using the standard nv driver too).

1. From the "System" panel, choose "Administration" and then "Software sources". Tick the tickbox for "proprietary drivers for devices (restricted)" (and you might as well tick the others while you're at it). Then click "Close". (more experienced users can reach the same result by removing the hash signs in from of the "restricted" repository in /etc/apt/sources) 

2. From the "System" panel, choose "Administration" and then "Synaptic package manager". In the package manager, click the blue "Reload" icon, then find "nvidia-glx" in the package list, right click it and choose "mark for installation" from the context menu. Click the green "Apply" icon and choose "Apply" from the popup window. (more experienced users can reach the same results by typing "sudo apt-get install nvidia-glx" in a shell).

3. From the "System" panel, choose "Administration" and then "Restricted drivers manager". Tick "enabled" for the NVidia driver.

4. Restart X windows by switching user, rebooting your machine or pressing ctrl-alt-backspace.

---

### Post by cptcrunch on 2007-05-07
try this HowTo

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

---

### Post by mulle on 2007-05-07
I try all of you great advice...

but X-Config kept coming with error :'(
its like there are no support for my GFX... :'(

---

