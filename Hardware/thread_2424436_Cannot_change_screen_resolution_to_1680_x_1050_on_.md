---
title: "Cannot change screen resolution to 1680 x 1050 on DELL Optiplex 755"
date: 2019-08-08
forum: Hardware
---

### Post by raspberrypieman on 2019-08-08
I have an ASUS VW202S monitor with a single VGA port.
My computer is a DELL OptiPlex 755 with a DVI port and use a DVI - VGA cable to connect the two.
I am running Ubuntu 18.04.2 LTS and get a screen resolution of 1024 x 768.
However, I know the monitor is capable of 1680 x 1050, because I can run it at that resolution from a Raspberry Pi-3, running Raspberry Stretch.

On one forum, I found tips on using xrandr and executed these commands on my Ubuntu system:

xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
  and
xrandr --addmode VGA1 1680x1050_60.00
([COLOR=#222222][FONT=Verdana]I am aware, that if I find a solution, I will have to make the xrandr changes permanent.)
[/FONT][/COLOR]The commands executed with no errors.

Then I went to Settings, and the new resolution of 1680 x 1050 appears, but when I select it and click "Apply", my screen goes black and never returns, and I have to reboot.
Is there something else I need to do, install some additional drivers, for example?

---

### Post by Autodave on 2019-08-09
Since no one else has jumped in here, let me offer my only idea.  Some VGA cables are not capable of that high of resolution.  Is this the same cable that you used on the Raspberry? Perhaps try another known good cable.  Better yet if you can find the cable with a choke at each end.

---

### Post by him610 on 2019-08-10
@AutoDave
Raspberry Pi-3 utilizes HDMI not VGA. 

@RaspberryPiMan
The DELL OptiPlex 755 may be the issue. It is a legacy computer with integrated graphics, probably made for office work. Those computers did not need higher display resolutions. Just because your monitor is capable of higher resolution does not mean every graphics chip can generate the higher resolution.

---

### Post by CatKiller on 2019-08-10
You could try putting
```
HorizSync 31-80
VertRefresh 56-75
```
in your xorg.conf.

---

### Post by raspberrypieman on 2019-08-10
[LEFT][COLOR=#000000][FONT=Ubuntubeta]@AutoDave, @him610 - Thanks - I did think the cable or the old OptiPlex might be a problem, but I now have a copy of [LEFT][COLOR=#555555][FONT="Roboto"]"Debian with Raspberry Pi Desktop"[/FONT][/COLOR][/LEFT] (the X86 version of the Rpi operating system) running in a separate partition on the OptiPlex 755 using the same cable and can get 1680 x 1050 resolution OK - I just cannot get it to work using the Ubuntu partition.[/FONT][/COLOR][/LEFT]

---

### Post by Autodave on 2019-08-10
From reading a bit on the 'net, supposedly you can allocate how much memory the graphics processor gets to use, by accessing that in the BIOS.  Have you looked there?  Perhaps upping the graphics memory you will be able to get the higher display sixe that you are looking for.

---

### Post by him610 on 2019-08-10
> X86 version of the Rpi operating system) running in a separate partition...can get 1680 x 1050 resolution

That's great!

How about booting to the Debian Rpi desktop and running *inxi -G* which should show which driver is being used.

---

