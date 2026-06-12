---
title: "Fast Writes and SBA Enabling on Nvidia GPU's"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by justin420 on 2007-05-28
Hope this may help people; I was searching around for how to enable Fast Writes and Sideband Addressing for my BFG Nvidia GeForce 6800 GS OC GPU on linux, as my PC's BIOS has no settings for enabling Fast Writes and Sideband Addressing for my GPU.  It took me awhile to find how to accomplish this.  This is how I did it; which MAY not be the correct way.  USE AT YOUR OWN RISK.  I am using ubuntu edgy with the nvidia-glx package from
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable .  Its driver version 1.0-9746; its newer than whats in the regular repo; but its still not the latest driver ( which would be 9755 ) at the current date ( 5/28/07 ) .  After doing a little bit of xorg.conf tweaking ( for those of you who dont know where that is located its in /etc/X11 folder; and its supposed to be called xorg.conf ) I added 2 simple lines to a file called nvidia-kernel-nkc ( the reason its labeled nvidia-kernel-nkc.txt is because i couldnt upload just a non-extension file or a .conf file for that matter ).   The two lines I added were :

options nvidia NVreg_EnableAGPFW=1 
options nvidia NVreg_EnableAGPSBA=1

I also have the svn beryl version working with multimonitor mode; one is a 20'in Widescreen LCD and the other is a SVIDEO 25'in TV.  I hope someone will get some use out of this as I have.  If someone knows a better way I can accomplish this ( maybe even for Debian ETCH ) I would be more than happy to listen. ( that includes the beryl svn version and a multimonitor mode setup WITH beryl )

P.S. Sorry if I posted this to the wrong forum; I seen Hardware and I thought it should go here.

---

