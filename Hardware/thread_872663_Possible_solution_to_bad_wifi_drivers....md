---
title: "Possible solution to bad wifi drivers..."
date: 2008-07-28
forum: Hardware
---

### Post by Kingstrum on 2008-07-28
**FINALLY!**
After much searching and gnashing of teeth, it looks like I may have stumbled upon a solution to the spastic, intermittent speeds on various wifi cards (specifically, in my case, Intel PRO/Wireless 3945ABG). Since I just discovered my T60 Thinkpad with Core 2 Duo was "AMD64-capable" and was switching out from 32-bit, figured it couldn't hurt to try from a fresh install (so, this means it appears work for both system types).

_[http://linuxwireless.org]("http://linuxwireless.org")_

A good start on doing for wifi what CUPS did for printing. The site indicates that their drivers work for the following cards:

adm8211
at76_usb
ath5k
b43
b43legacy
iwl3945
iwl4965
ipw2100
ipw2200
ub8xxx
libertas_cs
p54_pci
p54_usb
rndis_wlan
rt2400pci
rt2400pci
rt2500pci
rt2500usb
rt61pci
rt73usb
rtl8180
rtl8187
zd1211rw

Go _[here]("http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/")_ and grab the most recent tarball (for me, 07-27 was most recent).

Next, follow the instructions _[here]("http://linuxwireless.org/en/users/Download")_:
> 
***Building and installing***

*Extract:*

Extract the content of the package:

```
tar jxvf compat-wireless-$(date -I).tar.bz2
```

*Build:*

Build the latest Linux wireless subsystem:

```
cd compat-wireless-$(date -I)
make
```

*Install:*

We use the updates/ directory so your distribution's drivers are left intact.

```
sudo make install
```

*Uninstall:*

This nukes our changes to updates/ so you can go back to using your distribution's supported drivers.

```
sudo make uninstall
```

*Unload:*

Since you might be replacing your old mac80211 drivers you should first try to unload all existing mac80211 and related drivers. Note also that broadcom, zydas, and atheros devices have old legacy drivers which you need to be sure are removed first. We provide a mechanism to unload all old and legacy drivers first so you should run to be sure:

```
sudo make unload
```

*Load:*

If you know what module you need you can simply load the module using modprobe. If you simply are not sure you can use:

```
sudo make load
```

Note that this will run make unload first, just in case you forgot. This unloads your old wireless subsystem drivers and loads the new shiny ones. For example if ipw3945 and its proprietary daemon are found it'll be stopped and the module unloaded and then iwl3945 will be loaded. If you are simply upgrading a mac80211 driver this will unload the old one and the old mac80211 drivers and load the new ones. 


I installed the tarball into /home/foo/bin [personal bin directories are a **must** for long-term Linux lovin'], uncompressed it, and finished the make magic. After doing the unload step it indicated > Unloading iwlwifi_mac80211...
FATAL: Module iwlwifi_mac80211 is in use.
Unloading iwl3945...
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1 so I did ```
sudo modprobe -r iwlwifi_mac80211
sudo modprobe -r cfg80211

```to pluck them out myself. Upon completion of the load step, Network Manager* came back up and logged into my home wifi net without further issue.

Now previously I was experiencing dropouts or fade over (seemingly) random time & load intervals (sometimes it would go for 20+ minutes under varying loads before cutting a download from 1.8Mb/s to <200kb/s without any other load on the network; other times it would start off dragging). As a test of this new driver I copied a 3.9GB file while watching a streaming movie (*_[Gunner Palace]("http://www.imdb.com/title/tt0424129/")_*...not big on war movies, but I recommend it if you're curious about Iraq) and sustained an average of 1.8Mb/s for over 60+ minutes without a single major slowdown (it does vasilate a bit in the beginning, but once it gets set, it flies).

Haven't rebooted yet, but per the instructions above, the install goes into an updates/ folder that is persistant and can be undone with the 'sudo make uninstall' command inside the uncompressed folder (told you personal bin/ folders rock, fool!).

With any luck this should be a simple, straightforward fix for all my long-suffering peeps who've had serious grinder issues with the wireless thing. I'll post back again in a few days after I've abused it some more and am happy this is a more permanent solution.

I **strongly** encourage the Ubuntu team to look at getting these updates into the next patch cycle ASAP!

Must sleep now...

[*Side note: yeah, yeah, I know Network Manager gets a lot of grief from everybody -- including blame as the root cause of all the wifi slowdowns/failures -- but personally, it's always "just worked" and I'm not fond of Wicd or any of the other options out there. Plus, the OpenVPN support is hard to beat.]

Kingstrum

"There's no prob with 'BOB'!"

---

### Post by My Name on 2008-07-29
I get this error when make install
```
Your old wireless subsystem modules were left intact:

/lib/modules/2.6.24-19-rt/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-rt/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.24-19-rt/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/ssb/ssb.ko
/lib/modules/2.6.24-19-rt/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-rt/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.24-19-rt/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.24-19-rt/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/libertas/libertas_cs.ko
/lib/modules/2.6.24-19-rt/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/p54pci.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/p54usb.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/usb/usbnet.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/usb/rndis_host.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/rtl8187.ko
/lib/modules/2.6.24-19-rt/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.24-19-rt/kernel/net/ieee80211/softmac/ieee80211softmac.ko

make -C /lib/modules/2.6.24-19-rt/build M=/home/iain/Desktop/compat-wireless-2008-07-28 modules
make: *** /lib/modules/2.6.24-19-rt/build: No such file or directory. Stop.
make: *** [modules] Error 2

```

any ideas?

---

### Post by hobojoe789 on 2008-07-31
Kingstrum I also have an IPW 3945ABG but it does not seem to work for me with compat-wireless.  What kernel build are you using?

---

### Post by marcopolo1981 on 2008-08-01
Thanks Very much. Worked a charm.

Mark

---

### Post by Kingstrum on 2008-08-06
> **My Name said:**
> 
<snip>
```

make -C /lib/modules/2.6.24-19-rt/build M=/home/iain/Desktop/compat-wireless-2008-07-28 modules
make: *** /lib/modules/2.6.24-19-rt/build: No such file or directory. Stop.
make: *** [modules] Error 2

```

Hmmm...not sure about this one. I'll do some more research. This seems to indicate you're using the "real-time" kernel, correct? Maybe post some additional info (machine type, CPU, card type, etc.)


> **hobojoe789 said:**
> Kingstrum I also have an IPW 3945ABG but it does not seem to work for me with compat-wireless.  What kernel build are you using?

I'm using "2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64" on my T60 Thinkpad with Core 2 Duo, using AMD64 architecture.

Further testing through the week has shown these drivers to be rock solid and able to run at full speed for sustained periods of time without issue. Basically these are what the default drivers should have been (for which I mostly blame Intel, as I suspect the kinks just weren't considered important by the time Hardy released.)

Let me get back to you on the other bits.

Kingstrum

"Et in Arcadia ego...do you?"

---

