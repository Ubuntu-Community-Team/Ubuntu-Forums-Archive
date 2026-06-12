---
title: "RocketRaid 640L - can not compile driver"
date: 2015-03-29
forum: Hardware
---

### Post by JohnFante on 2015-03-29
I am trying to get my Ubuntu Mate 15.04 beta 2 system to recognize my HighPoint RocketRaid 640L raid card. 

I have downloaded the latest drivers from here:

[http://www.highpoint-tech.com/BIOS_Driver/RR64xL/Linux/RR64xl_Linux_Src_v1.3.7_13_12_27.tar.gz](http://www.highpoint-tech.com/BIOS_Driver/RR64xL/Linux/RR64xl_Linux_Src_v1.3.7_13_12_27.tar.gz)

And I am following the guide here: 

[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

I get this when I try to make:

```
benny@benny-EX58-UD4P:~/rr64xl-linux-src-v1.3.7/product/rr64xl/linux$ make
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-10-generic'
  CC [M]  /home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/os_linux.o
  CC [M]  /home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/osm_linux.o
  CC [M]  /home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/div64.o
  CC [M]  /home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/hptinfo.o
  CC [M]  /home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/config.o
/home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/config.c:26:31: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
 char driver_ver[] = "v1.3.7(" __DATE__ " " __TIME__ ")";
                               ^
/home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/config.c:26:44: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
 char driver_ver[] = "v1.3.7(" __DATE__ " " __TIME__ ")";
                                            ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/config.o' failed
make[2]: *** [/home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build/config.o] Error 1
Makefile:1394: recipe for target '_module_/home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build' failed
make[1]: *** [_module_/home/benny/rr64xl-linux-src-v1.3.7/product/rr64xl/linux/.build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-10-generic'
../../../inc/linux_32mpa/Makefile.def:108: recipe for target 'rr640l.ko' failed
make: *** [rr640l.ko] Error 2
benny@benny-EX58-UD4P:~/rr64xl-linux-src-v1.3.7/product/rr64xl/linux$ 

```

Any suggestions?

---

### Post by lukeiamyourfather on 2015-03-30
According to High Point their open source driver supports up to kernel 3.10 which is not a recent kernel (circa 2013). Ubuntu 15.04 uses kernel 3.19 which is very recent. I'd ask High Point support to update their driver. I've had one High Point controller, never again. Their support for Linux is awful.

---

### Post by JohnFante on 2015-03-30
Thank you for the reply. I have written to HighPoint and asked them to update the drivers. Lets see what that brings.

---

### Post by JohnFante on 2015-04-01
Great news! I mailed to HighPoint and the replied with a new beta driver that supports newer kernels including the one in 15.04 :-)

I did not follow the ubuntu guide linked to above. I just extracted, sudo make install, and sudo modprobe rr640l and now I can see my two partitions on the RocketRaid 640L.

I am striping (Raid 0) two HD's and I made the array in the RocketRaid bios on boot up.

Thanks to HighPoint for great service. I have gotten their permission to share the beta-driver here, so if anybody else can use them please do and report issues to HighPoint.

---

### Post by lukeiamyourfather on 2015-04-01
I'd follow the instructions on the Ubuntu wiki post if possible since it uses DKMS which will automatically rebuild the kernel module if the kernel changes. Without DKMS the driver will break when the kernel changes.

---

### Post by JohnFante on 2015-11-21
The driver posted at the top did not compile with the latest kernel (4.x series). I wrote to HighPoint at they supplied a new updated version. I have gotten permission to share the driver here. They are beta but work with me. Please report bugs to HighPoint if you find any.

---

### Post by ykuchinskiy on 2016-10-16
Thank you John, it is working with Ubuntu 14.04.4 & kernel 4.2.0-42 and x64 architecture.

At the same time, I'm trying to build drivers for ARM ([COLOR=#252525][FONT=sans-serif]Tegra[/FONT][/COLOR]), board Jetson [COLOR=#252525][FONT=sans-serif]TX1, with no luck. I emailed to [/FONT][/COLOR]highpoint, will see if they can help.

---

### Post by oldos2er on 2016-10-16
Old thread about an EOL Ubuntu version closed. Please start a new thread if there are problems or questions regarding a supported version.

---

