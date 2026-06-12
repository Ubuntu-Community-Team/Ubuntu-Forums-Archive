---
title: "Netgear A6210 Wifi Adapter Won't Connect To Network"
date: 2015-02-16
forum: Hardware
---

### Post by jade101j on 2015-02-16
My Netgear Wifi Adapter, A6210, the newer USB 3.0 version, won't connect to my network in Ubuntu, I've tried looking at other posts and following what they did, but to no avail, my Wifi Adapter still won't work, just tell me what you need to see and I'll do my best to get you what you need to solve the issue, glad for any help, and Thank You in advance :)

---

### Post by rjsec4ever on 2015-02-17
Same issue here.
Tried using ndiswrapper, and used the driver that was installed on my Windows HDD (netr28ux.inf).
Used the GUI version, said that the driver is installed, and is recognizing the device, as shown here.
[ATTACH=CONFIG]260051[/ATTACH]
However, I'm currently using a wired connection and only wired works.

Please note that because of this problem, you start to get verbose messages while booting up Ubuntu.

In terms of compiling the RT2870 driver given at [http://www.mediatek.com/en/downloads/rt2870usbrt2870rt2770](http://www.mediatek.com/en/downloads/rt2870usbrt2870rt2770),
I get various errors involving IOCTL, as shown here.
```
make -C tools
make[1]: Entering directory '/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/3.16.0-31-generic/build SUBDIRS=/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-3.16.0-31-generic'
  CC [M]  /home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.o
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1479:6: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
   if(!erq->flags & IW_ENCODE_MODE) 
      ^
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_private_show’:
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1830:78: error: macro "__DATE__" might prevent reproducible builds [-Werror=date-time]
             sprintf(extra, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                              ^
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1830:88: error: macro "__TIME__" might prevent reproducible builds [-Werror=date-time]
             sprintf(extra, "Driver version-%s, %s %s\n", STA_DRIVER_VERSION, __DATE__, __TIME__ );
                                                                                        ^
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:1979:1: warning: the frame size of 1672 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.c:599:1: warning: the frame size of 1304 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.o' failed
make[2]: *** [/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../os/linux/sta_ioctl.o] Error 1
Makefile:1345: recipe for target '_module_/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux' failed
make[1]: *** [_module_/home/askalangly/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-3.16.0-31-generic'
Makefile:243: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
```

On top of this, compiling my own ndiswrapper has various error messages as well.
```
make -C utils
make[1]: Entering directory '/home/askalangly/Downloads/ndiswrapper-1.59/utils'
make[1]: Nothing to be done for 'all'.
make[1]: Leaving directory '/home/askalangly/Downloads/ndiswrapper-1.59/utils'
make -C driver
make[1]: Entering directory '/home/askalangly/Downloads/ndiswrapper-1.59/driver'
make -C /usr/src/linux-headers-3.16.0-31-generic M=/home/askalangly/Downloads/ndiswrapper-1.59/driver
make[2]: Entering directory '/usr/src/linux-headers-3.16.0-31-generic'
  CC [M]  /home/askalangly/Downloads/ndiswrapper-1.59/driver/crt.o
/home/askalangly/Downloads/ndiswrapper-1.59/driver/crt.c: In function ‘_win_srand’:
/home/askalangly/Downloads/ndiswrapper-1.59/driver/crt.c:470:2: error: implicit declaration of function ‘net_srandom’ [-Werror=implicit-function-declaration]
  net_srandom(seed);
  ^
cc1: some warnings being treated as errors
scripts/Makefile.build:257: recipe for target '/home/askalangly/Downloads/ndiswrapper-1.59/driver/crt.o' failed
make[3]: *** [/home/askalangly/Downloads/ndiswrapper-1.59/driver/crt.o] Error 1
Makefile:1345: recipe for target '_module_/home/askalangly/Downloads/ndiswrapper-1.59/driver' failed
make[2]: *** [_module_/home/askalangly/Downloads/ndiswrapper-1.59/driver] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-3.16.0-31-generic'
Makefile:183: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
make[1]: Leaving directory '/home/askalangly/Downloads/ndiswrapper-1.59/driver'
Makefile:23: recipe for target 'driver' failed
make: *** [driver] Error 2

```

I'm just ticked off at the lack of Linux support Netgear has. Should have found this out before deciding to purchase the A6210.
(My main objective is to have a crossover cable always connected to the PlayStation 2.)

---

