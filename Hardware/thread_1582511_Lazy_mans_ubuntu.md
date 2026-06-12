---
title: "Lazy mans ubuntu?"
date: 2010-09-26
forum: Hardware
---

### Post by diebodie on 2010-09-26
Would it be possible to find and download a linux distro (preferably ubuntu) with madwifi pre-installed? I can't seem to install it the good old fashion way....

edit: Is this essentially what I'm looking for? [https://build.opensuse.org/project/monitor?project=home%3Ahschaa%3Amadwifi-free]("https://build.opensuse.org/project/monitor?project=home%3Ahschaa%3Amadwifi-free")

---

### Post by wojox on 2010-09-26
Linux Mint is probably what you seek. May want to check it out.

---

### Post by diebodie on 2010-09-26
Linux mint 9 or Linux debian?

---

### Post by coffeecat on 2010-09-26
Why do you want madwifi? The atheros drivers that come with Ubuntu have improved markedly in the last year+. Besides, the madwifi homepage doesn't seem to have been updated for more than a year. What wireless chipset do you have?

Does anyone know, is the madwifi project still alive?

---

### Post by diebodie on 2010-09-26
I'm using an old WG311T netgear 802.11g pci card. 

Though ubuntu 10.4 lets me connect out of the box, speed is crippled. Loading most webpages takes ~2+ minutes. I figured madwifi would help.

---

### Post by snowpine on 2010-09-26
Ubuntu *is* "the lazy man's Linux" so rather than switching distros, I recommend trying to work through whatever wireless problems you're having. 

Typically you can easily install a driver for most hardware by going to System->Administration->Hardware Drivers and letting Ubuntu scan your hardware for available drivers.

---

### Post by diebodie on 2010-09-26
> **snowpine said:**
> Ubuntu *is* "the lazy man's Linux" so rather than switching distros, I recommend trying to work through whatever wireless problems you're having. 

Typically you can easily install a driver for most hardware by going to System->Administration->Hardware Drivers and letting Ubuntu scan your hardware for available drivers.

Thanks! Does the system need to be connected to the internet though?

---

### Post by snowpine on 2010-09-26
> **diebodie said:**
> Thanks! Does the system need to be connected to the internet though?

I find a wired ethernet connection very helpful when diagnosing wireless problems, yes. Though I believe some users have had success copying drivers over from another computer with a USB stick if necessary.

---

### Post by diebodie on 2010-09-26
Alright ill have to try that. Mucho gracias!

---

### Post by diebodie on 2010-09-26
No luck. No drivers available. 


Any other ideas?

---

### Post by wojox on 2010-09-26
What happen's when you run any Live-CD's. Does wifi work?

---

### Post by diebodie on 2010-09-26
Yeah, it does but once again, it's extremely crippled.

---

### Post by wojox on 2010-09-26
> **diebodie said:**
> Linux mint 9 or Linux debian?

Either or. I'd try Mint first. Debian isn't really for the lazy.

---

### Post by diebodie on 2010-09-26
Ill try it out. Thanks everyone!

---

### Post by coffeecat on 2010-09-26
Since Mint 9 is based on Ubuntu 10.04, which is what you say you've tried, it will have the same wireless drivers. So I doubt it would make any difference. Ubuntu 10.10 (Maverick) is due to be released soon. That will have later drivers. It will be worth trying.

However...

> **diebodie said:**
> I'm using an old WG311T netgear 802.11g pci card. 

Tells us very little. What's the wireless chipset? Post the output of:

```
lspci | grep -i wireless
```Or if that produces nothing:

```
lspci | grep 802.11
```

---

### Post by diebodie on 2010-09-27
Cofeecat, I ended up getting this > 01:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

I tried installing madwifi again as a friend of mine suggested but everytime I get to ''sudo make'' I get this


> root@aj-desktop:/usr/src/madwifi-0.9.3.2# sudo make install
sh scripts/find-madwifi-modules.sh 2.6.32-21-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath'
test -d //lib/modules/2.6.32-21-generic/net || mkdir -p //lib/modules/2.6.32-21-generic/net
install ath_pci.ko //lib/modules/2.6.32-21-generic/net
install: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath'
make: *** [install-modules] Error 1
root@aj-desktop:/usr/src/madwifi-0.9.3.2# sudo make clean
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
		make -C $i clean; \
	done
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_hal'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate'
for i in amrr/ onoe/ sample/; do \
		make -C $i clean; \
	done
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/net80211'
make -C ./tools  clean
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig core a.out
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/tools'
rm -rf .tmp_versions
rm -f *.symvers svnversion.h
root@aj-desktop:/usr/src/madwifi-0.9.3.2# sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/usr/src/madwifi-0.9.3.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /usr/src/madwifi-0.9.3.2/ath/if_ath.o
In file included from /usr/src/madwifi-0.9.3.2/ath/../net80211/ieee80211_monitor.h:45,
                 from /usr/src/madwifi-0.9.3.2/ath/if_ath.c:71:
/usr/src/madwifi-0.9.3.2/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_attach':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:396: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:661: error: 'struct net_device' has no member named 'open'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:662: error: 'struct net_device' has no member named 'stop'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:663: error: 'struct net_device' has no member named 'hard_start_xmit'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:664: error: 'struct net_device' has no member named 'tx_timeout'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:666: error: 'struct net_device' has no member named 'set_multicast_list'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:667: error: 'struct net_device' has no member named 'do_ioctl'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:668: error: 'struct net_device' has no member named 'get_stats'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:669: error: 'struct net_device' has no member named 'set_mac_address'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:670: error: 'struct net_device' has no member named 'change_mtu'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_detach':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:934: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:979: error: 'struct net_device' has no member named 'stop'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_vap_create':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:988: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1058: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_vap_delete':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1211: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_suspend':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1313: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_resume':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1322: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_intr':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1615: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1806: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_init':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1849: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_stop_locked':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:1969: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_stop':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:2033: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_reset':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:2137: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_tx_startraw':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:2290: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_hardstart':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:2505: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_mgtstart':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:2821: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_key_alloc':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3183: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_key_delete':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3244: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_key_set':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3320: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_key_update_begin':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3335: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_key_update_end':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3356: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_mode_init':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3444: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_updateslot':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3495: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3525: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3573: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:3716: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:4308: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_node_alloc':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:4760: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_node_cleanup':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:4795: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_node_free':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:4849: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_rx_capture':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:5344: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_tx_capture':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:5377: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_recv_mgmt':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:5442: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_rx_tasklet':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:5514: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_grppoll_start':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:5953: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_grppoll_stop':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:6166: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_wme_update':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:6381: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_uapsd_flush':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:6400: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_tx_start':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:6595: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7419: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7440: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_tx_tasklet':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7475: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_tx_timeout':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7498: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_calibrate':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7855: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_scan_start':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7921: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_scan_end':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7941: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_set_channel':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7959: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_set_coverageclass':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7975: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_mhz2ieee':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:7985: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_newstate':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:8000: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_setup_stationkey':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:8389: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_newassoc':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:8549: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_getchannels':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:8580: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_xr_rate_setup':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:8750: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_setup_subrates':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:8779: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_rate_setup':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:8822: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_getstats':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9059: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_set_mac_address':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9082: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_change_mtu':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9114: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_ioctl':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9201: error: 'struct net_device' has no member named 'priv'
cc1: warnings being treated as errors
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_sysctl_halparam':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9286: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9286: error: too many arguments to function 'proc_dointvec'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9464: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9464: error: too many arguments to function 'proc_dointvec'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: At top level:
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9479: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9484: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9489: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9494: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9499: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9504: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9509: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9515: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9521: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9526: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9531: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9536: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9541: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9546: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9552: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9557: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9563: error: initialization from incompatible pointer type
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_announce':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9653: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c: In function 'ath_rcv_dev_event':
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9797: error: 'struct net_device' has no member named 'priv'
/usr/src/madwifi-0.9.3.2/ath/if_ath.c:9799: error: 'struct net_device' has no member named 'open'
make[3]: *** [/usr/src/madwifi-0.9.3.2/ath/if_ath.o] Error 1
make[2]: *** [/usr/src/madwifi-0.9.3.2/ath] Error 2
make[1]: *** [_module_/usr/src/madwifi-0.9.3.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2


Any ideas?

---

### Post by coffeecat on 2010-09-28
@diebodie, you say you have...

> **diebodie said:**
> an old WG311T netgear 802.11g pci card.

... with this chipset: 


> **diebodie said:**
> ```
01:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)                      
```

But at this community page (if you scroll down a bit)...

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

It says the WD311T has the AR5212 chip, whereas it's the WPN311v1 which has the AR5001X. Are you sure you've got the model number correct because the chipset number from lspci will be correct, and it's the chipset that matters. You'll probably see that whoever added the entry for the WD311T/AR5212 states both that they are using Madwifi and that it works out of the box. That's a contradiction and, anyway, that entry is old. I'm inclined to take it with a pinch of salt. Also, there's this:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

See the line for DN-7031-A. Although that's a PCMCIA card, that has the AR5001X chip and again "works out of the box".

I know you've said:

> **diebodie said:**
> Though ubuntu 10.4 lets me connect out of the box, speed is crippled.  Loading most webpages takes ~2+ minutes.

... I'm wondering on the basis of others' apparently good experiences with that chipset whether this is not a driver problem, but something else. Do you have any other computers/OSs connecting to your wireless rounter? What's the speed like with ethernet? Let's get those out of the way and see whether there's something else (perhaps IPv6) which is the problem.

---

### Post by diebodie on 2010-09-28
Thats rather odd. On the box and the driver cd it says WG311T but as you mentioned the chipset doesn't add up. After looking in the .inf file of the driver cd I noticed they sometimes referred it as WG311T13. Not sure if thats relevant? 

I'm actually dual-booting xp and ubuntu. It  works flawlessly on xp which is rather unfortunate because the only thing keeping that windows partition on my hard drive is the wifi support. 

I'm gonna try the openSUSE live cd soon, ill post my results.

---

### Post by coffeecat on 2010-09-28
One thing that might be worth excluding is the IPv6 problem. If you have an older router it might not cope with IPv6 addressing. Ubuntu (and most Linux distros) has/have supported IPv6 since the year dot, but XP doesn't. As a diagnostic test it might be worth disabling IPv6 in Firefox. That's not a complete fix but it might tell us something. Do you need help with that?

---

### Post by diebodie on 2010-09-28
Funny enough, openSUSE seems to have done it (sorta). Though it still seems slightly slower than on windows it's now very much usable. Weird thing is though, on windows I got a signal strength of 100%, on Ubuntu 84% and now with SUSE 60%. 

Thanks everyone, especially coffecat. I appreciate your help in this matter.

---

