---
title: "WIFI not recognized by 10.04 on HP G7"
date: 2012-06-02
forum: Hardware
---

### Post by Randy M on 2012-06-02
I installed 10.4 on my new HP G7, but it doesn't recognize the wifi card. I've downloaded the drivers that HP shows for it, but NDIS doesn't recognize them and tells me they are invalid drivers. Any suggestions on what to try next?

sudo lshw -c network
[sudo] password for randy: 
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: ec:9a:74:53:69:21
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:2000(size=256) memory:f0004000-f0004fff(prefetchable) memory:f0000000-f0003fff(prefetchable)

---

### Post by Randy M on 2012-06-02
Some more info, but not much progress. I found this thread [http://ubuntuforums.org/showthread.php?t=1604101](http://ubuntuforums.org/showthread.php?t=1604101) that gave some info about the card. It's a Realtek RTL8188CE. The thread gave two possible answers. One it a PPA for the driver. It did nothing. The second is how to install the driver from the Realtek site. It gives an error. Any ideas about what's going on here?

root@randy-laptop:/home/randy/Documents/Realtek# make
make -C /lib/modules/2.6.32-41-generic/build M=/home/randy/Documents/Realtek modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-41-generic'
  CC [M]  /home/randy/Documents/Realtek/base.o
In file included from /home/randy/Documents/Realtek/base.c:32:
/home/randy/Documents/Realtek/wifi.h: In function ‘rtl_find_sta’:
/home/randy/Documents/Realtek/wifi.h:2094: warning: passing argument 1 of ‘ieee80211_find_sta’ from incompatible pointer type
include/net/mac80211.h:2086: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
In file included from /home/randy/Documents/Realtek/base.c:34:
/home/randy/Documents/Realtek/base.h: At top level:
/home/randy/Documents/Realtek/base.h:143: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/randy/Documents/Realtek/base.h:143: warning: its scope is only this definition or declaration, which is probably not what you want
/home/randy/Documents/Realtek/base.c: In function ‘_rtl_init_mac80211’:
/home/randy/Documents/Realtek/base.c:322: error: ‘IEEE80211_HW_CONNECTION_MONITOR’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:322: error: (Each undeclared identifier is reported only once
/home/randy/Documents/Realtek/base.c:322: error: for each function it appears in.)
/home/randy/Documents/Realtek/base.c: In function ‘rtl_tx_agg_start’:
/home/randy/Documents/Realtek/base.c:991: warning: passing argument 1 of ‘ieee80211_start_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2033: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/randy/Documents/Realtek/base.c: In function ‘rtl_tx_agg_stop’:
/home/randy/Documents/Realtek/base.c:1020: warning: passing argument 1 of ‘ieee80211_stop_tx_ba_cb_irqsafe’ from incompatible pointer type
include/net/mac80211.h:2074: note: expected ‘struct ieee80211_hw *’ but argument is of type ‘struct ieee80211_vif *’
/home/randy/Documents/Realtek/base.c: In function ‘rtl_watchdog_wq_callback’:
/home/randy/Documents/Realtek/base.c:1274: error: implicit declaration of function ‘ieee80211_connection_loss’
/home/randy/Documents/Realtek/base.c: At top level:
/home/randy/Documents/Realtek/base.c:1332: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/randy/Documents/Realtek/base.c:1332: error: parameter 2 (‘smps’) has incomplete type
/home/randy/Documents/Realtek/base.c: In function ‘rtl_make_smps_action’:
/home/randy/Documents/Realtek/base.c:1352: error: ‘WLAN_HT_ACTION_SMPS’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1354: error: ‘IEEE80211_SMPS_AUTOMATIC’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1355: error: ‘IEEE80211_SMPS_NUM_MODES’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1357: error: ‘IEEE80211_SMPS_OFF’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1359: error: ‘WLAN_HT_SMPS_CONTROL_DISABLED’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1361: error: ‘IEEE80211_SMPS_STATIC’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1363: error: ‘WLAN_HT_SMPS_CONTROL_STATIC’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1365: error: ‘IEEE80211_SMPS_DYNAMIC’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c:1367: error: ‘WLAN_HT_SMPS_CONTROL_DYNAMIC’ undeclared (first use in this function)
/home/randy/Documents/Realtek/base.c: At top level:
/home/randy/Documents/Realtek/base.c:1376: warning: ‘enum ieee80211_smps_mode’ declared inside parameter list
/home/randy/Documents/Realtek/base.c:1376: error: parameter 3 (‘smps’) has incomplete type
/home/randy/Documents/Realtek/base.c: In function ‘rtl_send_smps_action’:
/home/randy/Documents/Realtek/base.c:1404: error: type of formal parameter 2 is incomplete
make[2]: *** [/home/randy/Documents/Realtek/base.o] Error 1
make[1]: *** [_module_/home/randy/Documents/Realtek] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-41-generic'
make: *** [all] Error 2
root@randy-laptop:/home/randy/Documents/Realtek#

---

### Post by ahallubuntu on 2012-06-02
You're almost there!  In Ubuntu, you need to give administrator privileges to certain commands to build drivers.  Just put the word "sudo " in front of any command to give it admin privileges.  It will ask you for the admin password the first time, then remember it for a while so it won't keep asking you.

So try

sudo make clean

(to erase anything you may have already built)

then

sudo make

then

sudo make install

most likely.

Note that you will need to edit the /etc/modules file (sudo gedit /etc/modules) and add the new module name to the tail end of this file (put a blank line after it) so it will get loaded automatically each time you boot.

Also, note that whenever you install a new kernel with the Update Manager, you will have to re-build/re-install this module all over again.  Just FYI.  I have built Realtek wireless modules like this before with Ubuntu.

---

### Post by Randy M on 2012-06-02
Possible progress!  Now the Hardware Drivers option shows that the Realtek 819x drivers are loaded, but not in use.

---

### Post by ahallubuntu on 2012-06-02
Did you do sudo make install ?

---

### Post by Randy M on 2012-06-03
I tried SUDO in front of each command, and I entered SUDO SU to put myself in superuser mode. Both methods produced the same results.

---

### Post by Randy M on 2012-06-03
I also booted 12.04 from a thumb drive. It finds the hardware and connected once. I haven't been able to get it to connect a second time. I'll try installing 12.04 and see what happens. It's probably best to do a new install to clear out any damage the other attempts may have done. My thanks for the responses and suggestions. They are truly appreciated.

---

### Post by Randy M on 2012-06-03
Installing 12.04 seems to have resolved the issue. WIFI is recognized and is working well.

---

