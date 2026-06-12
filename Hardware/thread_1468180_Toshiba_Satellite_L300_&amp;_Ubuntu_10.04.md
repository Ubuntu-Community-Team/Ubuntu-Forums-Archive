---
title: "Toshiba Satellite L300 &amp; Ubuntu 10.04"
date: 2010-05-01
forum: Hardware
---

### Post by Benyt on 2010-05-01
I have **[COLOR="red"]Toshiba Satellite L300[/COLOR]** with **[COLOR="red"]H2O Bios[/COLOR]**, and i have dual boot **Windows 7** and **Ubuntu 10.04**. In Windows 7 everything works SUPER !! in **Ubuntu 10.04** i have a problem with my **FN keys**, **not all of them**, **only Fn+F3 works** and after i press Fn+F3 i can use other Fn keys like Fn+F6 or Fn+F7 for Dispay brightness **they start to work** :confused: but after i restart my laptop again only Fn+F3 works :confused: . I also think that my **[COLOR="red"]CPU is sometimes hot[/COLOR]** :confused: . Please tell me, **i like to use only Ubuntu** on my laptop !! Thanks :confused:

---

### Post by ashima on 2010-05-04
Yes your computer is getting hot, very hot!
Seems to be the same problem with all newer Toshiba's.
I have Toshiba Satellite L500, H20 bios.
10.04 64bit. Ubuntu

Same problem exits with Fedora and PCLinuxOS

NO FAN CONTROL

Here is what works for me.
This does not solve the problem with the function keys but more importantly, gets the fan working properly and prevents a laptop meltdown.

first. sudo apt-get install sensors-applet
next. sudo sensors-detect

next. answer yes to everything.

exit then restart computer.

next. sudo gedit /etc/default/grub and then change

GRUB_CMLINE_LINUX_DEFAULT="quiet splash"

to read

..."quiet splash acpi_osi=Linux"

next. sudo update-grub to update /boot/grub/grub.cfg

exit then restart computer.

I hope this helps.

---

### Post by grnorris on 2010-09-07
Thanks for this.  I too am trying to get my FN keys to work correctly but, I hadn't really noticed just how bad my CPU was overheating (I rarely have my laptop directly on my lap).  Thanks to this post I successfully Fixed my fan and it is running much cooler now.  Also something that helped was [http://stochasticflux.com/blog/?p=13](http://stochasticflux.com/blog/?p=13)  be warned though that the formatting gets screwed up in the script, you need to change the quotes from single to double and I'm not quite sure if it's necessary or not but, I also deleted the preceding tabs.  The K10 sensor was necessary to my knowledge to get the sensors working.  (The sensors-detect command told me that unless it was already in my kernel I needed to install this driver.)

FYI My computer is a Toshiba Satellite L355D-S7901

---

### Post by rocdoc on 2011-01-30
Sorry to bump up an old post but I have the solution. You need to upgrade the BIOS to get fan control and function keys to work properly in Linux. See my complete article here:
[https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L300)

---

