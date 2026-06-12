---
title: "Unable to login after enabling Nvidia restricted driver"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by AshleyArgile on 2007-06-07
Hi, 

After a smooth install of Ubuntu 7.04 I enabled the restricted hardware driver for my Nvidia Ge-Force 2 ultra video card and after it was downloaded I restarted. Now the system will not start! I get past the login screen but the desktop never appears. I just get a mouse pointer, which I can move around.

Any ideas? Is there a way to un-enable the restricted hardware driver?

Thanks in advance

Ashley

---

### Post by dmoney on 2007-06-07
Try installing the legacy driver since you're using an older card.

When you get the mouse pointer, hit Ctrl-Alt-F2. Should bring you to a command prompt. 
Log in and run:
```
sudo apt-get install nvidia-glx-legacy
```

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then run:
```
sudo dpkg-reconfigure xserver-xorg
```

and select nvidia as the first option and go with the defaults on the rest. 
Then run:

```
sudo /etc/init.d/gdm restart
```

And hopefully X should restart properly.

---

### Post by BatsotO on 2007-06-07
edit your /etc/X11/xorg.conf

find device section, chang NVIDIA to nv

---

### Post by AshleyArgile on 2007-06-11
Thanks for your help, but I ended up re-installing the operating system. It was a clean install anyway. Everything worked fine afterwards!

Thanks Again

Ashley.

---

