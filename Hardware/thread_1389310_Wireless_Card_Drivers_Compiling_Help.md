---
title: "Wireless Card Drivers Compiling Help"
date: 2010-01-24
forum: Hardware
---

### Post by JumpForJoy on 2010-01-24
Hi, I recently bought a new Sabrent Wireless-N PCI card.  It came with linux drivers on a mini-cd, but I'm having a lot of trouble getting them to work.  I think they want you to build your own driver, and the readme says:
> =======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make			
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2860sta
I follow the instructions through, but I get errors when I make:
> zachary@zachary-desktop:~/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0$ make
make -C tools
make[1]: Entering directory `/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.o
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c: In function &#8216;RTMPReadParametersHook&#8217;:
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:928: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:929: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:1554: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:1555: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
make[2]: *** [/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [LINUX] Error 2

Is there a better/easier way to get the drivers for my card?  Or should I just try to figure out how to compile these?

Thanks for any help,
Jump For Joy

---

### Post by JumpForJoy on 2010-01-24
I didn't see the "networking & wireless" section before I posted this, so I posted this question over there.

Sorry for any troubles,
Jump For Joy

Solved [here]("http://ubuntuforums.org/showthread.php?t=1389311").

---

