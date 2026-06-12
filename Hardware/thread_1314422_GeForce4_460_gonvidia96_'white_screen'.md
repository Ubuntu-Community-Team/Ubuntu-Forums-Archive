---
title: "GeForce4 460 go/nvidia96 'white screen'"
date: 2009-11-04
forum: Hardware
---

### Post by gub~gub on 2009-11-04
I am having problems with my geforce4 460 go card and the nvidia 96 driver- the "white screen". 

Except when the white screen happens, dark areas slowly get more and more pronounced, like the screen is 'melting', and some color start appearing. Its quite psychedelic. Ive seen it before years ago (y2k) when trying to configure the LCD screen while installing Mandrake. Back then they said you can mess up your display if you don't have your xserver properly configured, i don't know if that is still true today.

I have had the problem with 9.04 and now with 9.10. Except now with 9.10 there does not seem to be a 'video' repair section in the recovery mode, so I have no video, but can boot to command line.

So, the help I need is:

a) How can I disable the nvidia96 driver from the command line? I've tried sudo dpkg-reconfigure xserver-xorg and nothing happens (it pauses for a couple seconds while the HDD 'thinks' and returns to the command prompt). I've also had no luck with nvidia-xconfig.

b) How do I properly configure my xorg.conf so I can have video acceleration (i miss google earth)

I have a toshiba satellite 5505-S505 with a geforce4 460 go card

Thanks!

---

### Post by aakozlov on 2010-03-04
i have exactly same problem with toshiba 5205-s704  with nvidia geforce4 460 go

i manually edited xorg.conf 
where replaced "nvidia" on "vesa"
this helped me to run X. now continuing to dig it )

---

### Post by cascade9 on 2010-03-04
> **gub~gub said:**
> 
a) How can I disable the nvidia96 driver from the command line? I've tried sudo dpkg-reconfigure xserver-xorg and nothing happens (it pauses for a couple seconds while the HDD 'thinks' and returns to the command prompt). I've also had no luck with nvidia-xconfig.



I think that you use the command "nvidia-installer --uninstall"

---

### Post by stereosphere on 2011-04-27
That's exactly what happens to me too! I've seen a lot of people telling about similar problems with toshiba&geforce 4 machines, but nobody seems to have found a solution.. I'm writing from a satellite 1410-801 with a geforce 420 go. 
I begin to suspect that there's a problem with the driver itself, rather than with the configuration.. Is that possible?

---

### Post by stereosphere on 2011-04-27
Sorry, I've just noticed how old this thread is..

---

### Post by bewilkinson on 2011-12-10
You need to add the following option to the Device section of xorg.conf:

Option "UseDisplayDevice" "DFP"

---

