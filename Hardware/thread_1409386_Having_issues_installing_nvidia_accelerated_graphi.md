---
title: "Having issues installing nvidia accelerated graphics driver"
date: 2010-02-17
forum: Hardware
---

### Post by untalented893 on 2010-02-17
Hey guys.
I'm having some issues installing the nvidia accelerated graphics driver (version 173). When I go into the hardware drivers and attempt to enable it it looks like it is working just fine but then it stops at about 25%. I let it run all night to make sure that it wasn't just running slow, but it made no progress. Does anyone know how to fix this or if there is a way to manually install the driver? My ubuntu skill is pretty basic, but I feel confident with terminal.

Thanks!

---

### Post by savantelite on 2010-02-24
same issue here under xubuntu

Terrably slow or no progress at all

512 MB nVidia GeForce GT210

---

### Post by dabl on 2010-02-24
Try it like this:

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

There are only a couple of difference for Ubuntu/Gnome:

use gdm, not kdm
use gedit, not kate
use gksu, not kdesudo

:)

---

### Post by zeronothing on 2010-02-24
try this guys, if your using a Nvidia card that is Geforce 6 and above. I do this with my Nvidia 7950GT card. Also this works if your using Ubuntu 9.10. Their is a Personal Package Archive Team that does deb packages for the latest Nvidia drivers. Go to this link [[COLOR="Blue"]here[/COLOR]]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") and look for the section "Adding this PPA to your system". right below this section you will noticed a string of text in bold lettering. Now highlight whatever is in bold and right click and hit copy. Next go to system -> administration -> software sources. when the window pops up click on the tab "other software." now click on the add button and paste what you copied and click add source. now you can close that window down and open up terminal and do this command "sudo apt-get update". this will update all of the packages on your system. Now go to system -> administration -> hardware drivers and see if you can install the latest 190 or 195 version driver. if you can, install version 195.

---

### Post by untalented893 on 2010-03-04
Thanks for the sugestions neither of them worked though... The really upsetting part of all of this is that I had ubuntu on this system before and had the same issue. I got the Nvidia driver working after a little bit of research, but I can't for the life of me seem to figure out what I did or where I looked online for the solution...

---

