---
title: "GeForce GTX 560Ti on 13.04 giving extremely choppy rendering"
date: 2013-07-13
forum: Hardware
---

### Post by JAnthHamilton on 2013-07-13
Hello,

I have a 64-bit 13.04 machine that I dual-boot windows on. I have a GeForce GTX 560Ti card that has been bugging me on Linux for quite some time now.

When running basic games, even ones where a single image is moving around the screen there is notable choppy stuttering during rendering. I should note that these exact same games run great on Windows, and they also run great on my Lenovo IdeaPad (P580).

I am currently running the Nvidia 310.44 driver, but I have tried most of the available drivers for my card to no avail. Is there anything else I can do to troubleshoot this issue? I have tried messing around in nvidia-settings quite a bit to see if there are any changes, but haven't gotten any that seem any better.

Any help is IMMENSELY appreciated!

---

### Post by whatthefunk on 2013-07-13
You should be sure your system is actually using the driver.  Sometimes the driver is installed but not activated.  In a terminal, run
```
sudo lspci -k
```

Scroll down until you find the entry for your graphics card.  It should look something like this:
> 01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
        **Kernel driver in use: nvidia**

---

### Post by JAnthHamilton on 2013-07-13
When running that I see

```

01:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 560 Ti 448 Cores] (rev a1)
	Subsystem: eVga.com. Corp. Device 2078
	Kernel driver in use: nvidia

```

---

### Post by pqwoerituytrueiwoq on 2013-07-13
I have a 550 TI, if you are using unity/compiz the stock nouveau driver preforms better
try a different DE like [xfce]("apt:xubuntu-desktop") or purge the nvidia driver and use the stock driver
 [FONT=courier new]nvidia sudo apt-get purge nvidia* && sudo rm /etc/X11/xorg.conf && sudo reboot[/FONT]

---

### Post by JAnthHamilton on 2013-07-14
I am able to get it running just fine on lxde.

Is there any way to improve how graphics work in Unity?

---

### Post by pqwoerituytrueiwoq on 2013-07-14
as i said in unity the opensource nouveau driver preforms better than the nvidia one

---

