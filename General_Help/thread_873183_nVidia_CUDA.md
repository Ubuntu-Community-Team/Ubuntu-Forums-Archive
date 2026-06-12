---
title: "nVidia CUDA"
date: 2008-07-28
forum: General Help
---

### Post by mkartic on 2008-07-28
hey ppl, i want to install the CUDA API in my Ubuntu. I've downloaded 3 .run files which i wasnt able to execute. I found in the IRC channel that i have to use chmod, but even after that it says something about not running from 'X Client', can you help me out? :confused:

---

### Post by ryanhaigh on 2008-07-28
The x client issue probably means that you need to be in a console rather than using a console emulator. Just press ctrl-alt-f1 to change to the first terminal and try running the files there. Ctrl-alt-f7 gets you back to your GUI.

---

### Post by bfhicks on 2008-09-12
a little late, but anyhow ...

First of all, you'll need to chmod them all to +x.

```
chmod u+x NVIDIA*
```
Secondly, you'll need to get into an init mode: 
```
CTRL+ALT+F1
```
If you aren't logged in, go ahead and do so. Now, let's shut down the x-server:
```
sudo /etc/init.d/gdm stop
```
Now, install the files:
```
sudo sh NVIDIA<whatever>
```
After you install the driver and build the kernel module (all this is done automatically when installing the driver) allow the application to configure your xorg.conf.

Let's verify that it's correct after the install:
```
sudo nano /etc/X11/xorg.conf
```
Under "Devices" and "Driver" if you don't see "nvidia" but instead you see "nv" or something, change it to "nvidia".

---

