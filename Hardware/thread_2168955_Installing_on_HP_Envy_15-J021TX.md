---
title: "Installing on HP Envy 15-J021TX"
date: 2013-08-20
forum: Hardware
---

### Post by German_Castro on 2013-08-20
Hi,

Has anyone information about compatibility or help to install Ubuntu in a laptop HP Envy 15-J021TX ([http://www8.hp.com/au/en/products/laptops/product-detail.html?oid=5390974#!tab=specs](http://www8.hp.com/au/en/products/laptops/product-detail.html?oid=5390974#!tab=specs))?

I'm trying to install Ubuntu 13.04 64bit from a USB stick. The USB is able to boot grub but after select the install option at the moment of initialize the graphics it only shows a brief flash of the Ubuntu logo before go to black.

Any idea?

---

### Post by Cheesemill on 2013-08-20
You might need to boot with the nomodeset option...

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by German_Castro on 2013-08-27
Thanks, that helped me to boot the installation, but I'm still having some problems.

After run the installation and boot for first time I wasn't able to start the xorg because problems with the NVidia Driver. So I installed the drivers provided by NVIDIA and removed the Nouveau driver provided by Ubuntu, so far so good. But after reboot I only get a screen 640x480 with and the empty default wallpaper (without any toolbar)

After look for a while in xorg logs, it seems to be using drivers for Intel video card instead nvidia driver. My laptop has the following 2 devices (from windows device manager):  Intel(R) HD Graphics 4600, NVIDIA GeForce GT 740M

Is any way to force the driver/graphic card to use? The Nvidia installation created a xorg config file specifying the driver and I added manually resolution of 1366x768 but xorg seems to be ignoring this and it still uses Intel driver with resolution 640x480.

Any recommendation?

Thanks

---

### Post by Mark Phelps on 2013-08-27
You appear to have Nvidia Optimus Graphics -- which presents a serious problem in Linux:  [http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/]("http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/")

---

### Post by gusdefrog on 2013-12-01
I searched for hours, messed with drivers, and finally found someone who posted that "the stupid screen" was turned off every time they booted, and they had to increase the brightness to turn it on. I tried it, and that turned out to be my problem. :x

---

### Post by jj.wauters on 2013-12-25
I also have a HP Envy 15 with the same graphic cards.
It is clear that Ubuntu has a problem with hybride systems with 2 graphic devices.:(
At this time, Windows 8.1, Ubuntu 12.04 and Ubuntu 13.10 are running after having done a dozen of (re-)installations and experimenting with Nvidia drivers.
Ubuntu 13.10 tells me my graphics = "Intel Haswell Mobile" and that there are no "additional drivers available"
Ubuntu 12.04 tells me my graphics = "unknown" and that I have to install "NVIDIA binary Xorg Driver kernel module"
Now :
[LIST]
[*] Both in 13.10 and 12.04 I DO NOT LOAD ANY NVIDIA DRIVER. (That way I can not make use of Nvidias extended graphical capabilities, but at least I have a stable GUI.)
[/LIST]

[LIST]
[*] I fixed the screen brightness as explained in :  [http://http://askubuntu.com/questions/79983/screen-brightness-reset-to-minimum-after-every-reboot](http://http://askubuntu.com/questions/79983/screen-brightness-reset-to-minimum-after-every-reboot) (Use scale 0-100)
[/LIST]

[LIST]
[*] I installed TLP (power saving)
[/LIST]
Rather than lose any more time experimenting with Nvidia drivers or patches, I wait the announced 14.04LTS release in april 2014.
Finger cross, Cannonical fix those problems!!!

---

