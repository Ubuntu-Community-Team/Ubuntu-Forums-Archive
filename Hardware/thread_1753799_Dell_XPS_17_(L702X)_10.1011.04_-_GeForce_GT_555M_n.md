---
title: "Dell XPS 17 (L702X) 10.10/11.04 - GeForce GT 555M not working."
date: 2011-05-09
forum: Hardware
---

### Post by JimDanger on 2011-05-09
Hi all,

I bought a brand new Dell XPS 17 (L702X) laptop which I planned on using as a Linux machine. I've installed both Maverick & Natty with no problems as far as the default video driver goes. However, if I want any of the Desktop effects or anything other than the bare minimum, I need to install the proprietary Nvidia restricted drivers. Each time I install and reboot, the machine just hangs at boot (checking battery state.) The only way to get out of this is to Alt + F1 and rm /etc/X11/xorg.conf

Everything I google indicates that 11.04 supports this card, but my personal experience is stating otherwise. Can anyone please help me?

---

### Post by rosewood on 2011-05-15
Well it seems nVidia have recently released a new driver for this graphics card for Linux. You can search for it here:
[http://www.nvidia.com/Download/index.aspx]("http://www.nvidia.com/Download/index.aspx")

---

### Post by ZaHACKieL on 2011-05-16
I also bought an xps17 few days ago and Ubuntu 11.04 recognize everything because I can use advanced effects and Unity interface but Ubuntu suggested me to install the restricted drivers. I did it and the system stopped recognizing the graphic cards and I lost the effects and Unity. I had to reinstall the system. 

I also tried with the official drivers but they didn't work (and it's a pain in the neck to install them). 

What I noticed is that NVidia website says that the driver's size is 76.8MB but when you download it, it's just 47.3MB....Why do you think is that?

Anyone had successfully configured this card on Ubuntu 11.04?

---

### Post by ZaHACKieL on 2011-05-16
btw...where do I find the supported video cards list for Ubuntu 11.04? Thanx!

---

### Post by cbarmpar on 2011-05-21
Dear all,

I am also an owner of a dell XPS L702x.

If your laptop is Optimus enabled then you will not be able to use the nvidea provided drivers as the linux X server will only handle the integrated (Intel GPU).

You cant use the dGPU for displaying purposes hence you shouldn't install the nvidea driver.

There is a project regarding enabling optimus laptop to use the discrete GPU and you can find information on:
[http://www.martin-juhl.dk/](http://www.martin-juhl.dk/)

But I havent found time to try the above.
Probably it should work for our laptop as well.

If your laptop is 3d enabled I believe that optimus is not present and hence you can use the dGPU for displaying by installing the driver.

Christos

---

### Post by ZaHACKieL on 2011-05-21
Hi cbarmpar. What is that Optimus stuff? As you say, it seems Ubuntu 11.04 is using Intel GPU (mine is an i5) on my laptop since I have effects/Unity with no Nvidia drivers. How do I know if I have Optimus enabled? Thanx

---

### Post by ZaHACKieL on 2011-05-21
> **ZaHACKieL said:**
> Hi cbarmpar. What is that Optimus stuff? As you say, it seems Ubuntu 11.04 is using Intel GPU (mine is an i5) on my laptop since I have effects/Unity with no Nvidia drivers. How do I know if I have Optimus enabled? Thanx

I can answer myself now. Correct me if I'm wrong but I see that Optimus is that technology included in some laptops where you have 2 GPUs : Nvidia and, let's say Intel and it seems Optimus does not support Linux. ref. [http://en.wikipedia.org/wiki/Nvidia_Optimus](http://en.wikipedia.org/wiki/Nvidia_Optimus)

Thank you so much cbarmpar, you have pointed me to a specific direction to look for a solution. I'll try Bumblebee and let you know if I get this fixed. Bye!

---

### Post by nerdy_kid on 2011-07-11
any news on this?  I'm looking to buy a XPS17...

---

### Post by cbarmpar on 2011-07-11
Hi,

Optimus and linux would probably never work officially.

In order for linux drivers to work i suggest to find a laptop with hardware mux swithable from bios.

I ve heart that lenovo support that.

I hope I helped.

---

### Post by hutch120 on 2011-09-17
Trying to solve this issue here if you find a solution please post:
[https://github.com/MrMEEE/ironhide/issues/66](https://github.com/MrMEEE/ironhide/issues/66)

---

### Post by zoquero on 2011-09-18
Hi!

My **L702X** has **GeForce GT 550m** , not the 3GB 555m, but I'm having similar problems.

**Has anybody been able to install propietary drivers** no only on Nvidia GeForce GT 555m but also on Nvidia GeForce GT 550m**?** Any clue or link to info would be sincerely appreciated.

Ubuntu's guide doesn't work on my 11.4 64b, it ends falling to unaccelerated graphics, and Nvidia latest installer (280.13) also doesn't work for me.

Any help would be welcome.
**Thanks!**
/ Angel

---

### Post by hutch120 on 2011-09-18
I recommend checking this link:
 [https://github.com/MrMEEE/ironhide/issues/66](https://github.com/MrMEEE/ironhide/issues/66)

---

### Post by cmdematos on 2011-10-17
I have this all working on a GT550M. Please try looking at [this blog entry]("http://www.cmdematos.com/2011/10/ubuntu-1110-oneric-on-dell-xps17-l702x.html"), it may help you.

[http://www.cmdematos.com/2011/10/ubuntu-1110-oneric-on-dell-xps17-l702x.html](http://www.cmdematos.com/2011/10/ubuntu-1110-oneric-on-dell-xps17-l702x.html)

---

### Post by freyberry on 2012-01-17
If you have a machine with Optimus, don't install the proprietary drivers, just install Bumblebee (it will install the drivers for you).

If you want the full battery life (~7hrs), you need to install the 2.6 kernel.

Here's what you need to do (on x64):

a) Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/)

b) download those three files:
   - linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb
   - linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb	
   - linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb

c) open a terminal, cd into your download directory and execute this command:

sudo dpkg -i linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb

d) download this: [https://lists.launchpad.net/hybrid-graphics-linux/sh3hFub0KkvH.sh](https://lists.launchpad.net/hybrid-graphics-linux/sh3hFub0KkvH.sh)

e) go into a terminal, cd into download directory and execute these commands:

  git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
  cd acpi_call
  make
  sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/drivers/acpi/
  sudo depmod
  sh3hFub0KkvH.sh off

The last command disables the NVidia card. Voilà!

(btw. **you can still install bumblebee if you want to run 3D stuff with the NVidia card**)

---

### Post by Lekensteyn on 2012-01-21
Bumblebee 3.0 from the Bumblebee Project has been released and supports out-of-the-box power saving. See [http://askubuntu.com/a/36936/6969](http://askubuntu.com/a/36936/6969)
Note: do not use the mainline kernel, it will crash!

---

