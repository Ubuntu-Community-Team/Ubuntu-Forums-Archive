---
title: "Graphic driver problems on HP g62-a50sm notebook pc"
date: 2011-03-27
forum: Hardware
---

### Post by kahwedyich on 2011-03-27
Hi. 

I'm using Ubuntu 10.10 x64 on a HP g62-a50sm laptop.

This notebook has:
irfan@irfan-HP-G62-Notebook-PC:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] [1002:68e0]

I installed Ubuntu 10.10 clean, and when the system booted up it it showed me the list of restricted (proprietary) drivers that I could install. The wireless driver installed fine, but when Installed "ATI/AMD proprietary FGLRX graphic driver" and rebooted the system it wouldn't go to the GUI. Instead it offered me a command line login.

Now there's more to this problem, the screen turns off a few seconds after I'm past the GRUB menu.
I connected an  external monitor to the VGA output, and that turned the both screens on, but I obviously can't do that every time system boots up:

This was happening even before I installed fglrx drivers; monitor would turn off and I wouldn't see the splash screen, but it would turn on once the system is fully booted up. 

So now I renamed the xorg.conf file, so the system wouldn't use it. I'm not really sure which driver is in use right now, but the system boots up the same as it did before I installed the driver

What I would really like to achieve is the same behavior this laptop has in Windows, where I can switch between the dedicated Ati card and the integrated Intel graphics as I wish.

Alternatively I'd use only the Intel graphics, because the Ati card really drains the battery.

PS : I also tried other Linux distros, they had the same problem.

---

### Post by linuxuser12345 on 2011-03-27
I had a similar problem with Debian. Try using a different version of Ubuntu

---

### Post by Yellow Pasque on 2011-03-27
For switchable graphics on Linux, you have to use open-source drivers and the vga_switcheroo script. Fglrx isn't going to work unless you can disable the intel IGP in the BIOS. A distro change won't help (well, maybe Fedora has vga_switcheroo installed by default).

---

### Post by realzippy on 2011-03-27
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)   :

*You can try it by installing the module and calling it like this:*

```
git clone http://github.com/mkottman/acpi_call.git

cd acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh
```

If you get a *works!* somewhere in the output it is a good sign,
checking your battery power before/after will prove if the ati card is shut off..

---

