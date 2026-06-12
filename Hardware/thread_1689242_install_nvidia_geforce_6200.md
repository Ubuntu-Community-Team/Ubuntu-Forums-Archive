---
title: "install nvidia geforce 6200"
date: 2011-02-16
forum: Hardware
---

### Post by barkerson on 2011-02-16
hi I'm having a problem with my graphics card it's an nvidia card and i have not had any problems with nvidia yet, but when i tried to change to a watercooled ati raedon my computer kept restarting(i guess it went to hot because the fan was broken on the nvidia card I had right before the ati).
now I don't know what to do, when i start nvidia x server settings it says like this: You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

i tried to run the "nvidia-xconfig" in the terminal but it looked like this:
```
 Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  At least one Device section is required.


ERROR: Unable to write to directory '/etc/X11'.
```what am i supposed to do?

---

### Post by cascade9 on 2011-02-17
sudo apt-get --purge remove nvidia-*

Then reboot. ;)

---

### Post by barkerson on 2011-02-17
oh, thanks alot! didn't expect it to be that easy!

---

### Post by cascade9 on 2011-02-17
Well, hopefully its that easy. It should be. 

Sometimes, you just have to know the right command ;)

---

