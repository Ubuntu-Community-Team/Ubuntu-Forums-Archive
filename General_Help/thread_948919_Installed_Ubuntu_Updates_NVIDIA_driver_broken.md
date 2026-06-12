---
title: "Installed Ubuntu Updates NVIDIA driver broken"
date: 2008-10-15
forum: General Help
---

### Post by AmbientOcclusion on 2008-10-15
This is for Ubuntu Hardy 8.0.4

I wanted to post this thread to list the steps I took to fix my NVIDIA driver.

I have a recently clean install of Ubuntu, when the updates (Oct 15, 2008) were installed today and I did the mandatory reboot Ubuntu entered low graphics mode. Here are the steps I took.

Rebooted into Live CD.

Change directory to my xconf file.
```
cd /media/disk/etc/X11
```
```
gedit xorg.conf
```

Looked for the line that had Driver and changed "**nvidia**" to "**nv**" so that I could boot into gnome.

After booting into Gnome

**CTRL+ALT+F1**
```

sudo /etc/init.d/gdm stop
```
The driver is on my Desktop so...
```
cd Desktop
```
```
chmod a+x NVIDIA-Linux-x86_64-177.80-pkg2.run
```
Installed the NVIDIA driver again
```
sudo sh NVIDIA-Linux-x86_64-177.80-pkg2.run
```
I went thru the menus, clicking okay and yes on everything.
```
sudo /etc/init.d/gdm start
```

Now everything works fine again.

My question is why did I have to re-install the driver? Was it because of a kernel update?

Also, is this the most efficient way to do this, or could I have accomplished this in a different way?

Thanks and/or hope this helps someone. (recent Windows convert like myself especially)

---

### Post by AmbientOcclusion on 2008-10-15
This also just occured with Wine, any suggestions why?

Although I haven't re-installed the NVIDIA drivers yet I am curious as to why this is...

I upgraded Wine 1 to 1.1.6

---

### Post by Tofus on 2008-10-15
I got the updates as well, which included a new kernel and had the same problem.  The problem is because the kernel module that was compiled when you initially installed the nvidia driver is now out of date.  I resolved the problem in the manner you described above, since I needed the new 177.80 driver anyway. If you already had the driver, I think you can recompile and install the module by running:

64-bit:
```

sudo ./NVIDIA-Linux-x86_64-177.80-pkg2.run -K
```

32-bit:
```
sudo ./NVIDIA-Linux-x86-177.80-pkg1.run -K
```

Either way, the update requires a recompile of the kernel module, no matter which way you install it.

---

### Post by jerome1232 on 2008-10-15
Yeah if you use anything other than the restricted driver manager in Ubuntu, every kernel update and sometimes after xserver updates, You'll have to recompile the driver.

---

### Post by AmbientOcclusion on 2008-10-16
> **Tofus said:**
> I got the updates as well, which included a new kernel and had the same problem.  The problem is because the kernel module that was compiled when you initially installed the nvidia driver is now out of date.  I resolved the problem in the manner you described above, since I needed the new 177.80 driver anyway. If you already had the driver, I think you can recompile and install the module by running:

64-bit:
```

sudo ./NVIDIA-Linux-x86_64-177.80-pkg2.run -K
```

32-bit:
```
sudo ./NVIDIA-Linux-x86-177.80-pkg1.run -K
```

Either way, the update requires a recompile of the kernel module, no matter which way you install it.

Thanks Tofus and Jerome.
 That seems more efficient. When I did the re-install it did display a message that it detected the previous driver.

---

### Post by phun-ky on 2008-10-16
after the little insident I had today with the new kernel: [http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu](http://phun-ky.net/2008/10/fix-for-failed-to-load-the-nvidia-kernel-module-on-ubuntu) , I cant log onto woW with Wine, or any other game. I can  log in , choose character, but the loadscreen stalls at 100% and nothing happens.. anyone that's got similar problem? I suspect the nvidia driver..

How do I fix this? The latest nvidia driver is recompiled..


solved it. installed the latest wine. [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by AmbientOcclusion on 2008-10-28
Thanks for that. I have had problems with previous wine installs.

---

