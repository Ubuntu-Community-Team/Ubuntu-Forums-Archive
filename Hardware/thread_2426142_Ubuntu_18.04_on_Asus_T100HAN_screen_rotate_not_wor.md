---
title: "Ubuntu 18.04 on Asus T100HAN screen rotate not working"
date: 2019-09-05
forum: Hardware
---

### Post by skippy1981 on 2019-09-05
Hi everyone,

In the past I have had a couple of laptops and desktops running smoothly on Ubuntu.

My latest laptop hybrid is an Asus T100HAN. I have it for a while now  and finally had the courage to install Ubuntu next to Windows as  multiboot.

A lot of issues with this laptop have been solved in the last couple of years. So "out of the box" Ubuntu 18.04 runs very well.

There is 1 issue which is still not working on my system, which is the  automatic rotation of the screen. I have found a lot of information  about possible solutions. The latest I have found has to do with  powering on the accellerometer sensors during boot up. Apparently they  are not given enough time to initiate and apparently something could be  added in the kernel to give them more time to initiate:

[https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=6f92253024d9d947a4f454654840ce479e251376](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=6f92253024d9d947a4f454654840ce479e251376)
[https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f1664eaacec31035450132c46ed2915fd2b2049a](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f1664eaacec31035450132c46ed2915fd2b2049a)

Weird thing is, this issue should have been solved after Kernel version  4.13 or something. But still the sensors are undefined after startup.

I am not at all experienced with Kernels and changing stuff in them, like described on git.kernel.org etc.

Can anyone give me a hint how to proceed?

Thanks in advance

---

### Post by mörgæs on 2019-09-05
Hi, welcome to the fora.
Does it work better in a live boot of 19.04?

---

### Post by skippy1981 on 2019-09-08
Thanks Mörgæs,

Great idea! After succesfully tried a live boot, I installed 19.04 instead of 18.04LTS. Screen rotating is working well in this version.

---

### Post by mörgæs on 2019-09-08
Congratulations.

Many of the problems posted in Ubuntuforum are from people trying to run old software on new hardware. From 20.04 onwards you can probably follow the LTS track if you prefer.

---

