---
title: "Driver compilation errors"
date: 2008-11-24
forum: General Help
---

### Post by Bl4z3r on 2008-11-24
I have recently downloaded and installed a new and clean installation of Kubuntu (Intrepid) and noticed that my wifi drivers needed some updating to support injection. after downloading and patching them, this is what happens when I execute the "make" command;

root@ubuntu:/rtl8187_linux_26.1010.0622.2006# make
rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/2.6.27-7-generic/build M=/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
In file included from /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:17:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv_rtl7&#8217;:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:1181: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv_rtl7&#8217; which is not static
  CC [M]  /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.o
In file included from /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.c:52:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv_rtl7&#8217;:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:1181: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv_rtl7&#8217; which is not static
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.c: In function &#8216;ieee80211_monitor_rx_rtl7&#8217;:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_rx.c:107: warning: cast from pointer to integer of different size
  CC [M]  /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_tx.o
In file included from /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_tx.c:60:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv_rtl7&#8217;:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:1181: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv_rtl7&#8217; which is not static
  CC [M]  /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.o
In file included from /rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:37:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h: In function &#8216;ieee80211_priv_rtl7&#8217;:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:1181: warning: &#8216;netdev_priv&#8217; is static but used in inline function &#8216;ieee80211_priv_rtl7&#8217; which is not static
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c: In function &#8216;ipw2100_translate_scan_rtl7&#8217;:
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:57: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:57: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:57: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:57: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:66: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:66: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:66: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:66: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:69: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:69: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:69: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:69: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:75: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:75: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:75: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:75: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:87: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:87: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:87: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:87: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:97: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:97: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:97: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:97: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:106: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:106: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:106: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:106: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:136: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:136: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:136: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:136: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:141: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:141: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:141: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:141: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:157: warning: passing argument 1 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:157: warning: passing argument 3 of &#8216;iwe_stream_add_event&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:157: warning: passing argument 4 of &#8216;iwe_stream_add_event&#8217; makes pointer from integer without a cast
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:157: error: too few arguments to function &#8216;iwe_stream_add_event&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:164: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:164: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:164: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:164: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:178: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:178: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:178: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:178: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:193: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:193: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:193: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:193: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:204: warning: passing argument 1 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:204: warning: passing argument 3 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:204: warning: passing argument 4 of &#8216;iwe_stream_add_point&#8217; from incompatible pointer type
/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.c:204: error: too few arguments to function &#8216;iwe_stream_add_point&#8217;
make[3]: *** [/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_wx.o] Error 1
make[2]: *** [_module_/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/rtl8187_linux_26.1010.0622.2006/ieee80211'
make: *** [all] Error 2


and then the "make install" command;

root@ubuntu:/rtl8187_linux_26.1010.0622.2006# make install
install -d /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rtl_ieee80211
install -d /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rtl8187
install -m 644 ./ieee80211/*.ko /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rtl_ieee80211
install: cannot stat `./ieee80211/*.ko': No such file or directory
make: *** [install] Error 1
root@ubuntu:/rtl8187_linux_26.1010.0622.2006# 
  

Pardon my noobness, but what does this mean? I have only been exploring Linux for about six months now, so any help would definitely be appreciated.

---

### Post by PreviousN on 2008-11-25
It means that there was an error, and you cannot install an incompletely built module. It would be like trying to fly a plane without wings: parts are just not fully built. 

I cannot get it installed either. I'm trying to figure out the problem myself. If I figure it out I can report back. I've found this but it hasn't been that helpful:

[http://ubuntuforums.org/showthread.php?t=418311](http://ubuntuforums.org/showthread.php?t=418311)
[http://tinyshell.be/aircrackng/forum/index.php?topic=3833.0](http://tinyshell.be/aircrackng/forum/index.php?topic=3833.0)

You may get more help asking on a forum more specific to the problem, though I'm experiencing the problems as well.

---

### Post by PreviousN on 2008-11-25
Search for this term on this page: 
"iwe_stream_add_event" compile error message
[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

Then, search for this term on the same page: 
"asm/semaphore.h: No such file or directory" compile error message

Try compiling again. :-)

---

### Post by Bl4z3r on 2008-11-27
Hrmm   Do you have to have a log-in to see the search results? Because all it gives me is a link back to the original page. Also, I can't find where to register...  =/

---

### Post by PreviousN on 2008-12-25
search as in ctl f, not forum search.

---

### Post by PreviousN on 2009-01-07
In case he never figured out what I meant, these are ripped from the aircrack site:

"iwe_stream_add_event" compile error message

If you get a series of compile messages similar to &#8220;error: passing argument 1 of 'iwe_stream_add_event' from incompatible pointer type&#8221; then do the following:

Use

wget [http://patches.aircrack-ng.org/rtl8187_2.6.27.patch](http://patches.aircrack-ng.org/rtl8187_2.6.27.patch)

instead of

wget [http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch](http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch)

Then, use these instructions:
ifconfig wlan0 down	 
rmmod r8187 rtl8187 2>/dev/null
wget [http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip)
unzip rtl8187_linux_26.1010.zip
cd rtl8187_linux_26.1010.0622.2006/
wget [http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch](http://patches.aircrack-ng.org/rtl8187_2.6.24v3.patch)
tar xzf drv.tar.gz
tar xzf stack.tar.gz
patch -Np1 -i rtl8187_2.6.24v3.patch
make
make install

AND: 
"asm/semaphore.h: No such file or directory" compile error message

See this forum entry:

Please note a repair apparently needed in ' rtl8187_2.6.7.patch' for kernel 2.6.27 +/-

Unmodified, you will get the following error : &#8211; output from ' make ' :

...In file included from /usr/src/drivers/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187_core.c:65:
   /usr/src/drivers/rtl8187_linux_26.1010.0622.2006/beta-8187/r8187.h:47:27: error: asm/semaphore.h: No such file or directory

Modification to file r8187.h :

  lines 46,47 are :
    #include <asm/io.h>
    #include <asm/semaphore.h>

  overwrite lines 46,47 to this....
    #if (LINUX_VERSION_CODE < KERNEL_VERSION(2,6,19))
      #include <asm/io.h>
      #include <asm/semaphore.h>
    #else
      #include <linux/io.h>
      #include <linux/semaphore.h>
    #endif

Sorry about the lazy copy and paste, but hopefully this makes it clearer for the guy/other people. And for my reference :-)

---

