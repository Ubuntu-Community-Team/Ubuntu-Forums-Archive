---
title: "Laptop brightness function keys not adjust brightness on laptop with hybrid graphics"
date: 2019-06-25
forum: Hardware
---

### Post by forcephenomenon on 2019-06-25
[COLOR=#000000][FONT=sans-serif]Hello all,[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]I'll lead in with an apology if this had already been addressed somewhere else, I've scoured google for the past month to no avail. Also, Linux is not my forte, so if I'm missing something obvious or have failed to execute a command that might otherwise be obvious to some, I again apologize. This is my first time posting here after trying kubuntu forums and level 1 techs to no avail.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]My laptop's is an older model, HP Zbook 17 G2. The GPUs I am working with are as such, via lscpi:[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]```

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XT [Radeon R9 M280X]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=sans-serif]
Wiped Windows off it, loaded it to the max with 32GB of ram and a few SSD's to make it a solid portable light virtualization platform and means of teaching myself Linux to a greater degree. Everything worked out of the box when installing Kubuntu 19.04, with the exception of the brightness keys. The prompt for the brightness meter would pop up and scale up and down, but it wouldn't actually change the brightness.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]An ls of /sys/class/backlight/ yields two results, intel_backlight and radeon_bl0. Poking around showed the brightness keys were modifying the files in radeon_bl0, but that intel_backlight was the one that actually changed  the brightness when poking the brightness setting inside its folder.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Googling yielded that putting the following into 20-intel.conf inside /usr/share/X11/xorg.conf.d/ would fix the problem:[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]```

Section "Device"
  Identifier  "Intel Graphics"
  Driver      "intel"
  Option      "AccelMethod" "sna"
  Option      "Backlight"  "intel_backlight"
  Option      "TearFree"   "true"
  BusID       "PCI:0:2:0"
EndSection
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=sans-serif]Sure enough, it did. Graphics were a tad wonky after that but I didn't think much of it, until I noticed performance in 3D apps absolutely tanked. Yet more digging showed that by doing this, it completely disabled the Radeon's output to xrandr, couldn't use it for anything after that.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]After yet more googling, tried the acpi_backlight=vendor or video edit in grub, didn't work. xbacklight didn't work. I am stumped. I can't install the AMD proprietary drivers for the radon gpu, they're too old.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Any insights/assistance would be greatly appreciated, and I am more than happy to post any other necessary information.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Thank you.[/FONT][/COLOR]

---

