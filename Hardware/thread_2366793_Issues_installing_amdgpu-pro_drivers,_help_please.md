---
title: "Issues installing amdgpu-pro drivers, help please"
date: 2017-07-21
forum: Hardware
---

### Post by lukas522 on 2017-07-21
Hi, first at all my apologies for my poor english. Its not my native language.

Well, i will tell what is my problem:

I have a laptop with dedicated graphics card (AMD R7 m445) identified by Windows 10 without any problems. Also i've installed UBUNTU (16.04.02) updated manually right now.

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

```

If I type [I]lshw -C display
[/I] i get:
```
$ $ sudo lshw -C display
[sudo] password for devel: 
Lo sentimos, vuelva a intentarlo.
[sudo] password for devel: 
  *-display               
       descripción: VGA compatible controller
       producto: Intel Corporation
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 02
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pciexpress msi pm vga_controller bus_master cap_list rom
       configuración: driver=i915 latency=0
       recursos: irq:280 memoria:d1000000-d1ffffff memoria:b0000000-bfffffff ioport:f000(size=64) memoria:c0000-dffff
  *-display
       descripción: Display controller
       producto: Topaz XT [Radeon R7 M260/M265]
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: c3
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi bus_master cap_list rom
       configuración: driver=amdgpu latency=0
       recursos: irq:281 memoria:c0000000-cfffffff memoria:d0000000-d01fffff ioport:e000(size=256) memoria:d0200000-d023ffff memoria:d0240000-d025ffff
```

Forget the spanish part, the system gets my graphics card as *Radeon R7 M260/M265* and not as *M445*. 

If i run GpuTest i get the result of the attached image (1Resultado GPUTest.png)

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=276091&d=1500677448[/IMG]

And already i have any additional driver disabled then I guess I am doing something wrong.

Going back to the results of *lshw -C display* command, those cards (M445, M260 and M265) appears as supported by AMDGPU-PRO and I installed that driver as the page says in the manual but I get an error during installation process (I dont know here to find the log of that error but the snapshot is the second attachment) but installer says "Install complete". But when I reboot the system can't load graphic login, says it is working in low resolution and only I can log as old school with Ctr + Alt + F1...F6 in order to run uninstallation script.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=276092&d=1500678310[/IMG]

How can I do that driver installation? or where is the error to fix it?

Can anybody help me?

Thanks in advance for any suggestion.

---

### Post by QIII on 2017-07-21
Hello.

Have you attempted to disable the Intel graphics through your BIOS/EFI?

---

### Post by lukas522 on 2017-07-21
Yes, i tried but i didn't found where or how. Unfortunately i'm very novice with that system (I've been working years ago with bios) X(

I will look on Internet looking for that and if it fix my problem i will publish how.

Thanks

---

### Post by lukas522 on 2017-08-03
No way, i can't disable intel graphics from EFI. I cant find how :(

---

