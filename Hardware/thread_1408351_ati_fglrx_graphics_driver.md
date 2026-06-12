---
title: "ati fglrx graphics driver"
date: 2010-02-16
forum: Hardware
---

### Post by maxrpowell on 2010-02-16
I am having problems with the ati fglrx proprietary driver on my dual install of windows and Ubuntu 9.10. After installing the driver through the hardware and driver utility it prompts you to restart the computer. When the computer boots up in Ubuntu I see nothing but a black screen and the ' CHECK CONNECTION CABLE ' sign the monitor bounces around when it is unplugged. I am sure the driver is the problem, because every time I install it the screen goes blank. Any suggestions?

---

### Post by paulbarratt on 2010-02-16
Things to try: 

- sounds dumb, but are you sure it is the correct driver for your model of graphics card?

- if it is, possibly the refresh rate or resolution are set wrongly for your monitor. Fortunately you can check this by booting into Windows. You could also try switching it into a lower resolution screen mode to see if it handles this correctly.

- does it all work fine with the open-source driver?

If you press Ctrl+Alt+F1 you should switch into a text mode login prompt, even if X is having problems displaying.  

Find /var/log/Xorg.0.log and post up the contents here.  This should contain any error messages which might give a clue to the problem.

---

