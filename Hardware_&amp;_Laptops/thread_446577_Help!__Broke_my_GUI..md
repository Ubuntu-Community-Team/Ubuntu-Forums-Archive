---
title: "Help!  Broke my GUI."
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by HungarianErich85 on 2007-05-17
Hello,

Last night I decided to give Beryl a go, and installed it and the Emerald packages available under Synaptic, as well as installed my NVidia 3D drivers.  Promptly upon reboot I lost my GUI with only a black screen displayed after the Ubuntu loading screen.  I had no XServer error, just a black screen.

Does anyone know how I can rectify this?  My specs are as follows:  Feisty Fawn 7.04 (32-bit), HP Pavilion dv6258se, AMD 64x2 Turion, Nvidia GeForce Go 6150, 2 GB of DDR RAM.  

Thank you for any help in restoring my computer!,

Erich

---

### Post by ingo on 2007-05-17
Don't worry, it is easy enough...

Get the latest Nvidia [driver]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run") and save it somewhere easy. Next, reboot and wait for X not to come up. Now change to another screen by pressing CTRL+ALT+F2, log yourself in and change to the directory you saved the driver in. 

Now you have to grant the driver executive rights by typing: ```
sudo chmod +x NV[tab]
```If you do not know the [tab] feature - it is absolutely wonderful as it will complete the typing for you.

Now you have to stop X by typing ```
sudo /etc/init.d/kdm stop
```If you are running Ubuntu, not Kubuntu as I do you have to replace kdm with gdm.

You are now ready to execute the driver ```
sudo sh NV[tab]
```If that does not work try ```
sudo ./NV[tab]
```Follow the instructions on screen. Say yes to everything. Once it has installed itself restart X by typing ```
sudo /etc/init.d/kdm start
```Or gdm instead of kdm if you are running Ubuntu.

Let us know if you are running into any probs...

---

### Post by Kobalt on 2007-05-17
How did you try to install your nvidia drivers ? The best way is to go into the System > Admin. > Restricted drivers manager, and click to enable your 3D acceleration. That will install the drivers properly for you. 
Right now, what you can do is press Ctrl+Alt+F1 to access a command line. Log in, then enter this command line (write this all down on a piece of paper, indeed) : ```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions, leave the default choice when you don't know what to pick, and then reboot you computer (you can type *sudo reboot* from the command line to do that). 
After this you should go to the Restricted drivers manager to install your drivers as I explained before, and then only, after a reboot, install Beryl if you'd like.

---

### Post by HungarianErich85 on 2007-05-17
> **Kobalt said:**
> How did you try to install your nvidia drivers ? The best way is to go into the System > Admin. > Restricted drivers manager, and click to enable your 3D acceleration. That will install the drivers properly for you. 
Right now, what you can do is press Ctrl+Alt+F1 to access a command line. Log in, then enter this command line (write this all down on a piece of paper, indeed) : ```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions, leave the default choice when you don't know what to pick, and then reboot you computer (you can type *sudo reboot* from the command line to do that). 
After this you should go to the Restricted drivers manager to install your drivers as I explained before, and then only, after a reboot, install Beryl if you'd like.

Right, it was installing the 3D drivers that killed my GUI though, so that seems like not the best option.  Also, I have no idea what the answers are for the configuration of the xserver.  The last time I ran into this I had to just reinstall Ubuntu, and that was my third reinstall in two weeks.  This is frustrating.

---

### Post by HungarianErich85 on 2007-05-17
> **ingo said:**
> Don't worry, it is easy enough...

Get the latest Nvidia [driver]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run") and save it somewhere easy. Next, reboot and wait for X not to come up. Now change to another screen by pressing CTRL+ALT+F2, log yourself in and change to the directory you saved the driver in. 

Now you have to grant the driver executive rights by typing: ```
sudo chmod +x NV[tab]
```If you do not know the [tab] feature - it is absolutely wonderful as it will complete the typing for you.

Now you have to stop X by typing ```
sudo /etc/init.d/kdm stop
```If you are running Ubuntu, not Kubuntu as I do you have to replace kdm with gdm.

You are now ready to execute the driver ```
sudo sh NV[tab]
```If that does not work try ```
sudo ./NV[tab]
```Follow the instructions on screen. Say yes to everything. Once it has installed itself restart X by typing ```
sudo /etc/init.d/kdm start
```Or gdm instead of kdm if you are running Ubuntu.

Let us know if you are running into any probs...

How do I save the driver any where but an external hard drive or a burnt CD?  Can I access that using this CTRL+ALT+F2?

---

### Post by ingo on 2007-05-17
Yes, no probs. I take it the operating system is still functioning properly, so pop in your CD, go onto the second console (using CTRL+ALT+F2) and copy the driver over to your home directory using > cp /media/cdrom/NV[tab] /home/name_of_your_home_directoryNow you can grant it executive rights etc.

---

### Post by HungarianErich85 on 2007-05-17
> **ingo said:**
> Yes, no probs. I take it the operating system is still functioning properly, so pop in your CD, go onto the second console (using CTRL+ALT+F2) and copy the driver over to your home directory using Now you can grant it executive rights etc.

I wait til the Ubuntu thing loads, and the black screen displays.  I press CTRL+ALT+F2.  Nothing at all happens. Any other suggestions?  :(

---

### Post by HungarianErich85 on 2007-05-17
Anyone?

---

