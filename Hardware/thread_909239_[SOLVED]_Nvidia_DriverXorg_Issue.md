---
title: "[SOLVED] Nvidia Driver/Xorg Issue"
date: 2008-09-03
forum: Hardware
---

### Post by FinalJenemba on 2008-09-03
Hi all, first off im using the latest version of Mint (Gnome), but I figured it wouldn't hurt to ask for help here since its based on ubuntu.

Ok on to my problem. Im running an 8800GTS 512 plugged into a LCD with a native res of 1920x1080. Its a good combination bit its always been a bit tricky to get them working well in linux. The restricted drivers in the ubuntu repos have never worked, the xorg always gets messed up after the install, so I didn't bother with those. I always have to get the newest driver from Nvidia's website and install it manually, that way I can have their installer write the new xorg file.

Iv done this a few times before, so I knew which headers I needed in order to compile the driver, etc, and the install went smooth. But here's the weird part, everything works perfect, compiz, videos, etc, as long as a don't restart the computer. I can log out and log back in, and restart X as many times as I want and all is well. But once I restart the PC it always looses the drivers and boots in the "low graphics mode", and the only way to fix it is to kill X and re-install the drivers. Then it will work fine until I restart the PC, then its "low graphics mode" again.

Anyone have any idea whats up?

PS. Iv installed the nvidia driver the same way in Hardy before and it worked fine, is there anything different about Mint that would be causing this?  Also I saw Envy was installed by default, so I made sure to go into it and uninstall any nvidia drivers that may have been there. It didn't help anything however.

---

### Post by Onyxblack on 2008-09-03
(go to comand prompt)

```
ctrl+alt + f3
```

(stop x server)

```
sudo /etc/init.d/gdm stop
```

(go to driver location)

```
cd <path to driver>
```

(install driver)
```

sudo sh NVIDIA-Linux<whatever>.run
```

(after installing the driver it should bring you back to the comand promp)
```

sudo /etc/init.d/gdm start
```

(this should bring you back to a WORKING desktop with drivers working, once there do)


```
sudo nano /etc/default/linux-restricted-modules-common

```
(edit the line to make it look like)

```
DISABLED_MODULES="nv nvidia_new"
```

Restart your comp - should all work after that

---

### Post by FinalJenemba on 2008-09-03
Thanks a bunch that took care of it!

---

