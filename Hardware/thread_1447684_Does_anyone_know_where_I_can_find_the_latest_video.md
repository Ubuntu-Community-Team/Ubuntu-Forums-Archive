---
title: "Does anyone know where I can find the latest video drivers for the Asus Eee 1201N?"
date: 2010-04-05
forum: Hardware
---

### Post by TheBiles on 2010-04-05
I just got the wireless drivers installed, but I need the drivers that are made specifically for the nVidia ION.  Any help is appreciated!

---

### Post by PaulReaver on 2010-04-05
Any particular ion or are they all the same?

It appears that there are four different ion's
Ion (desktops)
Ion (notebooks)
Ion LE (desktops)
Ion LE (notebooks)

yours is a eeepc so its either
Ion (notebooks) or Ion LE 

check [here]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")

---

### Post by PaulReaver on 2010-04-05
is it 32bit ubuntu?

---

### Post by hsoulen on 2010-04-07
[LIST=1]
[*]Go to the Nvidia website, choose download drivers.
[*]Choose "ION Notebook"
[*]Choose "Linux 32-bit" or "Linux 64-bit"
[*]Download the driver
[*]Save to a directory under home (e.g. /home/"yourusername"/nvidia)
[*]Close your window manager (e.g. "sudo gdm-stop" from the terminal for gnome)
[*]Run the install script: "sudo ./NVIDIA-Linux-x86-190.53-pkg1.run" (e.g. for the 190.53 32-Bit driver)
[*]Enjoy.
[/LIST]

---

### Post by emoguitarist06 on 2010-05-04
WHY?

I also have the 1201N
the Nvidia propriety drivers are included in Ubuntu 
System>Administration>Hardware Drivers
Both versions in 9.10 & 10.04 worked amazing well with me
compiz and world of warcraft work awesome

---

### Post by hsoulen on 2010-05-05
> **emoguitarist06 said:**
> WHY?

I also have the 1201N
the Nvidia propriety drivers are included in Ubuntu 
System>Administration>Hardware Drivers
Both versions in 9.10 & 10.04 worked amazing well with me
compiz and world of warcraft work awesome

Absolutely! Second this answer, only problem is if for some reason the person does not have the restricted repositories chosen in Synaptic.

If you do NOT have the option listed in Hardware Drivers to select the Nvidia proprietary drivers, you need to open Synaptic (System->Administration->Synaptic) and search for Nvidia, then choose to install "nvidia-current".

This should add the driver (most recent in most cases) as well as the vdpau libraries for video decoding and then add the option to select this driver under "Hardware Drivers".

Cheers,

Hank

---

