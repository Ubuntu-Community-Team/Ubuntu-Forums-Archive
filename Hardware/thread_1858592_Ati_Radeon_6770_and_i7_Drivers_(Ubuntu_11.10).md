---
title: "Ati Radeon 6770 and i7 Drivers (Ubuntu 11.10)"
date: 2011-10-12
forum: Hardware
---

### Post by jozeph78 on 2011-10-12
Hello guys. I've been trying for a few hours to get this working and simply can't seem to get any 3D acceleration going on my laptop. 

I have an HP dv6qe with a 2630M i7 and a 6770M. I've tried the fglrx and downloaded the ATI drivers and get various errors with both. Here is my lspci output. 

```
jhirn@dv6buntu:~$ lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: ATI Technologies Inc Whistler XT [AMD Radeon HD 6700M Series] (prog-if 00 [VGA controller])
```


This is for gnome 3.2. I cannot get gnome-shell to run and the experience is fallback no matter what I try. I can detail the failures of both fglrx and the prop drivers from ATI if that helps but I'm at work right now and have to post this up quickly. Essentially, both have installed but neither enable full gfx capabilities. I've gotten errors uninstalling them and had to do a force uninstall, but I think that's just the drivers getting conflicted. 

I did my fair share of searching around already and I'm stuck. help me please! =)

Also, is it possible to do the graphics switching between the two and does anyone know if the intel 2nd generation integrated graphics controller will run 3d effects? If not I'll probably keep the AMD card on all the time and underclock it, but let's get it working first. 

Thanks!

---

### Post by jozeph78 on 2011-10-12
Ok. On a clean install of the prop drivers, here is my output... It appears to have installed correctly but I get no acceleration. 

```
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit
loki_setup: directory: (null)
loki_setup: Couldn't write to file: //usr/lib32/libaticalcl.so
loki_setup: Couldn't write to file: //usr/lib32/libaticalrt.so
loki_setup: Couldn't write to file: //usr/bin/fgl_glxgears
loki_setup: Couldn't write to file: //usr/bin/fglrxinfo
loki_setup: Couldn't write to file: //usr/bin/aticonfig
loki_setup: Couldn't write to file: //usr/bin/atiodcli
loki_setup: Couldn't write to file: //usr/bin/atiode
loki_setup: 2 Unable to find file 'install/usr/bin/amdconfig' in '/home/ourumov/Downloads/fglrx-install.SxxSlC'
loki_setup: Couldn't write to file: //usr/bin/amdcccle
loki_setup: Couldn't write to file: //usr/bin/amdxdg-su
loki_setup: Couldn't write to file: //usr/bin/amdupdaterandrconfig

```

---

### Post by collisionystm on 2011-10-12
I had problems with this last night. Not the same, but ATi driver problems none-the-less.

I installed 11.10 with alternative install. Live CD would result in black screen.
Had to boot to command shell
Removed xorg ati drivers
Finally able to boot to GUI
Installed ATI Catalyst drivers from website
Install finished, Ran ATICONFIG for single head mode. 
Rebooted... 
Ubuntu would not boot past the splash logo. System would freeze. 

Booted into system rescue, hit the normal boot, held the shift key to boot it into safe mode. Once again back at prompt.

sudo apt-get purge fglrx
Could not purge everything
Looked at the log file, said I had to run a script manually to delete everything. 
did this
Re-Installed FGLRX.
sudo apt-get install fglrx
rebooted.
worked.

Im not sure what order you did things in, but if it was anything like what I did... maybe this will help?

---

### Post by jozeph78 on 2011-10-12
Thx for the reply colison. I just tried the steps you've suggested. Uninstalling the prop drivers, purging fglrx, manually cleaning up any files left behind. I then rebooted into safe mode and installed fglrx. 

Everything installed ok but still no 3D accel. Keeps going into fallback mode. Is there something I have to do to prevent it from going into fallback mode? I did turn off forced fallback mode in system info. 

I also was never as bad off as you. I've been able to boot just fine regardless of what state I've gotten into. I just cannot get teh 3d accel (transparency, gnome-shell) to work. 

I was getting that additional driver dialog but it no longer comes up. 

I should also add this particular laptop has two modes, fixed and dynamic in BIOS. Dynamic enables per application switching and fixed is on when plugged in or off when on battery. Fixed mode can be manually overridden by software. 

I'm actually going to try installing 11.04 over this current install. Shouldn't take long on my Agility 3 SSD =):guitar:

---

### Post by nembo on 2011-10-24
I had exactly the same problem.
For me the following approach worked:


- Uninstall fglrx-driver from repository
- Download the newest catalyst [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
- create deb packages with the following command
```
sh ati-driver-installer-*-x86.x86_64.run --buildpkg
```- Install **fglrx** and **fglrx-amdcccle** package
- Execute:
  ```
sudo aticonfig --initial
```if a problem occurs:
```
sudo aticonfig --initial --force
```Here is the german HowTo:
[http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation](http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation)

---

### Post by ghost305 on 2011-10-25
> **nembo said:**
> I had exactly the same problem.
For me the following approach worked:


- Uninstall fglrx-driver from repository
- Download the newest catalyst [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
- create deb packages with the following command
```
sh ati-driver-installer-*-x86.x86_64.run --buildpkg
```- Install **fglrx** and **fglrx-amdcccle** package
- Execute:
  ```
sudo aticonfig --initial
```if a problem occurs:
```
sudo aticonfig --initial --force
```Here is the german HowTo:
[http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation](http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation)
i did this but while it was building the package, it said that i was missing ia32-libs files. Its strange b/c my system is 32 bit.

---

