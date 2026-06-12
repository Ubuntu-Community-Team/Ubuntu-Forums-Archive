---
title: "nvidia drivers fail after the most recent kernel update"
date: 2009-02-06
forum: Hardware
---

### Post by fallen seraph on 2009-02-06
After the most recent kernel update my nvidia drivers just won't work. I'm having to boot into the older kernel versions of ubuntu to use my normal resolution and whatnot. Searching the forums has yielded no help, I seem to be the only one having this problem :\

Any help or anyone else suffering?

edit: it may also be of relevance that I've got an nvidia 7600 gt and am running hardy heron.

---

### Post by khelben1979 on 2009-02-06
```
sudo apt-get install nvidia
```
is the first thing you can try or you can try the drivers directly from the nVidia website.

First make a backup of the X config file:

```
cp /etc/X11/xorg.conf /etc/X11/xorg-backup.conf
```

then download the latest nVidia drivers from [here]("http://www.nvidia.com/object/linux_display_ia32_180.22.html"). If it fails you can always go back to your old config file by doing this:

```
mv /etc/X11/xorg.conf /etc/X11/xorg-bad.conf
mv /etc/X11/xorg-backup.conf /etc/X11/xorg.conf
```

(The driver which I have linked to needs a 32bit Linux system to work)

---

### Post by sedawk on 2009-02-06
I have a system with manually installed NVIDIA drivers where this
happens after every kernel update, because some kernel module
needs to be recompiled (or simply copied to another directory?).

So what I always do is this:

i) stopping X (e.g "sudo /etc/init.d/gdm stop")
ii) run (as root) the NVIDIA driver package to do the installation
    and recompilation of kernel modules.
    I tell the installer not to touch my xorg.conf
iii) start X with "sudo /etc/init.d/gdm start"

That should do the trick (if you downloaded the NVIDIA driver yourself).

---

