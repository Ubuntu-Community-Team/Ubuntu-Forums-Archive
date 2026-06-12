---
title: "Graphics driver problem?"
date: 2008-07-26
forum: General Help
---

### Post by JLaw on 2008-07-26
Hello all, first post and an Ubuntu 8.04 rookie here.  I'm not that computer savvy but decided to make the switch with support of my Ubuntu using family members.  

I'm running Ubuntu 8.04 on a 4(?) year old EMachines computer.  The only thing I know about the graphics in the computer are that it is NVidia GeForce 4 MX.  I am having some problems with graphics on some games, such as FlightGear and LinCity-NG. FlightGear is completely missing the control panel, guages etc.  LinCity-NG starts up and I have sound, but absolutely no graphics.  I have encountered this problem with a few other games.

Where should I start to try to get the graphics working?

Thanks so much, 

JLaw

---

### Post by alterpinguin on 2008-07-26
check you have nvidia-settings installed and maybe too sysinfo - you can find those with synaptic (use the search function)- 
with those apps you can check the 3d-installed-glx-functionality. Maybe you have not installed the 3d-driver ... etc.

---

### Post by northern lights on 2008-07-26
Could you please post the output of ```
sudo lshw -C display
```

Thanks

---

### Post by JLaw on 2008-07-26
Here's the results of that command line:

 *-display               
       description: VGA compatible controller
       product: NV18 [GeForce4 MX - nForce GPU]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia

JLaw

---

### Post by northern lights on 2008-07-26
+1 for ```
nvidia-settings
```

---

