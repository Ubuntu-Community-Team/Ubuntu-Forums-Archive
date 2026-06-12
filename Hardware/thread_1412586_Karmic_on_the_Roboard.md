---
title: "Karmic on the Roboard"
date: 2010-02-21
forum: Hardware
---

### Post by fca_neo on 2010-02-21
Hello everybody,

I am installing Karmic on a [RoBoard]("http://www.roboard.com/RB-100.htm") (follow the link for more info). It is a small embedded system that uses the [Vortex86DX]("http://www.dmp.com.tw/tech/vortex86dx/"), a 32bit x86 CPU running at 1000MHz, and 256MB DRAM. It has a 8GB SD Card as the main storage. 

This is mainly a single board computer intended for controlling robots.

I installed Xubuntu Karmic using another computer (an Eee PC) on the SD card and installed all the updates and removed the extra stuff such as games and office programs. I also installed the 386 Linux image in order to boot on the Vortex (I also removed all the extra old generic images).

The system boots up fine (on both systems) but the networking does not function (on the RoBoard). It requires the r6040 module that must be compiled against the kernel but I cannot get it to work.

I installed the appropriate headers and the build-essentials package, but I always get the same error when I try to compile:

(BTW, the contents of the tarball source code is the the directory /usr/src/r6040)

```

johnny5@RoBoard-1:/usr/src/r6040$ make
make -C /lib/modules/2.6.31-19-386/build M=/usr/src/r6040
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-386'
  CC [M]  /usr/src/r6040/r6040.o
/usr/src/r6040/r6040.c: In function &#8216;mdio_read&#8217;:
/usr/src/r6040/r6040.c:209: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;mdio_write&#8217;:
/usr/src/r6040/r6040.c:217: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_init_one&#8217;:
/usr/src/r6040/r6040.c:267: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c:298: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/usr/src/r6040/r6040.c:299: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/usr/src/r6040/r6040.c:300: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/usr/src/r6040/r6040.c:301: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/usr/src/r6040/r6040.c:302: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/usr/src/r6040/r6040.c:303: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/usr/src/r6040/r6040.c:305: error: &#8216;struct net_device&#8217; has no member named &#8216;tx_timeout&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_open&#8217;:
/usr/src/r6040/r6040.c:348: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_tx_timeout&#8217;:
/usr/src/r6040/r6040.c:380: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_start_xmit&#8217;:
/usr/src/r6040/r6040.c:395: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_interrupt&#8217;:
/usr/src/r6040/r6040.c:462: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_get_stats&#8217;:
/usr/src/r6040/r6040.c:523: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;set_multicast_list&#8217;:
/usr/src/r6040/r6040.c:535: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;netdev_get_drvinfo&#8217;:
/usr/src/r6040/r6040.c:582: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_close&#8217;:
/usr/src/r6040/r6040.c:596: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_down&#8217;:
/usr/src/r6040/r6040.c:621: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;netdev_ioctl&#8217;:
/usr/src/r6040/r6040.c:667: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_up&#8217;:
/usr/src/r6040/r6040.c:685: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_timer&#8217;:
/usr/src/r6040/r6040.c:772: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: In function &#8216;phy_mode_chk&#8217;:
/usr/src/r6040/r6040.c:818: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/usr/src/r6040/r6040.c: At top level:
/usr/src/r6040/r6040.c:926: fatal error: opening dependency file /usr/src/r6040/.r6040.o.d: Permission denied
compilation terminated.
make[2]: *** [/usr/src/r6040/r6040.o] Error 1
make[1]: *** [_module_/usr/src/r6040] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-386'
make: *** [all] Error 2

```

I also tried to follow this advice but without success: [http://ubuntuforums.org/showthread.php?t=1052426]("http://ubuntuforums.org/showthread.php?t=1052426")

Any ideas on how to get this compiled? Also, what is the best source for getting the source code of such modules; is there any official place or just fishing around the net is fine?

I'm planning on summarizing the installation process in a nice post for future reference so any help would be greatly appreciated.

Thanks to all!

---

