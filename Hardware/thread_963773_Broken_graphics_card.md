---
title: "Broken graphics card?"
date: 2008-10-30
forum: Hardware
---

### Post by meg23 on 2008-10-30
After many years of having no trouble with my graphics card and the nvidia drivers, all of sudden my laptop would only boot in recovery mode once the graphic drivers were removed. When the drivers are reinstalled x fails to start. In sysinfo, the graphics card is recognized however it cannot read the performance details of the card. Is it possible that I have a broken graphics card?

laptop:~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)

From Sysinfo:
Model: GeForce Go 6200
Card Type: PCI-E 
Video Ram: Unknown
GPU Frequency: Unknown

laptop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

---

### Post by overdrank on 2008-10-30
> **meg23 said:**
> After many years of having no trouble with my graphics card and the nvidia drivers, all of sudden my laptop would only boot in recovery mode once the graphic drivers were removed. When the drivers are reinstalled x fails to start. In sysinfo, the graphics card is recognized however it cannot read the performance details of the card. Is it possible that I have a broken graphics card?

laptop:~$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6200/6400] (rev a1)

From Sysinfo:
Model: GeForce Go 6200
Card Type: PCI-E 
Video Ram: Unknown
GPU Frequency: Unknown

laptop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Hi and it is a possibility, You may check bios to see if any thing has changed in the setup. If You have any graphics at all then it would seem that the system is still operational. You may also try and use the nv driver instead and use the xfix option in recovery mode to verify the graphics are bad.

---

### Post by phidia on 2008-10-30
With that card have you tried installing the driver with > sudo apt-get install nvidia-glx

I believe using that command allows apt to select the best driver for your card. 

Which version of ubuntu are you using?

---

### Post by phidia on 2008-10-30
> **overdrank said:**
> Hi and it is a possibility, You may check bios to see if any thing has changed in the setup. If You have any graphics at all then it would seem that the system is still operational. You may also try and use the nv driver instead and use the xfix option in recovery mode to verify the graphics are bad.

Hey overdrank, I'm struggling to provide useful help with xorg 7.4.
Is there a permanent link somewhere that shows the commands available and how to use them to correct xorg issues? 

I take it for instance that "xfix" is only available in recovery mode. There's another recent command that's been occasionally mentioned too. (not the standard dpkg-reconfigure command)

Thanks

---

### Post by meg23 on 2008-10-31
I am using 8.10 but the problem occurred in hardy also. I had hoped maybe an upgrade would fix the problem. I have basically installed all the drivers even old ones with envy-ng and the command line to no avail. It seems like something broke on the graphics card and ubuntu can't seem to boot into x with the graphics card. Can a graphics card break partially in a way that prevents any type of GPU acceleration?

---

