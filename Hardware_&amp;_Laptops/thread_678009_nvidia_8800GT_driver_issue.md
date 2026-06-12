---
title: "nvidia 8800GT driver issue"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by trakie on 2008-01-25
ok so my driver works, sort of.

its not a huge problem but every time i restart i get "running in low graphics mode" and then the login screen, from there i do a ctrl-alt-F1 and i stop gdm (sudo /etc/init.d/gdm stop) then go to my desktop (where the driver is - 169.04 since .07 makes the fan go 100% and drives me crazy), then a sudo sh NVID (and press tab here so i dont know what the name is), it tells me the driver is already installed but i install it anyway and then after that sudo modprobe nvidia (which appears to do nothing, but i saw it somewhere and it became part of my routine for some reason), and then i type startx

this procedure works fine, as im running 1920x1200 right now with full compiz effects, however boot up takes a little longer than id like, as i have to compile a driver every time i restart.

is there any thing i can do to stop the low graphics mode coming up?

ive tried editing the xorg.conf to no avail, it still comes up with vesa not nvidia and in low graphics mode, im slightly confused since when i install the driver again it tells me its already there...

i should have bought a different card...

---

### Post by Biznarie on 2008-01-25
I've had this problem too with my 8800GT, I think it had to do with an update that kept downloading when i logged back on because the driver install made another package out of date. Have you noticed this? I just stopped updating that file and now everything runs perfect no need to reinstall anymore (UT2004, Urban Terror 4.1, Sauerbraten, STEAM (TF2), and Guild Wars.)

---

### Post by Limbic on 2008-01-25
I don't know how much I'll actually be able to help, but as a complete novice I was able to get my 8800GT drivers working through [Envy]("http://albertomilone.com/nvidia_scripts1.html") without having to even touch the command line myself.  It automatically deleted the old drivers I unsuccessfully tried to install myself, then installed the new ones and it's worked without a hitch since.

Again, not sure how helpful this will actually be, but it worked for me.  i saw in [another thread]("http://ubuntuforums.org/showthread.php?t=674993") that Envy will now install the newest Linux drivers (169.09).

---

### Post by trakie on 2008-01-26
thanks limbic! envy worked like a charm, which surprised me since i tried it out once before and it didnt work out for me, but no complaints now, it installed 169.09 and no troubles at bootup.

---

### Post by jrickard on 2008-01-30
Well, it doesn't work for me.

I just downloaded envy and ran it.  I removed the NVIDIA drivers using Envy and rebooted.  My system came up with the clunky nv driver to pretty good resolution.  I then reran ENVY to install the NVIDIA drivers.  It installed 169.09.

On reboot, same problem.  After running rc.local, the screen cycles about three times going black and coming back, as if it were trying to load GDM and failing.  Then, I get the Ubuntu is running in Low Graphics Mode.  If I click CONTINUE, it will boot, but in 800 x 600.

This first happened after an update a couple of weeks ago.  I   had assumed, seeing others with the problem, that it would be fixed shortly.  It apparently hasn't.

Nvidia 8800 Ultra with Intel Xeon 6650

Jack Rickard

---

### Post by patrickfromspain on 2008-01-30
the problem you are having is because of the restricted modules package for the kernel you are running. If you uninstall that one or disable the nvidia module, you'll be fine. Otherwise, you have to keep reinstalling the nvidia.com driver at every reboot.

---

