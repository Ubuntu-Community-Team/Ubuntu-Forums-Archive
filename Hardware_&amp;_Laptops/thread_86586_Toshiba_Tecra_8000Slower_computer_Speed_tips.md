---
title: "Toshiba Tecra 8000/Slower computer Speed tips"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by Ribs on 2005-11-05
I recently got my old faithfull Tecra 8000 laptop working again (new battery and wireless network card). And I found Ubuntu to be pretty damned slow. I made a few changes to a default install, I figured they may help someone else, so here they are.

If you feel you can cope with xfce and Abiword instead of Gnome or KDE with OpenOffice.org, try out XUbuntu. At the time of writing, it's not a 'proper' project like Kubuntu is, but it's fairly stable right now. I suggest you do this from a clean 'server' install. You mearly have to enable the universe repos and apt-get update and apt-get install xubuntu-desktop. I also suggest you apt-get gdm. Xfce has some nice features, even for a light desktop, so at least consider using it, or try it out on an existing installation...

X seemed to pick the vesa driver for me?! Change the vesa line in your /etc/X11/xorg.conf file to 'neomagic'. The neomagic driver is the 'proper' driver to use, and will give a speed increase (tho not as much as I would have liked). If you can cope with 16-bit instead of 24-bit, use 16-bit. The tecra 8000 doesn't have much graphical memory, and using 16-bit will help things. You may find you're stuck with 640x480 resoultion after changing, which looks awfull, if this is the case, see here; [http://www.ubuntuforums.org/showthread.php?t=32651](http://www.ubuntuforums.org/showthread.php?t=32651)

Consider removing firefox and use Epiphany or another browser. Epiphany is a faster browser, but lacks features you may want on firefox.

Fix sound. See [http://www.ubuntuforums.org/showthread.php?t=32651](http://www.ubuntuforums.org/showthread.php?t=32651) to get sound working.

Disable powernowd. Powernowd is supposed to slow down the CPU when it's not being used heavily, therefore extending battery life. It doesn't work too well, and was my main motivation for writing this guide. powernowd complained about my CPU, but seems to totally screw things up. Runing cat /proc/cpuinfo showed up the following. Bear in mind the cpu was at 100% load, so powernowd should have push the speed up to the full 300mhz. But, as you can see, it's a lot less!

[FONT="Courier New"]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 5
model name      : Pentium II (Deschutes)
stepping        : 2
cpu MHz         : 77.842
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips        : 146.94[/FONT]

After removing powernowd from synaptic and rebooting (just stopping it didn't seem to help). I got the following:

[FONT="Courier New"]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 5
model name      : Pentium II (Deschutes)
stepping        : 2
cpu MHz         : 300.013
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
bogomips        : 593.92[/FONT]

Much better, and the machine felt a lot faster as well. I'd rather have a bearable machine with a less battery life!

I'd love to hear more tips for this machine, or even just older computers in general!

---

### Post by louman on 2006-02-19
Quite honestly, using the vesa driver makes performance *much* better. When I use the neomagic driver things are substantially slower, ironically when it comes to drawing windows, etc. I can also use full 24 bit colour with no ( compared to the neomagic...  ) real hitches. Perhaps somethings wrong with my videocard?

---

