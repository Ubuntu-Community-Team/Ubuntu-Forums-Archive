---
title: "Touchscreen problem"
date: 2010-11-18
forum: Hardware
---

### Post by dim_par on 2010-11-18
Hello everyone,
I have a LG T1710B touchscreen but i cannot make the touch panel work. It is an ITM TouchPanel. The usb-devices has an entry for it
```

T:  Bus=04 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=16e3 ProdID=f9e9 Rev=01.00
S:  Manufacturer=ITM Inc
S:  Product=USB Touch Panel
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

```
But there is no entry for it in /proc/bus/input/devices.
Is there a way to make it work. After googling i found out tha this touch panel is recognized from the kernel in Ubuntu.
Thanks in advance

---

### Post by craigbrandt on 2011-03-14
Hi dim_par,

I had struggled with problem and found the solution. Credit to William for providing this:

Please note that updating the kernel can cause other compatibility issues. Do this on a test system first!!


The repo was found here : [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

First, in /etc/apt/sources.list add this line "deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main"

Make sure that you have saved the sources.list file with the addition above

Now open Synaptic ( System->Administration->Synaptic Package Manager )

On top left, click on "Reload" Icon, this will update your repository list for Synaptic to use

You need to update first, click on "Mark All Upgrades" Icon

Then Apply Icon, then in the new window, apply again

If you need to restart after the updates, do so ( normally the the button on the top right of the screen will go red if you need to restart )

Once restarted, open Synaptic ( System->Administration->Synaptic Package Manager )

Locate this package linux-image-generic-lts-backport-natty, Click on "Search" Icon, then paste this into it, then click Search

Mark the little box next to linux-image-generic-lts-backport-natty, either right click on the Line, or click on the box, then "Mark for Installation"

Then Apply Icon, then in the new window, apply again

after this has been installed, the button on the top right of the screen will go red, so you need to restart, if you have not connected the monitor, then shutdown instead, when shutdown, connect the monitor, and the usb cable

Once the PC has booted up, and you are at the login part, you should be able to use the touchscreen side

Now I need to ask out there. Is there someone that can help with the calibration settings for the monitor?

Thanks in advance,

Craig

---

