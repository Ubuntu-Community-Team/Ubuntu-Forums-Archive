---
title: "Display Stopped Working"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by Hig on 2005-09-13
I keep my laptop uptodate, so it's probably something that was updated today, but when i tried to boot into Ubuntu, the display manager won't start. 

I've tried booting into recovery mode but the same thing happens. The Nvidia logo comes up but the drops back into the booting menu.

Any help would be appreciated.

EDIT: I've got knoppix working, so I can post any logs or anything requested.

---

### Post by evilghost on 2005-09-13
You just need to reinstall the NVIDIA driver, same thing happened on my end.  Just re-run the .run NVIDIA package, assuming that you installed the drivers using the official NVIDIA package.

The xlib update caused version differences I think with the NVIDIA driver compiled against them.

---

### Post by Hig on 2005-09-14
I did, but the same thing happened again.

Edit: And again.

I've switched my xorg.conf to vesa. I need some help here.

---

### Post by evilghost on 2005-09-14
Give me the output of:

```

dpkg -l | grep -i nvidia

```

Also, what's your /var/log/Xorg.0.log say the problem is?  What's your /etc/X11/xorg.conf look like?

---

### Post by Hig on 2005-09-15
```
david@laptop:~$ dpkg -l | grep -i nvidia
ii  nvidia-glx     1.0.7174-0ubun NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel- 1.0.7174+1     NVIDIA binary kernel module common files
ii  nvidia-setting 1.0-3ubuntu2   Tool of configuring the NVIDIA graphics driv

```

---

### Post by evilghost on 2005-09-15
I'd remove 7174 and install 7676 from the offical Nvidia package.

---

### Post by Franko30 on 2005-09-16
Hi,

had the same problem after the update (some Xorg files have been updated if I remember correctly).

I found out that this happened because I edited my xorg.conf file without making it 'updateable' aftwerwards as explained at the very beginning of said xorg.conf file.

So here's what I did:

First I ran the dpkg-reconfigure xserver-xorg as given in the xorg.conf file.

After that I changed my graphics driver to vesa.

Now, having a low resolution desktop, I reinstalled the graphics drivers and workarounds (in my case the i810 driver and the 915 resolution patch) and then re-used my old xorg.conf file.

Everything is back to 'normal'.

---

