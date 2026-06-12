---
title: "No networking with 3.19, all fine with 3.16"
date: 2015-05-24
forum: Hardware
---

### Post by patrick-koppenburg on 2015-05-24
Dear all,

After the upgrade to 15.04 I lost networking with the default kernel 3.19. I show a tick at enable networking but I am otherwise offline and get no wireless or ethernet options. All is fine with 3.16. lspci -v says 

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 197d
	Flags: bus master, fast devsel, latency 0, IRQ 7
	I/O ports at 5000 [size=256]
	Memory at d3600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

while 3.16 has

07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Device 197d
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at 5000 [size=256]
	Memory at d3600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8188ee

So some driver problem. But what should I do? Thanks

---

### Post by tokyobadger on 2015-05-24
When you boot with 3.19 what do you get from
```
lsmod | grep rtl8188ee
```

---

### Post by patrick-koppenburg on 2015-05-25
Nothing with 3.19. 

With 3.16 I get 
[21:52:01] 192.168.1.101:~/ > lsmod | grep rtl8188ee
rtl8188ee              85133  0 
rtl_pci                26674  1 rtl8188ee
rtlwifi                64237  2 rtl_pci,rtl8188ee
mac80211              660592  3 rtl_pci,rtlwifi,rtl8188ee

Something must be not installed properly. I see

locate rtl8188ee.ko
/lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.14.1-031401-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
/lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko

So no 3.19. How do I get this module? Thanks

---

### Post by tokyobadger on 2015-05-30
Well it's a bit of a hack and not guaranteed to work but you could create a folder
```
/lib/modules/3.19.0-XX-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/
```
where XX is the version of your 3.19 kernel.
Then copy the module from the 3.16 folder into the 3.19 folder.
Next try
```
sudo modprobe rtl8188ee debug=3 swenc=1 ips=0 fwlps=0 disable_watchdog=1
```
All of this will need to be done with "sudo"

---

### Post by jeremy31 on 2015-05-30
You might want to try ```
sudo apt-get install --reinstall linux-image-$(uname -r)
```

As I don't think the 3.16 kernel modules will work in 3.19

---

### Post by tokyobadger on 2015-05-30
> **jeremy31 said:**
> You might want to try ```
sudo apt-get install --reinstall linux-image-$(uname -r)
```

As I don't think the 3.16 kernel modules will work in 3.19
Agreed. This should be the first option. Might also be worth seeing if the linux-headers and linux-firmware packages are up to date.

The "workaround" suggested above has worked for me in the past (not 100%) eg USB webcam but we're talking at least 5 years or more ago and the kernel has undoubtedly become more complex/refined in that time. Nonetheless I'd use it as a last resort.

Out of interest, your 3.14 kernel looks "non-standard"; you said the 3.19 is default - can you give us the version?

**edit**: found another possible workaround to try after jeremy31's suggestion

```
 git clone [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git)
  cd rtlwifi_new
  make
  sudo modprobe -rv rtl8188ee
  sudo make install
  sudo modprobe -v rtl8188ee
```
From a [bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1314434) - posted March 2015 but kernel version not specified

---

### Post by patrick-koppenburg on 2015-05-30
Many thanks for the replies and apologies for not having given the full pedigree of the kernels. The one that works is

Linux toblerone 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:07:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
The one that does not is 3.19.0-15-generic

I tried reinstalling it but that didn't bring the missing modules.

I tried compiling from git (a two-step process as under 3.19 I have no network..). It compiled and installed fine but I get

sudo modprobe -v rtl8188ee 
insmod /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8188ee': Unknown symbol in module, or unknown parameter (see dmesg)


with dmesg:


[  515.953750] rtlwifi: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err 0)
[  515.953755] rtlwifi: Unknown symbol ieee80211_connection_loss (err 0)
[  515.953765] rtlwifi: Unknown symbol ieee80211_start_tx_ba_session (err 0)
[  515.953774] rtlwifi: Unknown symbol ieee80211_rate_control_unregister (err 0)
[  515.953776] rtlwifi: Unknown symbol ieee80211_get_hdrlen_from_skb (err 0)
[  515.953783] rtlwifi: Unknown symbol ieee80211_find_sta (err 0)
[  515.953789] rtlwifi: Unknown symbol wiphy_rfkill_set_hw_state (err 0)
[  515.953796] rtlwifi: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err 0)
[  515.953799] rtlwifi: Unknown symbol wiphy_to_ieee80211_hw (err 0)
[  515.953803] rtlwifi: Unknown symbol wiphy_rfkill_stop_polling (err 0)
[  515.953807] rtlwifi: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  515.953811] rtlwifi: Unknown symbol ieee80211_rate_control_register (err 0)
[  515.953825] rtlwifi: Unknown symbol wiphy_rfkill_start_polling (err 0)
[  515.953829] rtlwifi: Unknown symbol freq_reg_info (err 0)
[  515.953834] rtlwifi: Unknown symbol rate_control_send_low (err 0)
[  515.953838] rtlwifi: Unknown symbol ieee80211_resume_disconnect (err 0)
[  515.953848] rtlwifi: Unknown symbol ieee80211_rx_irqsafe (err 0)
[  545.190786] rtlwifi: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err 0)
[  545.190798] rtlwifi: Unknown symbol ieee80211_connection_loss (err 0)
[  545.190821] rtlwifi: Unknown symbol ieee80211_start_tx_ba_session (err 0)
[  545.190839] rtlwifi: Unknown symbol ieee80211_rate_control_unregister (err 0)
[  545.190846] rtlwifi: Unknown symbol ieee80211_get_hdrlen_from_skb (err 0)
[  545.190861] rtlwifi: Unknown symbol ieee80211_find_sta (err 0)
[  545.190874] rtlwifi: Unknown symbol wiphy_rfkill_set_hw_state (err 0)
[  545.190890] rtlwifi: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err 0)
[  545.190898] rtlwifi: Unknown symbol wiphy_to_ieee80211_hw (err 0)
[  545.190907] rtlwifi: Unknown symbol wiphy_rfkill_stop_polling (err 0)
[  545.190916] rtlwifi: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  545.190927] rtlwifi: Unknown symbol ieee80211_rate_control_register (err 0)
[  545.190959] rtlwifi: Unknown symbol wiphy_rfkill_start_polling (err 0)
[  545.190968] rtlwifi: Unknown symbol freq_reg_info (err 0)
[  545.190980] rtlwifi: Unknown symbol rate_control_send_low (err 0)
[  545.190990] rtlwifi: Unknown symbol ieee80211_resume_disconnect (err 0)
[  545.191012] rtlwifi: Unknown symbol ieee80211_rx_irqsafe (err 0)
[  565.950231] rtlwifi: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err 0)
[  565.950240] rtlwifi: Unknown symbol ieee80211_connection_loss (err 0)
[  565.950256] rtlwifi: Unknown symbol ieee80211_start_tx_ba_session (err 0)
[  565.950269] rtlwifi: Unknown symbol ieee80211_rate_control_unregister (err 0)
[  565.950274] rtlwifi: Unknown symbol ieee80211_get_hdrlen_from_skb (err 0)
[  565.950285] rtlwifi: Unknown symbol ieee80211_find_sta (err 0)
[  565.950294] rtlwifi: Unknown symbol wiphy_rfkill_set_hw_state (err 0)
[  565.950306] rtlwifi: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err 0)
[  565.950311] rtlwifi: Unknown symbol wiphy_to_ieee80211_hw (err 0)
[  565.950318] rtlwifi: Unknown symbol wiphy_rfkill_stop_polling (err 0)
[  565.950324] rtlwifi: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  565.950331] rtlwifi: Unknown symbol ieee80211_rate_control_register (err 0)
[  565.950354] rtlwifi: Unknown symbol wiphy_rfkill_start_polling (err 0)
[  565.950361] rtlwifi: Unknown symbol freq_reg_info (err 0)
[  565.950369] rtlwifi: Unknown symbol rate_control_send_low (err 0)
[  565.950377] rtlwifi: Unknown symbol ieee80211_resume_disconnect (err 0)
[  565.950393] rtlwifi: Unknown symbol ieee80211_rx_irqsafe (err 0)
[  569.226213] rtlwifi: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err 0)
[  569.226218] rtlwifi: Unknown symbol ieee80211_connection_loss (err 0)
[  569.226228] rtlwifi: Unknown symbol ieee80211_start_tx_ba_session (err 0)
[  569.226236] rtlwifi: Unknown symbol ieee80211_rate_control_unregister (err 0)
[  569.226239] rtlwifi: Unknown symbol ieee80211_get_hdrlen_from_skb (err 0)
[  569.226246] rtlwifi: Unknown symbol ieee80211_find_sta (err 0)
[  569.226251] rtlwifi: Unknown symbol wiphy_rfkill_set_hw_state (err 0)
[  569.226258] rtlwifi: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err 0)
[  569.226261] rtlwifi: Unknown symbol wiphy_to_ieee80211_hw (err 0)
[  569.226265] rtlwifi: Unknown symbol wiphy_rfkill_stop_polling (err 0)
[  569.226268] rtlwifi: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[  569.226272] rtlwifi: Unknown symbol ieee80211_rate_control_register (err 0)
[  569.226285] rtlwifi: Unknown symbol wiphy_rfkill_start_polling (err 0)
[  569.226289] rtlwifi: Unknown symbol freq_reg_info (err 0)
[  569.226295] rtlwifi: Unknown symbol rate_control_send_low (err 0)
[  569.226299] rtlwifi: Unknown symbol ieee80211_resume_disconnect (err 0)
[  569.226308] rtlwifi: Unknown symbol ieee80211_rx_irqsafe (err 0)

Finally copying the module from 3.16 gets the same result as with the compiled one. Is something new in 3.19 that has not yet been reflected in that driver?

Thanks

---

### Post by dino99 on 2015-05-30
you might get the realtek driver  [http://askubuntu.com/questions/475489/wireless-is-slower-in-ubuntu-with-a-realtek-rtl8188ee-card](http://askubuntu.com/questions/475489/wireless-is-slower-in-ubuntu-with-a-realtek-rtl8188ee-card)

---

### Post by tokyobadger on 2015-05-30
Just a thought - the 3.19.0.15 kernel in 15.04 has been superseded - if I'm not mistaken the latest is 3.19.0.20. Could be worth updating (booting into 3.16.0.24 or using a wired connection from 3.19.0.15) to see if a newer kernel version resolves the issue.

---

### Post by patrick-koppenburg on 2015-06-14
Dear all,

I tried upgrading to 3.19.0.18 without success. I only found 0.20 for 32 bit. But I'll follow up for sure.

I also tried the realtek driver but get

make -C /lib/modules/3.19.0-18-generic/build M=/home/pkoppenb/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 modules
make[1]: Entering directory '/usr/src/linux-headers-3.19.0-18-generic'
  CC [M]  /home/pkoppenb/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o
scripts/Makefile.build:257: recipe for target '/home/pkoppenb/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/base.o' failed
Makefile:1394: recipe for target '_module_/home/pkoppenb/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013' failed
make[1]: Leaving directory '/usr/src/linux-headers-3.19.0-18-generic'
Makefile:27: recipe for target 'all' failed

... argh see now this is the stdout, not stderr. Anyway, I saw something similar when I tried to compile a card reader driver from realtek a month ago. There seem to be quite some changes in kernel headers.

---

