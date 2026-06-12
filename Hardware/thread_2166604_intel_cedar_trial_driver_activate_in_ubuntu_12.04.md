---
title: "intel cedar trial driver activate in ubuntu 12.04"
date: 2013-08-10
forum: Hardware
---

### Post by ssanjeewa20 on 2013-08-10
hello

can enyone say how can activate cedar trial drivers in ubuntu 12.04. intel atom n2600 processor

---

### Post by Cheesemill on 2013-08-10
You're already using them.

Intel chipset, CPU and GPU drivers are built into the kernel.

---

### Post by Yellow Pasque on 2013-08-10
@Cheesemill: the n2600 is a cedarview chip, which uses PowerVR graphics. The regular intel driver does not work for PowerVR GPU's, because they're completely different than Intel GPU's. To use the special cedarview driver, you have to be using a 3.2 kernel (it's a closed-source module that only supports that kernel version). 

The easiest way to use the cedarview driver is install ubuntu 12.04.1: [http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)
Reference: [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584)

---

### Post by Cheesemill on 2013-08-10
> **Temüjin said:**
> @Cheesemill: the n2600 is a cedarview chip, which uses PowerVR graphics.

Thanks for this information, I always assumed that all Intel chips had Intel graphics.

---

### Post by texadactyl on 2013-09-06
Reference 1: [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584]("https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584")
Reference 2: [https://01.org/]("https://01.org/")
Reference 3: [http://www.minnowboard.org/]("http://www.minnowboard.org/")

I agree with the decision in reference #1; its just not worth pursuing something without vendor (Intel) support.  Using the Intel software from reference #2, I could not identify Intel hardware (GMA3650) as Intel!  I hope that new low-power Intel efforts like reference #3 work out better for Linux users although (caution) it appears to have GMA600 graphics.

I am also an "Intel orphan" running Cedar View on an Intel D2550MUD2 motherboard (Atom-CPU, chipset NM10, graphics processor GMA3650).  In Xubuntu saucy (13.10), kernel module gma500_gfx and the modesetting X driver were autoselected for my installation.  This works fairly well for a programmer (me) although it might be sub-optimal for an Ubuntu Studio user.  At least, I can use the full display resolution capability (1920x1080x60) of my 22" monitor.

Yes, had I had done research into the Linux integration aspects of Cedar View, I probably would have made a different motherboard purchase decision.  Water under the bridge.

---

