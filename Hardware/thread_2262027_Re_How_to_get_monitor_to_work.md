---
title: "Re: How to get monitor to work"
date: 2015-01-22
forum: Hardware
---

### Post by devdlp on 2015-01-22
I have a HCT monitor that i use with my laptop but its not working properly with my laptop Satellite Toshiba. I can only use the laptop with this monitor because my laptop screen is broken. When i use the monitor i cant see the mouse cursor and the monitor sceen reacts slowly, how can i fix this so i can use my laptop with the monitor please..

and it doesnt open apps on the monitor it'll open them on the laptop but wint show up on the monitor as opened

and it doesnt open apps on the monitor itll open them on  the laptop but wint show up on the monitor as opened so idk if that helps at all but could i have some help with this please

---

### Post by oldos2er on 2015-01-22
Moved to Hardware.

---

### Post by devdlp on 2015-01-23
i still need help with this

---

### Post by magpie03 on 2015-01-23
Hello devdlp.
I'll try to help as I am using an external monitor on a Toshiba with a broken screen. My Toshiba is a Satellite C655 running Ubuntu 14.04 LTS. What model Toshiba is yours, what version of Ubuntu are you using, and what video driver? Try going to system settings then open Displays. It should show two displays. Right click on the Built-in Display and make sure it is off. See my pics here. First pic is the external HP display which is showing "on". Second pic is the Built-in Display which is off. See if that hepls.
magpie03
[ATTACH=CONFIG]259434[/ATTACH][ATTACH=CONFIG]259435[/ATTACH]

---

### Post by devdlp on 2015-01-23
It started running more smoothly but still applications wont open on the monitor but they do on the laptop, i need them to open on the monitor. Im using Ubuntu 14.04 and its a Toshiba L455.
VGA compatible controller: Intel Corpration Mobile 4 series Grafic Controller (rev 07), also use Nvidia driver but cant figure out what version i think its GeForce 6400

---

### Post by magpie03 on 2015-01-24
If your fimillar with the terminal, the following commands will give you more information about your video card:
lspci | grep VGA
sudo lshw -C video
Some laptops have a function key to turn off the built in display. See if any info here helps:
[http://ubuntuforums.org/showthread.php?t=1581178](http://ubuntuforums.org/showthread.php?t=1581178)

magpie

---

### Post by devdlp on 2015-01-24
deven@deven-Satellite-L455:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
deven@deven-Satellite-L455:~$ sudo lshw -C video
[sudo] password for deven: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f2400000-f27fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2100000-f21fffff
deven@deven-Satellite-L455:~$

---

### Post by magpie03 on 2015-01-25
I am not an expert, but it looks like there is no video driver for your external monitor. You may have to totally remove all video drivers and reinstall them. But first, open the dash and search for Additional Drivers. If any are available, install them and see what happends.

magpie

---

### Post by devdlp on 2015-01-25
Gotcha ill respond with an update

It shows not additional driver available

I wish the problem I went to system settings>Displays and tunrt off the built in display. Problem solved.:KS;)

---

