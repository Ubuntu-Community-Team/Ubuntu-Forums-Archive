---
title: "Can't get the right graphic controllers with Ubuntu 13.04"
date: 2013-05-16
forum: Hardware
---

### Post by jony7so on 2013-05-16
I have ubuntu 13.04 64 bits
I've tried a lot of things before posting here, but none have worked.
This is my problem: I tried to play TF2, but the colors were wrong (blue screen with some other colors dispersed, I could tell that game itself worked only graphics were messed up).
I need the right drivers for my card. Running **lspci** returns "VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)". My card uses Intel HD Graphics.
My current installed drivers are: **Intel® Ironlake Mobile**, however, **I don't believe this to be the right driver**.
I hope somebody can help with this and **thank you** for taking the time to read this!

---

### Post by CatKiller on 2013-05-17
Intel graphics drivers are included in the kernel; it's unlikely (although not impossible, obviously) that the wrong driver would be used. What makes you think that it has been?

---

### Post by richierich1986 on 2013-05-17
What are your hardware specs exactly? This would help in finding a solution to your problem.

---

### Post by jony7so on 2013-05-18
[B][B][COLOR=#000000][FONT=Arial]I use Windows with this same laptop and everything works fine. However with ubuntu videos seem to lag more and I can't play Team Fortress 2. The game worked fine in Windows 7 but when I try to play it wrong colors appear and the game is almost unrecognizable. You can click on things and hear the sounds but graphics themselves are all messed up.
I changed my HDD and installed Ubuntu and was trying to get by without having to install windows again...
Info:[/FONT][/COLOR]
[/B]
[COLOR=#000000][FONT=Arial]My laptop is an Acer Aspire 5742 with:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- intel core i5 460M processor[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- Intel HD Graphics (I don't remeber exactly my card's details sorry :([/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]I will put some commands and their output below that people have asked for in similar cases, to give more info:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]command:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**glxinfo | grep OpenGL | head -n3**[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]output:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL vendor string: Intel Open Source Technology Center[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]OpenGL version string: 2.1 Mesa 9.1.1[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]command:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**lspci | grep VGA**[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]output:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]command:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**sudo lshw -C video**[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial][/FONT][/COLOR][COLOR=#000000][FONT=Arial]output:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]*-display               [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       product: Core Processor Integrated Graphics Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       physical id: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       bus info: pci@0000:00:02.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       version: 02[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       capabilities: msi pm vga_controller bus_master cap_list rom[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       configuration: driver=i915 latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       resources: irq:42 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:3050(size=8)
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR][/B]

---

### Post by Mark Phelps on 2013-05-19
You could try the link and see if there are any newer drivers there:  [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng")

---

### Post by Cheesemill on 2013-05-19
> **Mark Phelps said:**
> You could try the link and see if there are any newer drivers there:  [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13815&lang=eng)

There aren't. In fact 13.04 currently ships with xserver-xorg-video-intel version 2.21.6 which is newer than the version available from the Intel website.

@jony7so
You are already using the only Intel driver available, it is installed when you first install Ubuntu.

---

### Post by jony7so on 2013-05-19
Does that mean I can't do anything about it? :(

---

