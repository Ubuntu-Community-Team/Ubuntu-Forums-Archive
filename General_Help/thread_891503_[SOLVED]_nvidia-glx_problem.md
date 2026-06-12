---
title: "[SOLVED] nvidia-glx problem"
date: 2008-08-16
forum: General Help
---

### Post by pxhai on 2008-08-16
Hello,
I have a 5-year-old computer with an agp geforce4 mx460. Ubuntu Hardy kept reminding me of installing restricted driver, and I installed nvidia-glx, along with nvidia-settings. After reboot the first time, ubuntu cant detect the right resolution for my monitor, and ran at 800x600. I used Nvidia X server Configuration to change it (and save to /etc/X11/xorg.conf). And very strange thing happened: After the second reboot, the resolution it's okay, but the windows have no border and title bar! What happend? On my laptop with Intel chipset, everything works just fine.

---

### Post by Elfy on 2008-08-16
Do Alt+F2 and runb this command should get your borders back for you, 

```
sudo nvidia-xconfig --add-argb-glx-visuals == Option "AddARGBGLXVisuals" "true"
```

Works for my mx440

---

### Post by pxhai on 2008-08-16
Thanks for your great help, forestpixie.
Now graphics effects on ubuntu are awesome.

And the correct command is:

sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by Elfy on 2008-08-16
Never used that, the other one I've used is 

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Can you mark thread solved please

PS I'm adding a [SIZE="1"]small[/SIZE] warning when I know it might help, if nvidia haven't dealt with the driver for older cards before intrepid is released, I wouldn't upgrade as it doesn't work as yet with the new Xorg.

---

