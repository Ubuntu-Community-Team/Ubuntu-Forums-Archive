---
title: "Graphics issues HP EliteBook X360 1040 G6 [20.04 LTS]"
date: 2022-01-05
forum: Hardware
---

### Post by jona1995 on 2022-01-05
Hello everyone !

I've just installed Ubuntu 20.04 LTS on a HP EliteBook X360 1040 G6 and everything seems to work fine except for the graphic card. The screen refresh very oddly:  random parts of the screen do not update unless I move my cursor over it.
 Also, the available refresh rates are reported incorrectly: it's a 60Hz screen but Ubuntu let me pick higher values: 120,02/119,94/60,03/59,96/59,93/40,02

The GPU is listed as a "Mesa Intel UHD Graphics 620 (WHL GT2)". CPU is a "Intel Core i5-8265U".

Of course, if I use nomodeset, the problem is solved but software graphics comes with its own issues of screen tearing, etc.

I tried updated Mesa and oem kernel to no avail. Even reinstall Ubuntu just in case. Everything works perfectly on Windows.

BIOS update did not help either.

I add some screenshot of the system info in BIOS as attachements.

I will give you all the information you ask to track down the issue.

Thanks.

EDIT: Add requested infos:


```

$ lspci -k | grep -iEA5 'vga|3d'
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake) (rev 02)
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company UHD Graphics 620 (Whiskey Lake)
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200  v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0c)

```

```

$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       produit: UHD Graphics 620 (Whiskey Lake)
       fabricant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 02
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration : driver=i915 latency=0
       ressources : irq:187 mémoire:df000000-dfffffff mémoire:a0000000-afffffff portE/S:3000(taille=64) mémoire:c0000-dffff

```

```

$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.11.0-44-generic/kernel
Looking for nvidia modules in /lib/modules/5.11.0-44-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/5.11.0-44-generic/kernel
Looking for amdgpu modules in /lib/modules/5.11.0-44-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:3ea0
BusID "PCI:0@0:2:0"
Is boot vga? yes
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

---

### Post by Bashing-om on 2022-01-05
Hello jona1995; Welcome to the Forum -

This may be real tough to isolate as it is Intel, and Intel just works™ with ubuntu.

We can start the process by knowing exactly what hardware is installed:
Terminal commands:
```

lspci -k | grep -iEA5 'vga|3d'
sudo lshw -C display

```

And also what the kernel thinks of the graphic's modules.
```

cat /var/log/gpu-manager.log

```
Please use codes tags to relay the requested info back to the post:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT]all in the process
[/INDENT]

---

### Post by jona1995 on 2022-01-06
Hi ! Ok, here is the results of these three commands:

```

$ lspci -k | grep -iEA5 'vga|3d'
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake) (rev 02)
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company UHD Graphics 620 (Whiskey Lake)
    Kernel driver in use: i915
    Kernel modules: i915
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 0c)

```

```

$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       produit: UHD Graphics 620 (Whiskey Lake)
       fabricant: Intel Corporation
       identifiant matériel: 2
       information bus: pci@0000:00:02.0
       version: 02
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration : driver=i915 latency=0
       ressources : irq:187 mémoire:df000000-dfffffff mémoire:a0000000-afffffff portE/S:3000(taille=64) mémoire:c0000-dffff

```

```

$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.11.0-44-generic/kernel
Looking for nvidia modules in /lib/modules/5.11.0-44-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/5.11.0-44-generic/kernel
Looking for amdgpu modules in /lib/modules/5.11.0-44-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:3ea0
BusID "PCI:0@0:2:0"
Is boot vga? yes
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Error : Failed to open /dev/dri
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

Hope it helps ! Thank you for trying to help me :)

---

### Post by Bashing-om on 2022-01-06
Hey jona1995 -

> 
Hope it helps ! Thank you for trying to help me


Single card, so much for my thought of a dual graphic's card situation. 
As the kernel sees no issues at all and I have no Intel experience to guide; I am also at a loss as to how to proceed here.
Hopefully others here with that experience will pop in to render aid.

[INDENT]If I know more
[INDENT][INDENT]I would do more
[/INDENT][/INDENT][/INDENT]

---

### Post by jona1995 on 2022-01-07
Ok, thank you for trying anyway !

I have more precision that might help: The screen is a touch screen. Touch is working without issue but it seems the screen is not properly recognized. As I said, it reports incompatible refresh rate options. Also, in Energy, it reports a device called Wacom HID 4907 and there is a menu Wacom which just says "No stylus found".

Does someone think it can lead to strange conflict ?

Sometimes, the problem just disappear for no specific reason. Right now, I had the issue while starting this post, and it is now working properly. But as soon as I will reboot, it will be back. Maybe it will even come back just like like it went away right now so, yeah, I'm quite lost here...

EDIT: Yes, it came back just a few second after this post haha

EDIT2: Not actually sure it worked for a few minutes, it might just have been the way I was moving the cursor...

---

