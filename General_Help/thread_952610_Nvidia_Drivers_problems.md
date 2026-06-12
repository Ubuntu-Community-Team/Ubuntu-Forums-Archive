---
title: "Nvidia Drivers problems"
date: 2008-10-19
forum: General Help
---

### Post by linuxfreak3 on 2008-10-19
got some problems with my ubuntu hardy
Recently installed the Nvidia drivers, worked great! untill i restarted the computer :(, now there are no good drivers and its in grapich safe mode or something and i cant get the drivers back in :/

any suggestions?

---

### Post by northern lights on 2008-10-19
Can you please post the output of ```
sudo lshw -C display
```Thank you.

---

### Post by linuxfreak3 on 2008-10-19
*-display               
       description: VGA compatible controller
       product: GeForce 8600 GT
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

---

### Post by northern lights on 2008-10-19
> **linuxfreak3 said:**
> configuration: [COLOR="SeaGreen"]driver=nvidia[/COLOR] latency=0 module=nvidiaThe correct driver is assigned already.

See whether running nvidia-xconfig makes a difference.

Install```
sudo apt-get update && sudo apt-get install nvidia-xconfig
```
and subsequently run```
nvidia-xconfig
```
Now what?

---

### Post by Riffer on 2008-10-19
You could try EnvyNG, its in the repos, download and install.  The real trick here is to remove the present nVidia driver (by using Envy) and rebooting before re-installing your drivers.

I've had problems myself because of the Monitor driver, make sure that is setup correctly.  Good Luck.

---

### Post by linuxfreak3 on 2008-10-19
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
         default configuration.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by northern lights on 2008-10-19
> **linuxfreak3 said:**
> New X configuration file written to '/etc/X11/xorg.conf'
If you restart X now (i.e. reboot, log out and back in), are there more resolution available for your choosing?

---

### Post by linuxfreak3 on 2008-10-19
just restarted it, same **** still here :(

---

### Post by fooman on 2008-10-19
if you have not tried envyng-gtk yet,  maybe give that a shot.  ...see riffer's post above.

---

### Post by linuxfreak3 on 2008-10-19
envyng solved everything :)
thx ^^

---

### Post by Riffer on 2008-10-19
Please mark this thread solved.  And glad it worked for you.

---

### Post by linuxfreak3 on 2008-10-19
how? :p

---

### Post by Riffer on 2008-10-19
Under thread tools at the top.

---

