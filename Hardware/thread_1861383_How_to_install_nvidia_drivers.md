---
title: "How to install nvidia drivers?"
date: 2011-10-15
forum: Hardware
---

### Post by maleicon on 2011-10-15
Hi, 

I've been trying to get my graphic card working under ubuntu and opensuse but to no avail.

First, i tried through additional drivers, but after installation it keeps saying "this driver is activated but not currently in use". That is 3D-accelerated proprietary graphics driver for NVIDIA cards. (version current).

Nvidia settings panel says: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

The thing is when I run 'nvidia-xconfig' it replaces my xorg.conf file (it is supposed to do that) and when I restart the computer, I can't log back, it displays only the console prompt, no GUI. If I change to su and type init 6 it hangs on the welcome screen. Only when i delete xorg.conf I'm able to log in to GUI.

Secondly, I tried installing drivers downloaded from nvidia site from level 3, but it is the same.
I had to install gcc, make and kernel-sources because the install program reported errors. But after installing them it finishes installing driver all right. I log in, nvidia settings panel again says "You do not appear to be using the NVIDIA X driver", so I run 'nvidia-xconfig' and restart x and cannot log in to level 6.

I have nvidia GT 420M

---

### Post by CharlesT423 on 2011-10-15
It sounds like you might be using the nouveau drivers instead of the nVidia supplied ones.  Try running these commands and then reboot:

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```The "add-apt-repository" line can be skipped if you want, it's just  adding a new software source that has the latest versions of the various  video drivers.

After the reboot run "dmesg |grep -i nvidia" and you should see something like this:
```

# dmesg |grep -i nvidia
[   16.449472] nvidia: module license 'NVIDIA' taints kernel.
[   16.541636] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.541642] nvidia 0000:01:00.0: setting latency timer to 64
[   16.541702] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
[   16.558768] hda_intel: Disable MSI for Nvidia chipset

```The important part is the "loading NVIDIA UNIX ... Kernel Module X" part.  That says you are loading the nVidia supplied drivers and not the open source nouveau ones.

---

### Post by maleicon on 2011-10-15
nvidia-current is installed already.

dmesg |grep -i nvidia output looks like this

```
dmesg |grep -i nvidia
[   23.998001] nvidia: module license 'NVIDIA' taints kernel.
[   24.077174] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   24.077178] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   24.077187] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.077194] nvidia 0000:01:00.0: setting latency timer to 64
[   24.077303] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  285.05.09  Fri Sep 23 17:31:57 PDT 2011
```

so, is it loading the driver but not using it?

---

### Post by flierman on 2011-11-20
Not this bug?

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/661248](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/661248)

I have the same problem, activated but not in use...works randomly at some boot but mainly not.

Blacklisted nouveau but it didnt help.

---

### Post by rajeeja on 2011-12-23
NVIDIA Optimus Technology is currently not supported by Ubuntu. There is this bumblebee thingy, not sure how far along that is in switching the graphics card b/w nvidia and intel. 

We'll have to wait and watch, if somebody knows the latest development please update.

---

### Post by rajeeja on 2011-12-23
[http://scientificlinuxforum.org/m/index.php/t669.html](http://scientificlinuxforum.org/m/index.php/t669.html)
 
THis"NVIDIA GeForce GT 520M graphics card with 1GB DDR3 VRAM and NVIDIA Optimus Technology for smooth HD playback and Direct X 11 causal gaming with smart, battery-saving efficiency"

Has problems..

---

### Post by SACHINVD on 2012-01-01
> **maleicon said:**
> Hi, 

I've been trying to get my graphic card working under ubuntu and opensuse but to no avail.

First, i tried through additional drivers, but after installation it keeps saying "this driver is activated but not currently in use". That is 3D-accelerated proprietary graphics driver for NVIDIA cards. (version current).

Nvidia settings panel says: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

The thing is when I run 'nvidia-xconfig' it replaces my xorg.conf file (it is supposed to do that) and when I restart the computer, I can't log back, it displays only the console prompt, no GUI. If I change to su and type init 6 it hangs on the welcome screen. Only when i delete xorg.conf I'm able to log in to GUI.

Secondly, I tried installing drivers downloaded from nvidia site from level 3, but it is the same.
I had to install gcc, make and kernel-sources because the install program reported errors. But after installing them it finishes installing driver all right. I log in, nvidia settings panel again says "You do not appear to be using the NVIDIA X driver", so I run 'nvidia-xconfig' and restart x and cannot log in to level 6.

I have nvidia GT 420M

Hi maleicon
I am facing exactly same issue.
Did you get any solution for it ?

Thanks

---

