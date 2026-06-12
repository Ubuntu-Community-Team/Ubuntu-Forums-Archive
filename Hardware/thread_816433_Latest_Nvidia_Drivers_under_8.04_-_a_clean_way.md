---
title: "Latest Nvidia Drivers under 8.04 - a clean way?"
date: 2008-06-02
forum: Hardware
---

### Post by Thyrus on 2008-06-02
Hello I have a new Lifebook (E8410) and the nvidia-glx-new drivers do not allow me to adjust the brightness of the Display which is a battery killer. Is there any **clean** way of installing the latest drivers by repalcing the nvidia-glx-new and crafting a new package out of the 

NVIDIA-Linux-x86_64-173.14.05-pkg2.run

file I can get from the official website? (Anything using fakeroot to watch the installer and similar tricks?)

If I get a clean solution i might be able to host the new packages.

---

### Post by Nepherte on 2008-06-02
You can install the latest driver you downloaded from the nvidia website as follows:

You'll probably need the kernel headers for installing the nvidia driver. we'll just install everything required for compiling at once since it won't hurt a fly:
```
sudo apt-get install build-essential
```

Stop gdm:
```
sudo /etc/init.d/gdm stop
```

Navigate to the directory where you downloaded the driver with the cd command:
```
cd directory
```

Make the file executable:
```
chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
```

Run the installer:
```
sudo sh NVIDIA-Linux-x86-169.12.pkg1.run
```

Restart gdm:
```
sudo /etc/init.d/gdm start
```

Now you should have the latest driver running. To check you can see the version somewhere in the nvidia-settings tool. When compiling the drivers yourself, as we did now, you also get a tool to update to the latest driver (for in the future):
```
sudo nvidia-installer -update
```

---

### Post by Thyrus on 2008-06-02
I know, that there is a way to install the driver but I'd like to keep the files that are not tracked by the dpkg to a minimum. Basically I'm aiming for a home grown update do nvidi-glx-new 

(I expect others to have similar problems)

---

### Post by opossumjack on 2008-06-02
Do these new drivers support GeForce 7300 GT and the newest kernels?
Because I've tried to install the old drivers (version 169.somethingelse) and when I try to start X server it crashed... 

Do you know if these drivers will work with my card and my kernel (2.6.24-17)?

Thanks in advance

---

### Post by Thyrus on 2008-06-02
The GeForce 7300 GT is already supported by the driver version 169.12 (the version that comes with 8.04) so I suspect that your problem is elsewhere.

---

### Post by hotweiss on 2008-06-03
> **opossumjack said:**
> Do these new drivers support GeForce 7300 GT and the newest kernels?
Because I've tried to install the old drivers (version 169.somethingelse) and when I try to start X server it crashed... 

Do you know if these drivers will work with my card and my kernel (2.6.24-17)?

Thanks in advance

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

I also found an interesting thread about the new drivers:
[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

Using the following command should speed up applications like Firefox:

> nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

---

