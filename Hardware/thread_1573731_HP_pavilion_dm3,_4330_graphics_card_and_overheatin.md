---
title: "HP pavilion dm3, 4330 graphics card and overheating issues"
date: 2010-09-13
forum: Hardware
---

### Post by Heliix on 2010-09-13
notebooks from HP pavilion dm3 series were reported to have good power management, low working temperature and long battery life. 

I have new HP pavilion dm3-1120ec with the newest ubuntu jaunty freshly installed, and it is seriously overheating, that means about 70 degC just after installation, with openbox as a window manager and all possible services switched off! I purchased it with windows 7 and it didn't have such problems, so it must be a problem of ubuntu, I guess.

the issue was already reported at 
[http://www.linlap.com/wiki/hp+pavilion+dm3z](http://www.linlap.com/wiki/hp+pavilion+dm3z) 
(down at the page), and it is probably caused by the integrated graphic card ATI Mobility Radeon HD4330. 
the HP support offers only stuff for windows, I wrote them anyway but they didn't response yet.

well, what can I do about it?
will this issue be in other linux distributions (possibly Fedora, CentOS, openSUSE) too? 
the update manager offered me another driver for ATI graphic card, but when I installed it, the graphic environment stopped working at all and I had to remove it to get it to the original working but overheating state.

ANY help appreciated. thank you.

---

### Post by Yellow Pasque on 2010-09-13
Jaunty is using an outdated kernel. Newer kernels have much better support for open-source ATI power management. I'd recommend trying a LiveCD of Ubuntu Maverick/10.10 beta (which uses a 2.6.35.x kernel) and seeing if it improves the GPU temp.

Also, if the proprietary Catalyst/fglrx driver would work for you, it has power usage similar to Windows.

---

### Post by Heliix on 2010-09-14
thanks :) I'll try to reinstall it and I'll let you know how it worked.

is there any way of preserving the existing instalation and upgrading the kernel/or the drivers only, or is it too risky?

---

### Post by Heliix on 2010-09-16
> **Temüjin said:**
> Jaunty is using an outdated kernel. Newer kernels have much better support for open-source ATI power management. I'd recommend trying a LiveCD of Ubuntu Maverick/10.10 beta (which uses a 2.6.35.x kernel) and seeing if it improves the GPU temp.

Also, if the proprietary Catalyst/fglrx driver would work for you, it has power usage similar to Windows.

This is an advice from my friend who do not wish to be named:

Thanks, finaly we used the "proprietary Catalyst/fglrx driver" and it's look like OK.
Because we installed actual Lubuntu 10.04 distribution, we have
to install **xorg-driver-fglrx** package firstly and then the proprietary driver from [this page]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx"). 

Because we firstly forgot to install xorg-driver-fglrx, it cause that we can't start system and we stay in blinking terminal.

BTW: Message for BFU: If you have installed default Lubuntu 10.04 distribution on this notebook, you are using just "vesa" driver. This driver can use just 2D but not 3D. So many application can crash on it.

If you can use 3D on this notebook, you can proove by running **sudo glxgears** application in terminal. If this command return a window with 3 rotating gears, everything is OK. If not, you have to install proprietary driver.

---

### Post by WilliamNY on 2010-11-21
> **Heliix said:**
> thanks :) I'll try to reinstall it and I'll let you know how it worked.

is there any way of preserving the existing instalation and upgrading the kernel/or the drivers only, or is it too risky?

Hi Heliix.

So did your new installation work for you? I am seriously considering buying a dm3 series notebook (I'm looking at dm3-3010us). The model looks very good, and is precisely what I'm looking for.

So, was the overheating problem solved?

---

