---
title: "Can't get the nvidia binary drivers working"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by N'Jal on 2006-11-29
Hi I am using dapper drake, basically i have an nvidia 6600 PCI-E card that i DID have the binary nvidia drivers working on, but i needed to reinstall dapper, and now i can't get them working.

It appears that the nvidia kernel module isn't being injected into the kernel, which is very curious, since it should be a simple matter of installing nvidia-glx and setting /etc/X11/xorg.conf to use nvidia driver, as it stands only vesa works not even nv. So i am really lost as to what to do.

If anyone can help, i would appreciate it.

---

### Post by gborzi on 2006-11-29
To check that the nvidia module is loaded, try > lsmod|grep nvidia that should show a line like this > nvidia               4717492  36 along with other lines. If it's not loaded try to load it explicitely with > sudo modprobe nvidia
Please give more details about your problem, e.g. posting your Xorg.0.log (under /var/log) can be very useful.

---

### Post by Joe_CoT on 2006-11-29
what error specifically are you getting from xorg? have you tried:

```
sudo modprobe nvidia
```
to see if it loads manually, and if not, what error is provided?

---

### Post by N'Jal on 2006-11-29
Nevermid, it seems after installing linux-headers for the newer kernel it has worked. Oh well.

---

