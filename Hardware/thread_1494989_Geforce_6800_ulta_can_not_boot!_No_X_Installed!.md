---
title: "Geforce 6800 ulta can not boot! No X Installed!"
date: 2010-05-27
forum: Hardware
---

### Post by dznn on 2010-05-27
Hi,

I downloaded the 10.04 minimal ISO today and burned it. Installing went fine and the problem occured when I first booted... I get this => [http://img413.imageshack.us/img413/7060/imag0036k.jpg]("http://img413.imageshack.us/img413/7060/imag0036k.jpg") 

I installed only the "openSSH server package" when I was asked to choose. I took the Geforce out and used my onboard GPU and all booted fine. I checked to make sure and X wasn't installed ( no "startx" command, it suggested me to download "initx"... ). 

This seemed very strange since there was no Xserver or nothing installed except openSSH and the other basic stuff ubuntu minimal iso installs. I then switched my Geforce 6800 back in and booted from a live ubuntu 8.04 cd. Here I got the same problem except the stripes on my screen were colorful and I got a working mouse pointer. 

I then rebooted the live cd in "Safe Mode" as it's called and now everything worked fine! I then tried to boot the minimal X-less install on my hdd again... same problem! I then switched back to the onboard gpu and installed the xserver and stuff ( no window managers gnome, kde,... nothing, just xserver ) hoping this would fix it but it didn't, same problem. 

I really don't know or understand what's going on and I hope someone here can help me. I want to be able to boot in the terminal using my Geforce 6800. The final goal is to have a terminal and xserver installed with geforce nvidia drivers. No windowmanager. 

I would like to state again: the problem seems to occur even without X installed! So nothing to do with xorg.conf and stuff... I think? ( Altough X is installed now, it just didn't fix the problem. )


I hope someone here knows what's going on.

---

### Post by dznn on 2010-05-28
Is this the wrong forum categorie or something? Or really noone has an idea?

---

