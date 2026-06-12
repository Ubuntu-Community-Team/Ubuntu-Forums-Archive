---
title: "Ubuntu 8.10 and Alfa AWUS036H? (r8187)"
date: 2008-10-12
forum: Hardware
---

### Post by cooma7 on 2008-10-12
Hi, I was just wondering if anyone has managed to get Ubuntu 8.10 to work with the ALFA AWUS036H? (r818 chipset)in monitor mode
I have tried a bunch of times and just keep get of errors when using "make" and "make install" section of patching the drivers ([http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187)) 

Ill go into more details with errors when i get home from work,. Just wondering if anyone else has had problems or have it working?

thanks.

Ryan

---

### Post by Helldrik on 2008-11-06
Hello!
I have been trying to install exactly the same adapter, and followint the procedure, I get the same errors when using "make" and "make install" (Ive also blacklisted r8187)...
Have you managed to get those drivers work with (k)ubuntu 8.10?

thanks in advance

---

### Post by Xnyper on 2008-12-17
Same issue, bump.

---

### Post by redonwhite on 2009-01-14
I was thinking about purchasing the Alfa AWUS036H.  So you guys are having a hard time getting it to work for Ubuntu?  Any suggestions on something else that might work better?

---

### Post by Blackdragon1400 on 2009-02-01
I also have the same problem :Bump: I belive it has somthing to do with the ieee80211 subsystem but frankly I am not used to patching, manipulating ect. this subsystem. And I am also using 8.04.2 not intrepid if that changes anyhthing (i dont belive it does) The instructions on the driver CD are simple:

(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )
	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.

After running ./makedrv I get the following output w/lots of errors

```
ieee80211/
ieee80211/license
ieee80211/ieee80211_crypt.c
ieee80211/ieee80211_tx.c
ieee80211/ieee80211_softmac.c
ieee80211/ieee80211_softmac_wx.c
ieee80211/ieee80211_module.c
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_rx.c
ieee80211/tags
ieee80211/ieee80211_crypt_tkip.c
ieee80211/Makefile
ieee80211/readme
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211.h
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt.h
rtl8187/
rtl8187/license
rtl8187/r8180_rtl8225z2.c
rtl8187/r8180_rtl8225.h
rtl8187/r8187_led.c
rtl8187/r8180_93cx6.h
rtl8187/r8180_wx.h
rtl8187/r8180_hw.h
rtl8187/copying
rtl8187/r8187_led.h
rtl8187/r8180_pm.h
rtl8187/tags
rtl8187/r8187.h
rtl8187/Makefile
rtl8187/r8180_rtl8225.c
rtl8187/readme
rtl8187/install
rtl8187/.tmp_versions/
rtl8187/.tmp_versions/r8187.mod
rtl8187/changes
rtl8187/r8180_wx.c
rtl8187/r8180_pm.c
rtl8187/r8187_core.c
rtl8187/r8180_93cx6.c
rtl8187/authors
rtl8187/ieee80211.h
rtl8187/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/tmp
make -C /lib/modules/2.6.24-23-generic/build M=/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_scan_wq&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:421: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_stop_scan&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:495: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_abort&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:915: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_stop_protocol_rtl&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2120: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: (Each undeclared identifier is reported only once
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2229: error: for each function it appears in.)
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2230:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2231:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2232:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2233:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2234:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_free&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.c:2255: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type
make[2]: *** [/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/tmp
make -C /lib/modules/2.6.24-23-generic/build M=/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o
In file included from /home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:64:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187.h:29:26: error: linux/config.h: No such file or directory
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_init&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: (Each undeclared identifier is reported only once
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:450: error: for each function it appears in.)
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_proc_module_remove&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:456: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_rx_urbsubmit&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:730: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_tx&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:1648: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8180_init&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2053: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2054:77: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2055:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2056:80: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2057:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c: In function &#8216;rtl8187_usb_probe&#8217;:
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2938: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.c:2956: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217;
make[2]: *** [/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187/r8187_core.o] Error 1
make[1]: *** [_module_/home/patrick/Desktop/rtl8187_linux_26.1025.0328.2007/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [modules] Error 2

```

I assume you are supposed to patch the 80211 subsystem for this to work but I do not know how (last time I broke my wireless tring to do this) 

can anyone help?

---

### Post by xcell on 2009-02-25
Same problem here... Please someone?

---

### Post by xcell on 2009-02-26
> **cooma7 said:**
> I have tried a bunch of times and just keep get of errors when using "make" and "make install" section of patching the drivers ([http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187)) 

Someone?

---

### Post by rattking on 2009-02-26
Hi I have gotten the Alpha AWUS036H working on 8.10
I followed the instructions at [http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187) but changed a few things because we are using the 2.6.27 kernel

ifconfig wlan0 down	 
rmmod r8187 rtl8187 2>/dev/null
wget [http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip)
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget [http://patches.aircrack-ng.org/rtl8187_2.6.27.patch](http://patches.aircrack-ng.org/rtl8187_2.6.27.patch)
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.27.patch

then I had to edit the file 
beta-8187/r8187.h
and change
#include <asm/semaphore.h>
to
#include <linux/semaphore.h>

make
make install

hope that helps..

ps. I still cant get this driver to compile in a mameo scratchbox but thats a problem for a different forum < Got it!
pps. there is a newer driver rtl8187_linux_26.1025.0328.2007 thats listed non-beta but i cant seem to find a patch for it..

---

### Post by xcell on 2009-02-27
Awesome man! Works like a charm. Much appreciated!

Now #airmon-ng start wlan0 gives me R8187 in monitor mode. Next to check: packet injection!

---

### Post by N04h on 2009-03-04
Nevermind.  Got it figured out.

---

