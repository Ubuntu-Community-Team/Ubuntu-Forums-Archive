---
title: "GTX1070, proprietary driver, dual screen and weird behaviors"
date: 2016-12-23
forum: Hardware
---

### Post by SilentSib on 2016-12-23
Good evening,

I have this new rig with two BenQ monitors (one connected to the Intel integrated graphics card via VGA, and the other connected to the GTX 1070 via HDMI). I'm using Unity but I'm having some weird problems with it and with the proprietary drivers (tested 375 and 367 since 367 works fine on my Ubuntu laptop).

So, here's what happens:

- When I select the **nvidia** card via prime, I can only have proper render on both screens if I clone them (having the same display on both monitors). If I choose anything else, I will have this:

[IMG]http://i.imgur.com/WwqNp9i.png[/IMG]

If you can't see the problem here, let me explain: everything is much larger than it should on the desktop (apart from the icons on the left) AND the cursor's position is also incorrect (I need to put the cursor like 2 centimeters from what I'm trying to click if I want that to work. I do have both screens displaying something, though... Also, what's interesting here is that the nvidia settings only see one screen... even though both are turned on and actually display the same thing...

- When I select the Intel card via prime, **only one screen displays something **; the other stays black

What I've tried:

- removing Unity and reinstalling it: no change
- uninstalling the nvidia driver (via remove --purge nvidia*) and reinstalling it via ppa: no change
- removing xorg and reinstalling it: no change

I've browsed many topics on nvidia, intel & ubuntu so far but haven't been able to find anything that could have helped me figuring this one out. I'll try pretty much anything.

Thanks!
SilentSib

---

### Post by Irvs on 2017-01-22
Same problem occuring here on a new laptop (Medion Erazer X6601) after a fresh install. I'm using a FHD laptop + FHD monitor attached to HDMI port (HDMI to DVI cable in beween).
I've tried different nvidia drivers, different kernels, to no avail. Afaik I also have an Intel chip +  Nvidia GTX 970m.

Using the nouveau driver my windows scale normally and the dual monitors work fine. The only thing there is that the mouse leaves a trail on the 2nd monitor, which is also annoying.

Note that in the screenshot of the previous post the bar at the top is rendered normally (same here).

---

### Post by oldfred on 2017-01-22
Did you install the newest nVidia driver using the ppa, not from nVidia?
       Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 

If Skylake or Kabylake, did you install newest Intel driver?
      
 Intel Driver updates
[https://ubuntuforums.org/showthread.php?t=2342137](https://ubuntuforums.org/showthread.php?t=2342137)
Updates often needed for Skylake or Kabylake
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

Another Intel thread.
[https://ubuntuforums.org/showthread.php?t=2328993](https://ubuntuforums.org/showthread.php?t=2328993)

---

