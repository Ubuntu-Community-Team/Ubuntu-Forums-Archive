---
title: "how to see hardware details (Ubuntu 8.04)"
date: 2008-11-07
forum: General Help
---

### Post by gotix on 2008-11-07
I just re-installed a 8.04 Ubuntu on a computer. It installs all hardware without problems. However I would like to see details about the hardware.
I noticed that:
- Information about sound card can be obtained at "System -> Preferences -> Sound"
- Information about CPU, Memory, Ubuntu versions can be obtained at "System -> Administration -> System Monitor -> System tab.

However I would like to know how can I see details about the Video Card, Motherboard model, Network Adapter, CD-ROM and Hard Disks models. I know I can see some of those in /var/log/dmesg, but I would like something in graphics mode

thanks

---

### Post by _sAm_ on 2008-11-07
System > Prefrences > System Profiler and Benchmark will give you some info.

Better programs with gui for this would be *sysinfo* and *hardinfo* After you installed them go to Applications > System Tools
```
sudo aptitude install hardinfo sysinfo
```

You can also use cli programs, lshw is already installed(and has a gui you can install called lshw-gtk), and you can try hwinfo.
In a terminal just run; lshw

---

### Post by beno1990 on 2008-11-07
In the terminal:

```
sudo lshw
```

But that's a text only version, so try

```
sudo apt-get install lshw-gtk
```

It should then appear in one of your menus as "hardware lister".

It seems to appear in the menus rather arbitrarily, though; it appeared under preferences on my computer for some reason, so you might have to dig through your folders for it once it's installed.

---

### Post by renzokuken on 2008-11-07
```
lspci
```
and
```
lsusb
```

---

### Post by gotix on 2008-11-07
thanks a lot! very usefull info.

minor observations:
lshw is great - it detects and shows all the hardware present in the PC, however the lshw-gtk does not show any info about hard disk, CDROM's and network card.
sysinfo - last version is from 2006, it does not show some info (sound card, video card)
System > Prefrences > System Profiler and Benchmark - This is hardinfo. It shows almost everything.

Anyways I would say the most complete information (even motherboard model) you can get from text mode "lshw" command

---

### Post by Odyssey1942 on 2008-12-09
My System/Preferences does not have a 'System Profiler and Benchmark' option. When I first installed it, there was no partition editor and I managed to get it to show, but cannot remember how.

How can I get System Profiler and Benchmark to show in mine?

---

