---
title: "How I installed the driver for my nVIDIA GeForce 8600 GTS"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by enfeiris on 2008-03-15
Hey all, new to the forums, and new to Ubuntu (I've only been using it for a few days).  I'm currently using 7.04.

My first major hurdle was installing the drivers for my nVIDIA GeForce 8600 GTS.  I found a solution that worked for me, and thought I'd share it in the clearest possible terms so that others in my situation may benefit.

First I downloaded the driver from nVIDIA: [http://www.nvidia.com/object/linux_display_ia32_169.12.html]("http://www.nvidia.com/object/linux_display_ia32_169.12.html")

Note that I downloaded this package to my desktop, and that if you don't, the commands at the bottom of this post won't work.

Then I went to System -> Administration -> Synaptic Package Manager and installed the following packages:

	libc6-dev (2.5-0ubuntu14) 
	linux-libc-dev (2.6.20-16.35)

Then I hit CTRL-ALT-F1 and typed in the following commands (in order):

	sudo /etc/init.d/gdm stop
	cd Desktop
	sudo sh NVIDIA-Linux-x86-169.12-pkg/.run

When the installer finished, I typed: 

	sudo /etc/init.d/gdm start

Hope this helps!:)

---

### Post by overdrank on 2008-03-15
> **enfeiris said:**
> Hey all, new to the forums, and new to Ubuntu (I've only been using it for a few days).  I'm currently using 7.04.

My first major hurdle was installing the drivers for my nVIDIA GeForce 8600 GTS.  I found a solution that worked for me, and thought I'd share it in the clearest possible terms so that others in my situation may benefit.

First I downloaded the driver from nVIDIA: [http://www.nvidia.com/object/linux_display_ia32_169.12.html]("http://www.nvidia.com/object/linux_display_ia32_169.12.html")

Note that I downloaded this package to my desktop, and that if you don't, the commands at the bottom of this post won't work.

Then I went to System -> Administration -> Synaptic Package Manager and installed the following packages:

	libc6-dev (2.5-0ubuntu14) 
	linux-libc-dev (2.6.20-16.35)

Then I hit CTRL-ALT-F1 and typed in the following commands (in order):

	sudo /etc/init.d/gdm stop
	cd Desktop
	sudo sh NVIDIA-Linux-x86-169.12-pkg/.run

When the installer finished, I typed: 

	sudo /etc/init.d/gdm start

Hope this helps!:)

HI and glad to hear you have it working, You can also try Envy 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Good luck!

---

### Post by amrasurion on 2008-06-04
what was the problem you were having prior to the install of the drivers? I'm still having a hard time, my monitor keeps going to sleep upon installation/reboot and the only way i can get it to work is by going back and changing to the NV drivers.. help D:

---

