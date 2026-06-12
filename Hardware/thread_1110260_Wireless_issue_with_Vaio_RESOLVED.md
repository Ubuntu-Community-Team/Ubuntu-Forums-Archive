---
title: "Wireless issue with Vaio RESOLVED"
date: 2009-03-29
forum: Hardware
---

### Post by tomasaur on 2009-03-29
I'm running a Sony Vaio VGN-NR120E and had been unable to get the wireless up and running with KDE 4.1

I'm a total newbie to Linux, and while I can follow commands, I often don't know what they mean.  Just sayin'...

I've been trying to track this problem down, and here are the paths I've taken so far.

[B] 1) Disable Hardware drivers and install  backport.
[/B]
This procedure is detailed in this thread  [http://ubuntuforums.org/archive/index.php/t-970717.html](http://ubuntuforums.org/archive/index.php/t-970717.html) by ravi and goes like this:
[INDENT]
I can confirm that the process I previously posted to enable Atheros wifi cards works! 

System > Hardware Drivers: Disable the stock Atheros support. Something odd happened here, when I open the Hardware Driver manager from the K menu, it doesn't ask for the administrator password. I closed it, and then clicked on the tray icon for the Hardware Driver Manager, and then got prompted for the administrator password. Then I could disable the stock driver. 
Reboot. 
sudo aptitude install linux-backport-modules-intrepid-generic 

Reboot. 

Right click NetworkManager, your wireless should be up and running.[/INDENT]

This didn't work for me.

**2)  Tried the sequence of commands outlined here:**
  [http://ubuntuforums.org/showthread.php?t=887531&highlight=atheros+ar242x+802.11abg+wireless+pci+ex%20press+adapter&page=4](http://ubuntuforums.org/showthread.php?t=887531&highlight=atheros+ar242x+802.11abg+wireless+pci+ex%20press+adapter&page=4)

This is a little too lengthy to go into here, but it involves disabling  ath_hal in the file linux-restricted-modules-common.

I followed each of the terminal commands given, again, no luck.

**3) I followed the instructions given here**
 [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

Here are his abbreviated instructions:
[INDENT]sudo aptitude install build-essential
wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
sudo tar -jxvf compat-wireless-2.6.tar.bz2
Move to the directory you extracted in terminal
cd directoryname
Run the following commands
make [/INDENT]
**NOTE:  running this command gave me a series of permission denied messages**:  
hollydavid@Holly-Laptop:~/compat-wireless-2009-03-29$ make               
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
./scripts/check_config.sh: line 12: include/linux/compat_autoconf.h: Permission denied
./scripts/check_config.sh: line 13: .config.mk_md5sum.txt: Permission denied          
make: *** [.compat_autoconf_master-2009-03-24] Error 1         

**So I used the command *sudo make* instead**:                       
hollydavid@Holly-Laptop:~/compat-wireless-2009-03-29$ sudo make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.27-11-generic/build M=/home/hollydavid/compat-wireless-2009-03-29 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'                   

**This gave me a long output with a few errors.  Here are the errors:**
...
 CC [M]  /home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/b43/main.o             
/home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/b43/main.c: In function &#8216;b43_print_fw_helptext&#8217;:                                                                                             
/home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/b43/main.c:1971: warning: format not a string literal and no format arguments                                                                
/home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/b43/main.c:1973: warning: format not a string literal and no format arguments                                                                
/home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/b43/main.c: In function &#8216;b43_request_firmware&#8217;:                                                                                              
/home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/b43/main.c:2233: warning: format not a string literal and no format arguments                                                                
  CC [M]  /home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/b43/tables.o     
....
 CC [M]  /home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/ipw2x00/libipw_rx.o         
  CC [M]  /home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/ipw2x00/libipw_wx.o         
/home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/ipw2x00/libipw_wx.c: In function &#8216;ieee80211_wx_set_encodeext&#8217;:
/home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/ipw2x00/libipw_wx.c:622: warning: format not a string literal and no format arguments                                                                                                              
  CC [M]  /home/hollydavid/compat-wireless-2009-03-29/drivers/net/wireless/ipw2x00/libipw_geo.o       
....
CC [M]  /home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.o
/home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.c: In function &#8216;ieee80211_agg_splice_packets&#8217;:
/home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.c:385: error: implicit declaration of function &#8216;skb_queue_splice_tail_init&#8217;
make[3]: *** [/home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.o] Error 1
make[2]: *** [/home/hollydavid/compat-wireless-2009-03-29/net/mac80211] Error 2
make[1]: *** [_module_/home/hollydavid/compat-wireless-2009-03-29] Error 2

I then entered this command

[INDENT]sudo make install[/INDENT]

and got a long list of info with these errors at the end:
...
make -C /lib/modules/2.6.27-11-generic/build M=/home/hollydavid/compat-wireless-2009-03-29 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.o
/home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.c: In function &#8216;ieee80211_agg_splice_packets&#8217;:
/home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.c:385: error: implicit declaration of function &#8216;skb_queue_splice_tail_init&#8217;
make[3]: *** [/home/hollydavid/compat-wireless-2009-03-29/net/mac80211/agg-tx.o] Error 1
make[2]: *** [/home/hollydavid/compat-wireless-2009-03-29/net/mac80211] Error 2
make[1]: *** [_module_/home/hollydavid/compat-wireless-2009-03-29] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2

Next I entered these commands:

[INDENT]sudo make unload
sudo make load[/INDENT]

Neither had any sort of scrolling response after entering them.
Network Manager didn't give me any indication that my wireless was active.

At this point, I rebooted.

And it worked.

I should note that the first time that I tried this last method it didn't work.  I guess that all my prior stumbling around did something useful.
I hope this is helpful to someone out there.

---

