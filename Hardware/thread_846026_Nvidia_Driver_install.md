---
title: "Nvidia Driver install"
date: 2008-07-01
forum: Hardware
---

### Post by darkhorse186 on 2008-07-01
Hi,
I have an nvidia Geforce 5200 FX graphics card but i'm not sure if it is working as some applications like blender run very slowly. The driver isn't listed in the restricted drivers section like it used to be.
I tried downloading the Nvidia driver from their site but whenever i run it i get this message and I have no idea what to do:

 
  ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I tried that But I don't really understand what to do.

Darkhorse

---

### Post by overdrank on 2008-07-01
> **darkhorse186 said:**
> Hi,
I have an nvidia Geforce 5200 FX graphics card but i'm not sure if it is working as some applications like blender run very slowly. The driver isn't listed in the restricted drivers section like it used to be.
I tried downloading the Nvidia driver from their site but whenever i run it i get this message and I have no idea what to do:

 
  ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I tried that But I don't really understand what to do.

Darkhorse


Hi and if you are trying to install the nvidia drivers for then site then use the keys alt, ctrl, F1 and this will bring you to the command prompt
then enter this command to stop x
```
sudo /etc/init.d/gdm stop
```
Then follow the direction from the nvidia site and you will have to cd to the directory where downloaded the file which is your desktop
```
cd ~/Desktop
```
then run the command to install. Good luck

---

### Post by Irontooth on 2008-09-05
Hello there!

I seem to be having the same problem with Blender. It runs very slowly, and compared to what I was used to have on Windows it is much slower. Does it really help to install that graphics card driver? I didn't install anything after installing the system, and if it isn't obligatory I rather wouldn't because I once tried to install those Nvidia drivers and then I had to reinstall the system because something went wrong and I couldn't make it right again... :lolflag:


PS I've got Geforce 7600 GS and Linux Mint 5.

---

### Post by overdrank on 2008-09-05
> **Irontooth said:**
> Hello there!

I seem to be having the same problem with Blender. It runs very slowly, and compared to what I was used to have on Windows it is much slower. Does it really help to install that graphics card driver? I didn't install anything after installing the system, and if it isn't obligatory I rather wouldn't because I once tried to install those Nvidia drivers and then I had to reinstall the system because something went wrong and I couldn't make it right again... :lolflag:


PS I've got Geforce 7600 GS and Linux Mint 5.

Hi and welcome, I am pretty sure that yes it would make a difference if you installed the drivers.

---

### Post by Irontooth on 2008-09-05
Ok, I will have to try it again,

thanks

---

