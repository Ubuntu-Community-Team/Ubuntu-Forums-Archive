---
title: "Replace proprietary nVidia driver with open-source nouveau?"
date: 2010-10-05
forum: Hardware
---

### Post by natasa on 2010-10-05
After a default install of Ubuntu 10.10-rc Maverick, how can I replace the proprietary nVidia driver (installed by default, version 260) with an open-source one, such as nouveau? Do you think nouveau can serve me well? Here are my requirements:
- absolute need: problem-free external monitor support (VGA port) at same resolution as the laptop's LCD panel (1440x900)
- just 2D needed, no 3D games
- optional: OpenGL for Google Earth
- optional: Compiz
My model is nVidia GeForce 6100 Mobile on an Acer AMD64 laptop.

---

### Post by P4man on 2010-10-06
Does 10.10 automatically install the proprietary nvidia driver? That would surprise me very much. Just go in to system > administration > hardware drivers. If it does indeed say its using the proprietary nvidia driver, then just disable it, thats all.

---

### Post by coffeecat on 2010-10-06
> **natasa said:**
> how can I replace the proprietary nVidia driver (installed by default, version 260) with an open-source one, such as nouveau?

It is the nouveau driver that is installed by default, not the nvidia one. If you have installed the nvidia driver through System > Administration > Additional Drivers, just use Additional Drivers to disable it as p4man says. If you do that you will have the nouveau driver.

At the moment, with a default install the nouveau driver does not support acceleration needed for compiz and google earth. You can enable this simply by installing the package libgl1-mesa-dri-experimental. It is an experimental package but I believe people are getting good results with it.

---

### Post by natasa on 2010-10-07
yeah you're correct, nouveau is the default one. I uninstalled the proprietary nvidia driver but now when Ubuntu boots I only see graphical garbage and the computer is locked up. The only thing I can do is to shut off the power. What should I do to get a working system again?

---

### Post by P4man on 2010-10-07
Try booting in recovery mode and lets purge the nvidia driver:

```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings

```

Then force a reinstall of nouveau:

```

sudo apt-get install --reinstall xserver-xorg-video-nouveau 
```

Shouldnt be necessary, but I guess its in beta for a reason.

---

### Post by coffeecat on 2010-10-07
If your computer is locking up, you will need to boot into the recovery console to do the commands P4man suggests. The recovery option is the second in the grub menu. Choose 'drop to root shell' when prompted with some options. You won't need the sudo command because you will have root powers, so try P4man's commands but without the sudo.

Another thing you might need to do is to remove the xorg.conf that the nvidia settings manager created when you installed the nvidia driver. It will be confusing the system because it tries to load the nvidia driver. At the root prompt, type:

```
ls /etc/X11
```If no xorg.conf is listed you need do nothing further. If there is one, do:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```Make sure you get X11 correct - that's capital-X-eleven.

Now...

```
reboot
```... from the recovery console and the system should boot with the nouveau driver

---

### Post by natasa on 2010-10-07
hey thanks for the help, I tried all commands but it still doesn't work :( still seeing graphical garbage on the screen... any other ideas?

What's the best way to switch back to the nvidia proprietary driver from the revovery console?

---

### Post by natasa on 2010-10-14
well I put on the nvidia proprietary driver back, as nouveau doesn't seem to work on my system...

but I still want to replace it with something more stable, because the nvidia driver locks up every few hours leaving my screen corrupted, forcing me to reboot.

What other options do I have?

---

