---
title: "AMD C50 cpu &amp; AMD 6250 onboard"
date: 2021-09-10
forum: Hardware
---

### Post by seithan on 2021-09-10
Hello, ):P
i primarily using the netbook (nb550d) for running services but i'd like to play a youtube video or two. The performance on the generic vga driver is abysmal so im thinking, has anyone tried installing successfully Catalysts (or any other software that would offer 3D acceleration , esp within Chrome) on this old chipset? Tried with installing catalysts but i ended up with a broken lubuntu installation where i could switch to no tty (alt+F2/alt+ctrl+F2), and only solution was either fiddle through Live CD or reinstall. 

Any help is appreciated.

---

### Post by mikewhatever on 2021-09-10
Well, you can't expect too much of a 10 year old netbook. To play youtube videos eficiently, you need support for modern video codecs, which is tricky, as none of them were used by youtube in 2011. The old Catalist driver was discontinued by AMD in 2015. The only option for old AMD GPUs is now "radeon", which works reasonably well, but doesn't enable hardware accelerated video decoding, as the hardware does not support it.
You can check its capabilities with <glxinfo -B> and <vainfo>, but tamper you expectations.
The machine is actually not bad, just old, and it wasn't a speed demon even 10 years ago.
Intel based netbooks suffer from very similar problems, they've outlived their usefulness.

---

### Post by seithan on 2021-09-11
Tried installing a new radeon-pro driver package. it broke my ubuntu installation. Looks like there is no way to install fglrx on a new linux distro, at least in a sane way. And tbh the netbook is fine for running services (i run opnsense for fun through a VM, allocatin 1 core and 512mb RAM while the netbook has 2Gb ram) or office apps, but youtube is another story. Truth be told its always been REALLY slow, unable to play 720p/1080p with decent framerate, its just way worse now due to lack of prop drivers. Also, youtube worked way  better on windows installation rather on linux (at least 10y ago on this specific machine).

edit: some machines can't really simply be "revived" but just installing an SSD :D :D Like i said , its an ok machine to run services in a tight spot, but slow cpu, slow usb2, slow fast ethernet, really hinter its applications.

---

### Post by mastablasta on 2021-09-13
10 years ago most videos on you tube were probably still 360p or 480p. 

default opensource radeon is the only driver and should offer some hardware acceleration. 

but you may want to make sure you are using the old Xorg. : [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

also you need more ram. i know some C50 laptops could not increase ram and they only cam soldered with 2Gb. so i avoided them and got a slightly better and still cheap E-450. i increased ram to 8 GB and it flies. i sometimes feel that only it's slow HDD is holding it back.

---

### Post by Yellow Pasque on 2021-09-15
> **seithan said:**
> Looks like there is no way to install fglrx on a new linux distro, at least in a sane way.

No, and even if you did manage to get fglrx/Catalyst installed, it wouldn't do what you want. fglrx had better 3D performance in some scenarios, but its support for video decoding was awful.

---

