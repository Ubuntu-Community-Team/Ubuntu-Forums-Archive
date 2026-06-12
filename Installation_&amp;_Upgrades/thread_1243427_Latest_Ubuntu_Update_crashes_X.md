---
title: "Latest Ubuntu Update crashes X"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by Buschbarber on 2009-08-18
I am running Ubuntu Ultimate Edition 2.3 based upon Ubuntu 9.04.

Today I received a prompt to install the latest Updates. After everything was downloaded and installed I was informed I needed to Reboot. Upon Reboot, X crashes. I Rebooted again and chose the previous kernel(-14) from the Grub menu. Everything booted up fine.

Here is a copy of the Grub menu:

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=68320aa0-8c38-491c-8003-eb32914aab6c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		68320aa0-8c38-491c-8003-eb32914aab6c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

What is the best way to correct this problem?

I am running the 185.18.14 drivers. I have not upgraded to the 185.18.31 drivers because I was waiting for the 190 drivers to come out.

---

### Post by markbuntu on 2009-08-18
You may need to reinstall the driver on the new kernel. This is a very common problem with kernel updates and is mostly caused by not removing old drivers before installing new ones. If you do not remove the old driver then the new kernel sees more than one set of driver kernel modules and so does not build any of them into the kernel.

You will see messages to this effect if you watch the terminal as the new kernel builds.

---

### Post by Buschbarber on 2009-08-19
> **markbuntu said:**
> You may need to reinstall the driver on the new kernel. This is a very common problem with kernel updates and is mostly caused by not removing old drivers before installing new ones. If you do not remove the old driver then the new kernel sees more than one set of driver kernel modules and so does not build any of them into the kernel.

You will see messages to this effect if you watch the terminal as the new kernel builds.

Thank you!! When I accepted the Updates, I did not realize that I was receiving a new Kernel.

I followed a thread, that I have used before, to successfully remove a previous Nvidia driver and Download/Install the latest driver. All went well.

Do you know if the 190 version of the drivers will have an option to Resize the Display, like the Windows version does? I have had an Overscan problem, with Ubuntu, which I get around by accessing the Service Menu, in my Sony 50" HDTV, and setting Overscan to Zero. I still have a small portion of my Ubuntu Desktop cut off.

Thanks

---

