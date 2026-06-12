---
title: "64 bit nvidia driver for nvidia NV 9600M card"
date: 2008-12-25
forum: Hardware
---

### Post by Jeff k on 2008-12-25
Hello:
I have a laptop with 64 bit intel processor and the
driver is listed as
nvidia NV 9600M
I do not see this specifically listed on the nVidia cards
listed on the Ubuntu site.

There are several listed as
for Hardy Haron 8.04 is
nvidia-glx-new  169.12
nvidia-glx    96.43.05
nvidia-glx-legacy (did not record this)

My question is, which of these drivers would
be useful for this graphics card?


I have a prior post on this same subject;
the maximum resolution this system (64 bit)
will display is 800x600
It should be a few sizes larger than this.
Thanks for info
Jeff K

---

### Post by IQRules on 2008-12-25
Google this "envyng", install envyng might solve your problem

$ apt-cache search envyng
envyng-core - install the ATI or the NVIDIA driver
envyng-gtk - dummy package to envyng-core
envyng-qt - install the ATI or the NVIDIA driver

Run apt-get install to install the software.

---

### Post by Jeff k on 2008-12-27
Thank you for the suggestion and instruction. I have one issue that
has prevented me from connecting this machine to the internet to access repositories, and install from DVD. That is that I would have to assign it one of my static ip addresses to connect to internet. The other possibility is to have it connect through a proxy, which I have done in the past but that only seems to work when I am using GUI on target machine, not when I am using command line. I do not know how to tell applications like apt-get how to connect through a proxy server on the command line. I do some sensitive development on this machine and am uneasy connecting it
to public network directly.
To 'overload' this, I also have purchased a device that connects a network interface to a machine via USB port. It comes with drivers for Windows and Mac but does not mention anything about Linux or other 'nix' systems (such as FreeBSD that I use for web and DNS servers). 
What are my options on Ubuntu, or any Linux system for this device?

This laptop does not have a pc card slot. Otherwise I would get a pc card nic. I am using Ubuntu instead of Debian because Debian does not seem to have driver for DVD/CDROM on this machine, so won't install.

Thank you again for the attention;
Jeff K

---

