---
title: "[SOLVED] Nvidia and 8.10 can't enable desktop effects"
date: 2008-10-31
forum: Hardware
---

### Post by Jackie999 on 2008-10-31
I was able to turn on 'extra' desktop effects 8.04 with my nvidia card. Now I'm on 8.10 and it's set to none and can't be enabled.

I get this :
```
jackie@ubuntu:~$ glxinfo
NVIDIA OpenGL Driver requires CPUs with SSE to run.

The current CPU does not support SSE.

```Does this mean my computer is just too old? I'm assuming if I reinstall 8.04 it will work again? No hope for 8.10 ?

---

### Post by overdrank on 2008-10-31
> **Jackie999 said:**
> I was able to turn on 'extra' desktop effects 8.04 with my nvidia card. Now I'm on 8.10 and it's set to none and can't be enabled.

I get this :
```
jackie@ubuntu:~$ glxinfo
NVIDIA OpenGL Driver requires CPUs with SSE to run.

The current CPU does not support SSE.

```Does this mean my computer is just too old? I'm assuming if I reinstall 8.04 it will work again? No hope for 8.10 ?

Hi and the support for some older nvidia graphics has some issues. What is the model of the graphics card? Have you tried to install the drivers?

---

### Post by Jackie999 on 2008-11-01
My card is pretty old, a GeForce FX 5500.
I've been looking in the Nvidia forums and see some drivers and patches that may help. But there are loads of them and I'm not sure which combination I need. It also appears I have to edit xorg (?) so this may take me awhile to figure it all out. Plus I have enabled the "NVIDIA accelerated graphics driver (version 173)" in Hardware drivers, so I suppose I have to reverse that somehow to install my own.
A little daunting for a newbie :confused:

---

### Post by rich257 on 2008-11-02
The easiest way is probably to use the [EnvyNG]("http://albertomilone.com/nvidia_scripts1.html") tool.  There is a beta version of the nVidia version 96 and 71 drivers that will work with the new X.Org on 8.10.  I'm sure one of these two will work for your card and don't require SSE either.

If you look at [this blog]("http://albertomilone.com/wordpress/?m=200810") you will see that EnvyNG will soon provide these new drivers, once they have been tested.

So, the easiest way would be to keep an eye on the blog and use EnvyNG when the new drivers are available.  EnvyNG takes care of removing the old driver that you have.

I have the same problem --- I can't upgrade to 8.10 at the moment as I won't have a 3D accelerated nVidia driver.

---

### Post by Jackie999 on 2008-11-12
Since envy isn't available for 8.10, I tried ticking the "pre released updates (intrepid proposed)" in the software sources - and it grabbed some new files on update ```
nvidia-173-kernel-source (173.14.12-1-0ubuntu4) to 173.14.12-1-0ubuntu5
nvidia-173-modaliases (173.14.12-1-0ubuntu4) to 173.14.12-1-0ubuntu5
nvidia-177-modaliases (177.80-0ubuntu2) to 177.80-0ubuntu3
nvidia-glx-173 (173.14.12-1-0ubuntu4) to 173.14.12-1-0ubuntu5
```I rebooted and still couldn't enable desktop effects.
So disabled the proprietory driver in Admin->hardware drivers, rebooted and tried to enable again. It told me it needed to install the drivers to enable desktop effects, I said okay, then it said I needed to reboot and then enable the effects. Did that and still get the message can't enable desktop effects. Not to sure if I did something wrong - or if the nvidia 173 driver isn't working?

---

### Post by Jackie999 on 2008-11-15
I was able to get my nvidia GeForce FX 5500 running under 8.10 with the 96.43.09 driver. At first I had some text rendering problems, but after posting in the [bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107") report I was told how to fix that (simple change in the xorg.conf)
Thanks to all that helped and are still working on it :)

---

### Post by Gaming4JC on 2008-12-20
I have the same problem with my Nividia Geforce FX 5200, any luck on getting some new drivers working for this? Or better explaining the solution. :???:

---

### Post by wiildchild on 2008-12-20
me too

---

