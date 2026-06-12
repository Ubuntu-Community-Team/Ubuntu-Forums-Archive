---
title: "Nvidia 6600 go driver issues"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by bnahill on 2007-01-25
I am having problems with my chembook (asus v71) and the graphics drivers. It has a geforce 6600 go in it and for some reason, the ubuntu package does not work. It worked in previous ubuntu versions, it worked when I had gentoo on this thing, but now it just doesn't. So I gave up on that and am using the drivers straight from nvidia. They work but some things are still choppy, I don't get the nvidia logo when x starts up(not that I miss it) and when I try to return to the terminal (ctrl+alt+f*), I just get a black screen. Looking at /var/log/Xorgsomething I find
```
(EE) NVIDIA(0): Failed to initialize the GLX module; please check in your X
(EE) NVIDIA(0):     log file that the GLX module has been loaded in your X
(EE) NVIDIA(0):     server, and that the module is the NVIDIA GLX module.  If
(EE) NVIDIA(0):     you continue to encounter problems, Please try
(EE) NVIDIA(0):     reinstalling the NVIDIA driver.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 6600 at PCI:1:0:0 (GPU-0)
```
Some OpenGL applications run just fine, like GL117 but X restarts when I try to run cedega and I notice a bit of chop in the annoying fades for gksudo. I'd report the nvidia-settings output on GLX but X restarts when I try to view it. I know I'm not being terribly descriptive; I'm just fishing around to see if anybody might have had a similar experience.
Also, It's pretty ridiculous that the forums have this: :guitar:

---

### Post by K.Mandla on 2007-01-26
What? You don't like the guitar man?!

If you are using the Nvidia drivers from the Nvidia site, are you using the 386 kernel (I'm assuming you're using Edgy)? It was my understanding that the generic, vanilla Ubuntu kernel did not include the nvidia-kernel module, and that installing the nvidia drivers dragged linux-386 along with it. So it might be a simple matter of getting the kernel with the nvidia module included.

Aside from that, is there any chance earlier versions or packaged versions of nvidia drivers are getting in the way? What I mean is (hopefully without sounding condescending), did you properly remove the old nvidia driver package when you realized it didn't work?

And welcome, by the way. Even if you don't like the guitar man. ;)

P.S.: Also check that you have the Load "glx" line in your xorg.conf file ... but you probably already checked that.

---

