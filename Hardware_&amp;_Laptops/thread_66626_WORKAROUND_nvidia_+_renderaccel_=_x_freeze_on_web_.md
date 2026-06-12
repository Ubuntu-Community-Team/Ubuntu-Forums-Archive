---
title: "WORKAROUND: nvidia + renderaccel = x freeze on web browsng"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by woahdae on 2005-09-17
I am so happy that I finally have renderaccel working without the freezing problem, that I thought I would post how I got it working. If you don't know what I'm talking about, google "nvidia renderaccel freeze" and click on just about any link- many, many people have been affected by this bug for about a year, and for those of us who want translucency to work, it is the bug that puts you against the wall.

Note that I have a gforce4-MX440. I tried renderaccel on someone's computer with a newer card and it worked, although I know the problem is not older-card specific.
_________________________________________________________

gist: match the right kernel to the last nvidia driver version with working renderaccel support. I found that the kernel that comes default with kubuntu 5.0.4 (2.6.10) matched with the nvidia driver 1.0-6629 works.
__________________________________________________________

For those of you that want a little more direction, here is a bit more info. If you don't understand something, google a little (for example, if you don't know where to get the kernel headers).

-make sure you are using the default kernel, as the nvidia 1.0-6629 drivers failed to build the nvidia kernel module using 2.6.11 from the universe repositories.

-make sure you have the kernel headers installed (you can find them in synaptic).

-go to [http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html](http://www.nvidia.com/object/linux_display_ia32_1.0-6629.html) to get the 1.0-6629 drivers

-stop x and drop to console (i like ctl+alt+backspace)

- do "sudo sh NVIDIA-Linux-x86-1.0-6629-pkg1.run" from where you downloaded the drivers to

-edit /etc/X11/xorg.conf, replacing "nv" with "nvidia" in the "Device" section, and add the lines:
      Option     "RenderAccel" "true"
      Option     "AllowGLXWithComposite" "true"
to the Device section as well. 

now try it. start x ("startx") and see if it still freezes. If your luck is as good as mine, it won't. Now, I could tell you how to get translucency working, but it's easy and well documented. The important part is having RenderAccel working.

IMPORTANT: there is still one more thing to do. if you have everything working to this point, when you restart your computer X will complain of having no usable screens (and won't work).

-I'm not sure this is necessary, but the first thing I did was remove all nvidia and nvidia-related packages and "restricted" kernel modules from apt (using synaptic with a search on "nvidia" is easiest). this didn't fix the rebooting problem in itself, but it's still something I did.

- Turns out you have to put the nvidia module in /etc/modules (i expected the installer to do this for me...). run:
sudo grep -q ^nvidia /etc/modules || echo nvidia >> /etc/modules

I also typed "modprobe nvidia," which honestly I don't know what it does, but it didn't report anything. may not be necessary, but it is something I did.

_______________________________________________________

And there you have it- all this worked for me, and now I am enjoying the composition manager effects built in to kde 3.4, which are pretty cool and well worth the effort. I hope this helps someone.

My system specs: 
CPU- I just upgraded to an AMD athlon 64 3200+, but I'm still running 32 bit kubuntu. I had the same problem with my old motherboard/cpu combo, which had an amd athlon xp 2000+. I'm running an ECS motherboard with nForce3-250 currently. Also, as mentioned, an gForce4-MX440 (64mb) graphics card.

EDIT: you should probably uninstall all the nvidia drivers in synaptic before running the driver installer from nvidia. if it doesn't work in the order already mentioned, you might need to repeat installing the 1.0-6629 drivers. Or, maybe it's not that picky- it's just what woked for me.

---

