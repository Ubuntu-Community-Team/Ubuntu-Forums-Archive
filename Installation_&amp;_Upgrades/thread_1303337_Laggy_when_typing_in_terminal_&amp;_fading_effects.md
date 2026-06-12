---
title: "Laggy when typing in terminal &amp; fading effects"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by novellterminator on 2009-10-28
I thought it was related to my video card, since Ubuntu 9.10 has a real issue with fading in/out on my machine, so I tried to install a driver for my video card (not listed in restricted drivers -- it's a NVidia GeForce 285gtx). I found a site that said a needed to apply a patch to the driver for it to work probably on Ubuntu 9.10... It said to type

```
./NVIDIA-Linux-x86_64-185.18.14-pkg2.run --apply-patch nvidia-185.18.14.patch
```

I shortened the file names so I wouldn't have to type so much -- to nvidia.run and nvidia.patch, respectively. I have no clue what "./" does, but when I "cd /home/derek-desktop/Downloads" and try to run it, it says the file cannot be found, let alone working with the above patch code.

Here's a screenshot; what am I doing wrong?

[IMG]http://derekcannon.com/filenotfound.PNG[/IMG]

Could there also be another reason why typing in the terminal and effects with fading could be laggy? I have extra visual effects on, and it doesn't lag at all with other effects such as minimize, maximize, and dragging around a wobbly window.

I am using 64-bit edition and I'm running it on Windows 7 through VirtualBox (with Guest OS additions installed).

Thanks,
Derek

---

### Post by kellemes on 2009-10-28
Working from a virtual machine means you cannot use your real videocard. The machine is virtual.
Maybe it helps if you increase the amount of videomemory.

---

### Post by novellterminator on 2009-10-28
I see, thanks. Well, is there any way I can get rid of this horrible lag while I type then? It actually lags outside of the terminal window too, for example, in the search field of Synaptic Package Manager.

---

