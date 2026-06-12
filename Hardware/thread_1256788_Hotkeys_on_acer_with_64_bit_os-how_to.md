---
title: "Hotkeys on acer with 64 bit os-how to?"
date: 2009-09-03
forum: Hardware
---

### Post by arcull on 2009-09-03
Hi everyone. I got stuck with 64 bit version of Kubuntu 9.04 when trying to get my hotkeys (volume,play,pause,brightness..) working on Acer emachines g725. What I already tried is: I did install acerhk driver, but when I try to link it as module in kernel using m-a utility, I just can't see it. When I took a better look on the homepage of the autohr of acerhk [http://www.cakey.de/acerhk/]("http://www.cakey.de/acerhk/") I saw it can not be used on 64 bit linux. I did try to compile it on my own, but no luck. Now I would really need some help with this :(, is there maybe some workaround for this? How did you guys manage hotkeys on laptops? Thanks for your help.

---

### Post by newton21989 on 2009-09-03
Run xev in a terminal window and see if you get any output from those keystrokes. If so you could bind the commands to keystrokes using something like lineak.

---

### Post by arcull on 2009-09-04
> Run xev in a terminal window and see if you get any output from those keystrokes. If so you could bind the commands to keystrokes using something like lineak. thanks mate, I'll try it when I get home. Suppose some event (trigger) fires when I press the keys, how can I bind them to hardware commands? You mentioned lineak, is somewhere any guide available for this? Thanks again.

---

### Post by arcull on 2009-09-08
Uf, I'm still stuck with this :( , I've found out that xev can find the hexa codes of keys I press, but there is no way of linking them to actual commands, that would command the hardware. Googling around revealed I must have some module which would support this special keys. Acerhk is for older 32 bit kernles and there is  a module named acer-wmi, that should do equal job on 64 bit kernel. The only problem now seems to find it :( ...I can't see it as available module in module assistant. Does anyone know where could I download it, or is it maybe already on my system and I just can't find it.:-k Any advice much appreciated.

---

### Post by arcull on 2009-09-08
The never ending story , I've found out that module acer-wmi is available for my x64 kernel, I did list all available modules via```
modprobe -l |grep acer
kernel/drivers/misc/acer-wmi.ko

```, but I can not load it into kernel ```
sudo modprobe acer-wmi
FATAL: Error inserting acer_wmi (/lib/modules/2.6.28-15-generic/kernel/drivers/misc/acer-wmi.ko): No such device

``` which means (found out by googling) that acer-wmi isn't compatible with my BIOS. Grrrrrr, is there anything else I could try? An interesting thing is that if try to use my Fn+Arrow keys to change brightness of screen when in grub menu, it works ok, however in kde no avail with it. Is there maybe any other third-party modul available that I could try? Still searching for help

---

### Post by arcull on 2009-09-14
The solution is always simple if you know it :) , well since the most crucial hotkeys for me are those for changing brightness and I don't care for multimedia keys very much, you just add **acpi_osi=Linux** to the file /boot/grub/menu.lst and that's it.

---

