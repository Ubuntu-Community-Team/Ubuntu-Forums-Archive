---
title: "Ubuntu 24.04 blank screen with AMD HD 7850 on DVI"
date: 2024-05-29
forum: Hardware
---

### Post by jey815 on 2024-05-29
Hi,

I just installed Ubuntu 24.04 64 bits on my computer.
My specs are:
[LIST]
[*]Gigabyte P35 
[*]Intel Core 2 Quad Q9550 
[*]8GB RAM 
[*]Sapphire HD 7850 2GB DDR5 
[/LIST]

The installer only works in safe graphics mode, if I boot up the installer in normal mode I get a blank screen.
I was able to install Ubuntu using the safe graphics option, but as expected I got a blank screen after rebooting. It's not even a blank screen, the display just turns off after the grub.
I can boot into Ubuntu if I add the kernel parameters "nomodeset" or "acpi=off". I don't need to add both of them at the same time, however with "acpi=off" the computer won't power off by itself, I have to press the power button after telling ubuntu to power off.

I made sure my ubuntu installation is up to date.

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP] [1002:6819]
    Subsystem: PC Partner Limited / Sapphire Technology Radeon HD 7850 2GB GDDR5 DVI-I/DVI-D/HDMI/DP [174b:e221]
    Kernel modules: radeon, amdgpu
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000 Series] [1002:aab0]
```

```
sudo lshw -c video
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: Pitcairn PRO [Radeon HD 7850 / R7 265 / R9 270 1024SP]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff memory:f5000000-f503ffff ioport:b000(size=256) memory:c0000-dffff
  *-graphics
       product: simpledrmdrmfb
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=2560,1440
```

Looking at the "UNCLAIMED" part no driver is loaded for my graphics card. And I see that there are 2 kernel modules listed "radeon, amdgpu".
I am pretty sure that at least the radeon one should work with this card, but no module is in use.
I saw people online using it without any problems, for example this post online
[https://linuxreviews.org/The_Current_State_Of_Older_AMD_Graphics_Hardware_On_Linux:_What_Driver_To_Use_And_What_To_Expect](https://linuxreviews.org/The_Current_State_Of_Older_AMD_Graphics_Hardware_On_Linux:_What_Driver_To_Use_And_What_To_Expect)
they were able to use both radeon and amdgpu with the card that I have.
In the Linux hardware database, many users have this card working on Ubuntu. List of system with the card working: [https://linux-hardware.org/?id=pci:1002-6819-174b-e221](https://linux-hardware.org/?id=pci:1002-6819-174b-e221)
Why does my system use neither of them?
I have no idea how to continue from here to fix this problem. In windows 10 everything works well, so I don't suspect an hardware problem.

EDIT: Changed to title to reflect the real issue - no output on dvi after boot
[https://ubuntuforums.org/showthread.php?t=2498074&p=14192161#post14192161](https://ubuntuforums.org/showthread.php?t=2498074&p=14192161#post14192161)

---

### Post by Yellow Pasque on 2024-05-30
What happens if you try to load amdgpu manually?
```
sudo modprobe -v amdgpu si_support=1
```
If you don't get any errors, try logging out/in after that.

---

### Post by Yellow Pasque on 2024-05-30
Wait, are you still booting with "nomodeset"? If so, that's why kernel modules aren't loading. Try booting without nomodeset and instead boot with:

```
modprobe.blacklist=radeon amdgpu.si_support=1
```

Note: radeon module should theoretically work, but there seems to be a problem with it.

---

### Post by jey815 on 2024-05-30
> **Yellow Pasque said:**
> Wait, are you still booting with "nomodeset"? If so, that's why kernel modules aren't loading. Try booting without nomodeset and instead boot with:

```
modprobe.blacklist=radeon amdgpu.si_support=1
```

Note: radeon module should theoretically work, but there seems to be a problem with it.

Yes, I hade the nomodeset option.
I wasn't quite sure what it did, it was recommend somewhere else.

> **jey815 said:**
> I was able to install Ubuntu using the safe graphics option, but as  expected I got a blank screen after rebooting. It's not even a blank  screen, the display just turns off after the grub.

Ok, so, the radeon driver does load and the card works on ubuntu. I was looking at the wrong place, it was not a driver problem.
What is not working are the DVI ports. The graphics card has 2 DVI ports, a DVI-I and a DVI-D. On Windows they work fine, but on Ubuntu for some reason they don't seem to display by default.

I plugged another monitor to HDMI and noticed that it was working normally. I can then, plug a monitor to the DVI port, after login in to Ubuntu, and if I mirror the monitors, they will both work. After that I can choose the option to join monitors, and I get both of them working.
After rebooting, the issue comes back, there is no DVI output after gub.

---

### Post by guiverc on 2024-05-30
Did you try following the Lubuntu manual?

Lubuntu media does not include closed-source kernel modules, that can be found in other Ubuntu Desktop media.. but those can be installed after first boot.

In the manual, it's found at [https://manual.lubuntu.me/stable/4/4.2/software_sources.html](https://manual.lubuntu.me/stable/4/4.2/software_sources.html)  in the "*Proprietary Drivers*" section.  You use safe-graphics on the install media to get the system installed, then add what you need after first boot. Have you tried adding additional drivers as outlined in the manual?  Did the OS find any?

You've put this is the Lubuntu section of this forum, but mention Ubuntu..   I'm not sure if you're using Lubuntu or Ubuntu  (*Lubuntu is a Ubuntu OS, but it will install different packages, with some differences in defaults*)

---

### Post by Yellow Pasque on 2024-05-31
I'd still try and force amdgpu module just to see if it's caused by the kernel module or something else:
```
radeon.si_support=0 amdgpu.si_support=1
```

> **guiverc said:**
> Did you try following the Lubuntu manual?
Have you tried adding additional drivers as outlined in the manual?  Did the OS find any?


Exactly what closed-source driver(s) are you talking about?

---

### Post by guiverc on 2024-05-31
> **Yellow Pasque said:**
> I'd still try and force amdgpu module just to see if it's caused by the kernel module or something else:
```
radeon.si_support=0 amdgpu.si_support=1
```

Exactly what closed-source driver(s) are you talking about?

None specifically, but as the Lubuntu ISOs come with only the basic kernel modules (*where as ubuntu-desktop-installer used by Ubuntu Desktop & other flavors can include more*; *albeit increasing ISO size*) if any are required, they need to be installed post-install using `ubuntu-drivers autoinstall`.

---

