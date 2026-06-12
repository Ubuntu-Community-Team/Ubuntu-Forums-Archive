---
title: "Ubuntu repositories for Nvidia drivers"
date: 2020-06-23
forum: Hardware
---

### Post by John Jason Jordan on 2020-06-23
There are dozens of Nvidia drivers in the repos, but there is no information there about which of Nvidia's hundreds of cards a given driver is good for. Surely there exists a chart somewhere so you can scroll down to your card and find the name of the package in the repository. I've spent a couple hours searching, but nada so far. Everyone else seems to have no problem finding the right driver, so I must be dumb. Can someone point me to an Nvidia driver selection tool?

PS: This is for a fresh install of Xubuntu 20.04, which installed the nouveau driver. However, there are problems using the nouveau driver with my card - low resolution and it uses only a quarter of the installed video RAM. I could download the proprietary driver from Nvidia, but it's a lot easier just to use the repositories.

---

### Post by CatKiller on 2020-06-23
> **John Jason Jordan said:**
> Can someone point me to an Nvidia driver selection tool?

[https://www.nvidia.co.uk/Download/index.aspx?lang=en-uk](https://www.nvidia.co.uk/Download/index.aspx?lang=en-uk) 

Don't download them from there, but it will show you which cards are supported by each driver version. Plus changelogs. 

Generally you want the latest version, unless your card is old and no longer supported, in which case you'd want the latest version that still supports it. Which you can find out on that page.

---

### Post by Yellow Pasque on 2020-06-23
There's "Additional Drivers" in Xubuntu's Settings menu. If you can't find it, run:
```
software-properties-gtk --open-tab=4
```
That tool works about 99% of the time, especially on a recent release of Ubuntu.

If you have a very new card on an older Ubuntu, you may have to use: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
(Note: There is no point in using this PPA on 20.04 at the moment.)

> Surely there exists a chart somewhere so you can scroll down to your card and find the name of the package in the repository.
Nvidia has a list in their README. It is not Ubuntu specific, but it lets you know which nvidia-driver package you want (e.g. nvidia-driver-440 or nvidia-driver 390)
[http://us.download.nvidia.com/XFree86/Linux-x86_64/440.82/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/440.82/README/supportedchips.html)

---

### Post by John Jason Jordan on 2020-06-23
> **Yellow Pasque said:**
> There's "Additional Drivers" in Xubuntu's Settings menu. If you can't find it, run:
```
software-properties-gtk --open-tab=4
```
That tool works about 99% of the time, especially on a recent release of Ubuntu.

Thanks! That did the job!

Now I have to work with it for a while to see if it solves my problems. The card in question is a Quadro NVS 140M in an ancient Thinkpad T61 that I am reviving. After installing 20.04 as a fresh install the computer was hanging on me after anywhere from five to 30 minutes. I used to use this computer as my main computer for years, and I dimly recall that I had FHD display, but the nouveau driver was giving me just 1680x1050, and when it would hang it seemed as though it was some window that wasn't being redrawn correctly. The command above gave me 340.108, and after installing it and rebooting, I saw the Nvidia logo displayed, and lshw -c video says the driver is Nvidia, but Display says I'm still at 1680x1050. It remains to be seen if the hanging problem is resolved.

Thanks again!

---

