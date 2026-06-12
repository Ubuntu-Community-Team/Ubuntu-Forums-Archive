---
title: "Will Intel N135 work from the box on Ubuntu 12.04 LTS?"
date: 2012-10-25
forum: Hardware
---

### Post by LFX64 on 2012-10-25
I've been wanting to ditch Windows for a while... and I'm trying to sell my current PC. I have some annoying issues with Windows 7, but even though it's good for gaming, I hate being held by the balls by Windows because it's the go-to OS for simplistically jamming on my favourite titles.

I don't want Windows 8, because... it's going to be evil but I want to be able to game! Ubuntu to the rescue! However...

Will an Intel N135 work out of the box with Ubuntu 12.04 LTS? I just don't want to run into any issues from the off. Obviously I don't want to have to rely on an Ethernet cable for updates.

Also, what you think folks?

i5-3210m or i7-3610QM.

i5 has higher base clocks. i7 has 4 cores / 8 threads and a higher total Turbo (3.3 as opposed to 3.1). Note this is going to be in a laptop, so the i7 has 45TDP and will obviously make more heat.

Just to note it's a custom Optimus IV from PCSpecialist. AUO Screen. 8GB Kingston Hyper-X Genesis. 500GB WD Scorpio. Nvidia GTX660m. 15.6" 1080p screen. I'll be picking the MX-4, a paste I always use for building PCs/changing coolers to help with the heat.

Appreciate any answers given.

:)

---

### Post by ahallubuntu on 2012-10-25
According to this page:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

The Intel Centrino Wireless-N 135 card has been supported with the built-in iwlwifi module in the kernel since kernel 3.2.0 .  I believe you get at least that kernel in Ubuntu 12.04.1 LTS; if you don't, wire in with an ethernet cable to do all your updates then the wireless should work.

---

### Post by ahallubuntu on 2012-10-25
As for the CPU: only you know whether you really need that much performance in a laptop CPU vs. the extra heat/reduced battery life.

---

### Post by grahammechanical on 2012-10-26
> Just to note it's a custom Optimus IV

That is where you will hit problems and it is because Nvidia has only just decided to develop a Linux driver for this.

Here is an alternative:

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

Regards.

---

