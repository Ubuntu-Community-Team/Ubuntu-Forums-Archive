---
title: "Graphics issues after moving system to all new hardware"
date: 2012-12-24
forum: Hardware
---

### Post by dblicken on 2012-12-24
I recently moved my Ubuntu system to almost all new hardware (motherboard, CPU, Memory and Graphics Card) and I am having intermittent issues with the graphics. 

Graphics card is AMD Radeon HD 6570

1. When I first put everything together I was having problems booting into GRUB, however it pretty consistently loads GRUB now.

2. Sometimes when I choose to boot Ubuntu it starts to load but the screen goes to a blank lighter purple color than the normal start up screen. Based on sound, I can tell that I am able to type in my password and log in but the screen doesn't change. I tried leaving it for a while to see if it would eventually load but no luck.

3. Sometimes when I choose to boot Ubuntu, the screen flickers constantly and the whole screen seems to be shifted and wrapped around the other side. (The "left edge" of my screen is just to the right of center and I have to move the cursor to past the right edge to wrap around to the rest of the desktop)

I haven't nailed down a pattern yet but it seems like if I try to boot into recovery mode, it still has problems but the next boot will be completely normal. Other times it will boot normally without me noticing that I did anything.

When it boots into the flickering offset screen, I can reinstall the fglrx package and the next boot is usually successful or that light purple screen.
 

I am also having trouble booting into Windows, however, I can't remember the last time that I even tried; so I have no evidence that it wasn't broken before the hardware change.

---

### Post by Bashing-om on 2012-12-24
dblicken; Hi ! Welcome to the forum.

Sounds like a graphics issue;
To see your graphics card and info: From the desk top-> ctl+alt+t (combo keys) activates a command line interface (terminal), post the out put of these terminal commands:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga
``` <- better info

as a before note: have you tried booting up with the boot parameter "nomodeset" and using the "Additional Driver" utility to  load the recommended driver ?
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by dblicken on 2012-12-24
Here are the outputs from your commands:

$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: Turks [Radeon HD 6570]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:42 memory:d0000000-dfffffff memory:fddc0000-fdddffff ioport:ee00(size=256) memory:fdd00000-fdd1ffff

$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Turks [Radeon HD 6570]

$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Turks [Radeon HD 6570] [1002:6759]
	Subsystem: ASUSTeK Computer Inc. Device [1043:0403]
	Kernel driver in use: radeon
	Kernel modules: fglrx, radeon

> have you tried booting up with the boot parameter "nomodeset"
[INDENT]No I have not but I will try.[/INDENT]

> and using the "Additional Driver" utility to  load the recommended driver 

[INDENT]Yes and it seems to install the driver without error.[/INDENT]

Thank you for your reply. Any help is appreciated.

---

### Post by Bashing-om on 2012-12-24
dblicken;

I looking to see if I can find an alternative.
The output shows the "open source" driver "radeon" as the one installed. That sucker (driver installer) is pretty smart, may not have a better alternative.
[INDENT][INDENT]I'll Be Back <== BDQ

[/INDENT][/INDENT]

---

### Post by dblicken on 2012-12-24
Adding "nomodeset" to the boot parameters seems to have solved the problem. After adding it, I had several successful boots in a row.


Thanks for your time.

---

### Post by Bashing-om on 2012-12-24
dblicken;

That is not a good solution. As that also disables kernel mode setting. But, it does go to show the problem is the graphics driver.

For a better solution try and load the fglrx driver. This howto:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
In this situation I suggest that you purge your other attempts (code is in the howto) and follow the directions in the command line installation method to install the fglrx driver.
[INDENT]try'n to help <== BDQ

[/INDENT]

---

### Post by QIII on 2012-12-24
One thing in that link that I haven't gotten around to updating is that the instructions for uninstalling the driver if you have installed it from the ATI website is a bit buried.

If you installed from the ATI website, you need to use the amdconfig utility to uninstall.```
sudo amdconfig --uninstall
```

---

