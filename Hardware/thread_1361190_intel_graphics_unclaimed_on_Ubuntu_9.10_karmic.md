---
title: "intel graphics unclaimed on Ubuntu 9.10 karmic"
date: 2009-12-21
forum: Hardware
---

### Post by v1nsai on 2009-12-21
I've been reading about [the Intel driver disaster]("http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/") that went down in the jaunty age.  In my Karmic 64 bit install on my Dell Studio 1555, 'lshw -c display' still says that both my VGA and display drivers are unclaimed.  Performance is pretty good, but I still get lag on compiz window animations and VMware isn't able to use 3D acceleration because it doens't recognize my card (I'm hoping a driver will fix this).

I tried rolling back to the Intrepid xserver-xorg-video-intel driver, which apparently works for jaunty but it caused lockups on boot on Karmic.  I switched back but everything is still unclaimed.

I know there are threads out there about this, but everywhere I've read seems to indicate that everything was fixed in Karmic, but I'm still having problems.  Is there anything I can do besides wait for 10.04 and hope?

---

### Post by IcarusR on 2009-12-22
I'm running Intrepid on my Toshiba A100-305 with same graphics chip as you.
Running 'lshw -c display' gives me the same as you, yet my graphics work well enough for me.

Having said that I do not run any 'Visual Effects' & when I try to enable them I get an error 'Destop Effects Could Not Be Enabled'

---

