---
title: "Nvidia drivers gone bad"
date: 2009-02-27
forum: Hardware
---

### Post by joshaman on 2009-02-27
i installed the nvidia drivers through hardware drivers, driver 177.xx.  I then realized there were later nvidia drivers available.  So I then installed them.  i then realized the 177.xx drivers were still active "or so said hardware drivers" and so I deactivated them.  I then decided to reinstall the nvidia drivers (180.29) as i figured perhaps they had not fully overwritten the 177.xx drivers.  Now I can only use default drivers, and any attempt to enable the 177.xx drivers or reinstall the new ones goes wrong.  i get an error message and have to revert to low-graphics settings.  i have never used linux before - been using windows.

will someone help me out here?

---

### Post by nixscripter on 2009-02-27
If you want to go back to the 177.xx drivers, you can download the package file [here]("http://packages.ubuntu.com/intrepid/nvidia-glx-177") and replace it manually from the Terminal: ```
sudo dpkg -i nvidia-glx*deb
```

Hope this helps.

---

### Post by joshaman on 2009-02-27
I'll try that now.  However it didn't work when I reinstalled them using "Hardware Drivers."  At this point I can't even create a new configuration nor use the default one.  Something seems corrupted.  I can only use low-graphics mode.  I tried to save all the output logs as pdfs but I can't find them.

I ended up reinstalling, btw.

---

