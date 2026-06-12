---
title: "nvidia nouveau 12.04 flickering Samsung SyncMaster E2220 GeForce 7025 / nForce 630a"
date: 2014-11-16
forum: Hardware
---

### Post by zamcan45 on 2014-11-16
My Samsung SyncMaster E2220 is flickering all the time in Ubuntu 12.04. I have driver nouveau installed. My kernell is 3.2.0-54-generi. 
lshow -class display output is:
descripción: VGA compatible controller
       producto: C61 [GeForce 7025 / nForce 630a]
       fabricante: NVIDIA Corporation
       id físico: d
       información del bus: pci@0000:00:0d.0
       versión: a2
       anchura: 64 bits
       reloj: 66MHz
       capacidades: pm msi vga_controller bus_master cap_list rom
       configuración: driver=nouveau latency=0
       recursos: irq:22 memoria:fa000000-faffffff memoria:e0000000-efffffff memoria:f9000000-f9ffffff memoria:fbfc0000-fbfdffff

lspci -vn | grep -i --color 'vga' output is
00:0d.0 0300: 10de:03d6 (rev a2) (prog-if 00 [VGA controller])

lspci -v | grep no
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb

Ubuntu is offering me nvidia propietary driver number 304 is this the appropiate driver to use with my card GeForce 7025 / nForce 630a]?
Thank you in advance.

---

### Post by zamcan45 on 2014-11-16
You are right. My question was a not very useful one. I have tried the dirver 304. There is no delay in the refreshment as it was with nouveau, but the flickering is so intense that is like blinking all the time.
Here are the outputs
sudo lspci -v | grep nvi

    Kernel driver in use: nvidia
    Kernel modules: nvidia_304, nouveau, nvidiafb


lspci -vn | grep VGA

00:0d.0 0300: 10de:03d6 (rev a2) (prog-if 00 [VGA controller])

I have borrowed a laptop with windows from a friend and the resolution is clean without flickering under Windows.

Is there anything I can set or change to avoid flickering in my Ubuntu 12.04?

Thanks in advance

---

### Post by zamcan45 on 2014-11-16
Using the latest dirver did not help, it is still flickering.
sudo lspci -v | grep nvi

Kernel driver in use: nvidia
    Kernel modules: nvidia_304_updates, nvidia_304, nouveau, nvidiafb

Outpui of my sudo cat /var/log/Xorg.0.log is in here: [http://paste.ubuntu.com/9045168/plain/](http://paste.ubuntu.com/9045168/plain/)
is there someone who can guide me asking me for output and giving a solution?


Thank in advance

---

### Post by zamcan45 on 2014-11-16
Using previous driver did not help. still is flickering
    Kernel driver in use: nvidia
    Kernel modules: nvidia_173, nvidia_304_updates, nvidia_304, nouveau, nvi

Is there someone who can guide me asking me for output and giving a solution?


Thank in advance

---

### Post by zamcan45 on 2014-11-16
Using the last driver the 96 one did not help either

Kernel driver in use: nvidia
    Kernel modules: nvidia_173, nvidia_96, nvidia_304_updates, nvidia_304, nouveau, nvidiafb

so, I will look for another linux distribution that has a better support for my monitor and my card.

If someone is able to help me I will be helpful.

Thanks in advance.

---

### Post by zamcan45 on 2014-11-27
I would like to add something more and share my experience. 
Problem: A Samsung SyncMaster E2220 has a standard resolution of  1920x1080, but flickering is so intense that after 30 minutes of  standing in front of the screen your eyes hurt.
Solution: Change the refresh rate
Root-problem: propietary drivers allow you to have maximum 60 Hz refresh rate
Solution: Elevate the refresh rate to 75 Hz

Solution step by step:
First deshabiitate the propietary drivers
12.04 offers you 4 propietary drivers: 96, 173, Recommended (304), and  304 updates. The first two (96 and 173)  allow you to have maximum 50 Hz at  1920x1080, the last 2 allow you to have maximum 60 Hz at 1920x1080; it is better, however it is not enough
How: with the GUI, In System > Administration > Hardware drivers.  Click on the driver. Green means it is installed. You have to uninstall  all of them
Second: habilitate native driver that comes with ubuntu called nouveau.
Nouveau has a refresh rate at 1920x1080 of 60 Hz. It stills flicker.
Third: Set a different refresh rate, but you have to change also the resolution
How: with the CLI (Command Line) Open a terminal (ALT+F2 and type "gnome-terminal") and write the following at the prompt:
     Code:
```
xrandr -s 1400x900
```

You can try to write 
```
xrandr -s 1440x900 -r 75
```
but xrandr will complaint: The reason is that in Ubuntu 12.04 xrandr version is 1.3 or superior and assumes that if you are changing the resolution the standard refresh rate for that resolution should be applied, For that reason is better if you use only: 
```
xrandr -s 1400x900
```

The resolutions is worse. Icons seems deformed, but the flicketing is gone.

It could be that my nvidia video card GeForce 7025 / nForce 63 does not play well with higher resolutions using a VGA port.
I have read that higher resolutions should go though DVI-I which is faster and slower refresh rate does not affect to flickering.
But as I have this monitor amsung SyncMaster E2220 and this nvidia card GeForce 7025 / nForce 63 this is the better solution I have found so far.

---

