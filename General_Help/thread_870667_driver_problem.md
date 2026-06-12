---
title: "driver problem"
date: 2008-07-26
forum: General Help
---

### Post by vidyutandambi on 2008-07-26
i have upgraded ubuntu7.10 to ubuntu8.04 .my application ,places system and all the windows shown by right click of mouse is appearing completly transaparnt i m not able to see nything either in browser i knnt see the window while scrolling down for file, edit and any other option

i have enabled the restricted driver then this problem came after enabling this restricted driver nvidia-glx-new has been intalled  on my machine.

while in ubuntu7.10 after enabling the restricted driver nvidia-glx has got installed and all 3d effect and evrything was fine.

---

### Post by northern lights on 2008-07-26
Can you please post the output of ```
sudo lshw -C display
```
Thank you.

---

### Post by argail1980 on 2008-07-26
probably your card has moved from the nvidia-glx-new package to the nvidia-glx package in Hardy. Try to uninstall the '-new' drivers and install nvidia-glx instead.

---

### Post by vidyutandambi on 2008-07-27
the output of this code
sudo lshw -C display
 
is as:

description:VGA compatible controller
product:c516[GeForce6100]
vendor:nvidia corporation
physical id:5
bus inf0:pci@0000:00:05.0
version:a2
width:64bit
clock:66MHz
capabilities:pm msi vga_controller bus_master cap_list
configuration:driver=nvidia latency=0 module=nvidia

---

### Post by vidyutandambi on 2008-07-27
the output of this code
sudo lshw -C display
 
is as:

description:VGA compatible controller
product: c516[GeForce6100]
vendor: nvidia corporation
physical id:5
bus inf0: pci@0000:00:05.0
version: a2
width:64bit
clock:66MHz
capabilities: pm msi vga_controller bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia

---

### Post by overdrank on 2008-07-27
> **vidyutandambi said:**
> the output of this code
sudo lshw -C display
 
is as:

description:VGA compatible controller
product: c516[GeForce6100]
vendor: nvidia corporation
physical id:5
bus inf0: pci@0000:00:05.0
version: a2
width:64bit
clock:66MHz
capabilities: pm msi vga_controller bus_master cap_list
configuration: driver=nvidia latency=0 module=nvidia

Ok do you have a issue that you need help with?
Threads merged and moved :)

---

### Post by overdrank on 2008-08-02
If you can boot into recovery mode and use the xfix option. The recovery mode is usually the second choice from the grub. This hopefully will correct the issue. If not post back to this thread and do not create a new thread on this issue. :)

---

### Post by vidyutandambi on 2008-08-02
> **overdrank said:**
> If you can boot into recovery mode and use the xfix option. The recovery mode is usually the second choice from the grub. This hopefully will correct the issue. If not post back to this thread and do not create a new thread on this issue. :)

i have booted in recovery mode but still not able to fix the problem.

---

### Post by overdrank on 2008-08-02
> **vidyutandambi said:**
> i have booted in recovery mode but still not able to fix the problem.

Ok use the keys ctrl, alt, F1 and this will bring you to the command prompt. login and use the command ```
metacity --replace
```

---

### Post by vidyutandambi on 2008-08-06
> **overdrank said:**
> Ok use the keys ctrl, alt, F1 and this will bring you to the command prompt. login and use the command ```
metacity --replace
```

let me a bit more precis about what i have done.
i have edited my /etc/X11/xorg.conf there i have changed the driver name from nvidia-glx-new to nvidia-glx and from the "apearence" menu of preferences i have changed the desktop effect as "none" no desktop effect.
so now i am getting what is that.i m able to see the all the content window of application, places,system e.t.c i.e. all right click as well as left click window is visible now.
but now now problem is this when i m trying to change the desktop effect from the aperence tab in the preferences the again i m getting the ssame problem. and one more this is that whenevr i am starting my computer i am able to get the resolution of 1280x1024@60hz in the startup window but after logging in again the resolution of 800x600@50hz is coming .
everytime i have to b root in my terminal and then i have to open nvidia-settings to change the resolution.
after changing the resoltution i am alway saving it to /etc/x11/xorg.confg but nothing is happening..
1280x1024@60 resolution will continue till i dint restart my compuetr.

tell me how to fix the resolution for always.so that i need not to fix it afetr each startup.
and the way to use the desktop effect.

i have tried with 
ur code
metacity --replace...
no result....
please solve my issue..

---

### Post by northern lights on 2008-08-06
Run ```
sudo apt-get update && sudo apt-get install nvidia-xconfig nvidia-settings && sudo nvidia-xconfig && sudo /etc/init.d/gdm restart
```

This should allow you to adjust your settings by running 'nvidia-settings' they should remain permanent. The third command, 'nvidia-xconfig' might not have to run as root (Don't want to try right now, my system runs).

---

