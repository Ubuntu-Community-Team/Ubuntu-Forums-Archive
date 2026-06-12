---
title: "AMD A8 7600 APU Driver?"
date: 2017-12-18
forum: Hardware
---

### Post by wauxhall on 2017-12-18
Do i have to install anything different than the additional drivers, 'amd-microcpu' one?

---

### Post by mastablasta on 2017-12-19
> **wauxhall said:**
> Do i have to install anything different than the additional drivers, 'amd-microcpu' one?

depends on which version of Ubuntu you have installed. but likely no, nothing else. they should be included in kernel (Radeon driver). system offers them for install if more are available.

amd-microcpu is basically fixes for the CPU part.

---

### Post by wauxhall on 2017-12-19
> **mastablasta said:**
> depends on which version of Ubuntu you have installed. but likely no, nothing else. they should be included in kernel (Radeon driver). system offers them for install if more are available.

amd-microcpu is basically fixes for the CPU part.


Ubuntu 16.04 LTS Sir.

---

### Post by mastablasta on 2017-12-19
The the chip you have will use Radeon driver. 

original 14.04 ( not the point releases) can use proprietary AMD fglrx driver (Catalyst), but that Ubuntu is supported until around April 2019 (old releases: [http://old-releases.ubuntu.com/releases/14.04.0/](http://old-releases.ubuntu.com/releases/14.04.0/) ) . 
16.04.3 has same kernel as 17.04 had. 16.04.4 should be out soon i believe

more info on releases and kernels: [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

latest kernel is in 17.10. 

in linux (unlike in windows) opensource drivers are included in kernel (the OS core). the higher the kernel the newer the drivers (usually, but not always - legacy chips might only have bug fixes or just support)

---

### Post by Yellow Pasque on 2017-12-19
I would install mesa-vdpau-drivers for video hardware decode support (of local files).

---

### Post by wauxhall on 2017-12-20
> **Temüjin said:**
> I would install mesa-vdpau-drivers for video hardware decode support (of local files).

Do you recommend it? How can i install? Sorry, i'm a new user.

---

