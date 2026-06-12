---
title: "Laptop GPU fan wont spin up, GPU overheats/throttles"
date: 2014-12-07
forum: Hardware
---

### Post by Steve_Owens on 2014-12-07
Hello guys.  I recently installed 14.10 on my older core 2 duo nvidia 9800gts laptop (PM45 intel chipset on a Gateway p-7803h).  Everything seems to have gone great thus far, except anything graphic related causes the GPU to quickly climb to 110 degrees, which throttles it from 1500Mhz to about 93Mhz, and of course anything graphic related at that point slows to a crawl.  The fan definitely doesn't bother to go on at all.  I've been trying to find a way to enable some form of manual fan control, or otherwise allow the laptop to properly throttle up the fan speed as the GPU temp increases like it does in Windows.  I've of course tried things thus far.

Installed latest Nvidia drivers (340.something) and tried everything related to coolbits to enable driver fan control without success.  The option just doesn't show up in nvidia-settings, though this may simply be due to the fact it is a mobile GPU.

My BIOS has no fan settings at all, so I can't do anything there.

Really I'm just looking to see if anyone has ran into this before and what cane be done.  With Steam now being on Ubuntu, I thought I would finally be able to get rid of Windows, but without my GPU fan running, gaming is of course impossible.

Edit - I also tried fancontrol route and pwmconfig shows "/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed"

Edit 2 - Optput from sensors

steve@Steve-Laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.0°C  (crit = +90.0°C)
temp2:        +49.0°C  (crit = +110.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +39.0°C  (high = +90.0°C, crit = +90.0°C)
Core 1:       +40.0°C  (high = +90.0°C, crit = +90.0°C)

---

### Post by Steve_Owens on 2014-12-07
Switched to Nouveau driver, and get more output from sensors.

steve@Steve-Laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +48.0°C  (crit = +90.0°C)
temp2:        +48.0°C  (crit = +110.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +38.0°C  (high = +90.0°C, crit = +90.0°C)
Core 1:       +40.0°C  (high = +90.0°C, crit = +90.0°C)


nouveau-pci-0100
Adapter: PCI adapter
temp1:        +73.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +2.0°C)
                       (emerg = +110.0°C, hyst =  +5.0°C)

However with these drivers, steam games don't even load.  Steam pops up error that direct rendering isn't enabled (even though glxinfo says direct rendering yes..).  It just feels like I'm so close to being rid of Windows.

---

### Post by weatherman2 on 2014-12-07
How do you know the fan itself is working?  Did it work in Windows?  Does it come on when you are say reading the BIOS Setup screen before booting an OS?

---

### Post by Steve_Owens on 2014-12-07
Ya it absolutely works in Windows. It does run very slow in Ubuntu (like it's 1st setting, nearly dead quiet), it just doesn't adjust up to the higher speeds as the GPU gets warmer like it does in Windows.

---

### Post by weatherman2 on 2014-12-07
Have you tried other Ubuntu versions, like 14.04?  You should be able to boot live and try it right?

There are a few tricks to set in your /etc/default/grub file - have you tried those?

[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

You might try [COLOR=#333333][FONT=Ubuntu]acpi_osi=Linux 

[/FONT][/COLOR]To try these in your installation, in the file /etc/default/grub you can change the line GRUB_CMDLINE_LINUX_DEFAULT to add " acpi_osi=Linux" to what is currently there, then run sudo update-grub, then reboot.

---

### Post by Steve_Owens on 2014-12-07
Thanks for the tips.  Tried the grub option without success.  For testing, I loaded up handbrake and encoded a video, CPU temp never exceeded 65, so CPU seems fine.  For the GPU, I loaded up Kerbal Space and just left it at the main menu.  Temps just slowly raised from 63 to 110 again with no change in fan speed.  I'll try live booting another OS.  I guess the tricky part is running a program that stresses the GPU with a live OS.

---

