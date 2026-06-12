---
title: "Sound card problem"
date: 2009-12-07
forum: Hardware
---

### Post by mahadevan on 2009-12-07
I cannot get my Yamaha PCI sound card to detect.

[root@localhost mahadevan]# lspci | grep audio
06:05.0 Multimedia audio controller: Yamaha Corporation DS1L Audio
[root@localhost mahadevan]# aplay -l
aplay: device_list:223: no soundcards found...


When i try to setup my sound driver using

alsaconf

I get this output



Loading driver...
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
Starting sound driver: snd-ymfpci WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
done
Starting sound driver: snd-ymfpci WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
done
/usr/sbin/alsactl: load_state:1608: No soundcards found...
Setting default volumes...

---

### Post by mahadevan on 2009-12-07
I get the following output

[root@localhost mahadevan]# modprobe snd-ymfpci
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.


[root@localhost mahadevan]# lsmod
Module                  Size  Used by
pppoe                   9808  2 
pppox                   2668  1 pppoe
ppp_generic            20856  6 pppoe,pppox
slhc                    4840  1 ppp_generic
fuse                   52712  2 
sunrpc                158388  1 
ip6t_REJECT             4620  2 
nf_conntrack_ipv6      17548  2 
ip6table_filter         3168  1 
ip6_tables             11144  1 ip6table_filter
ipv6                  239428  30 ip6t_REJECT,nf_conntrack_ipv6
cpufreq_ondemand        6160  2 
acpi_cpufreq            8848  0 
dm_multipath           14472  0 
uinput                  6852  0 
[B]snd_ymfpci             29768  0 
gameport                9672  1 snd_ymfpci
snd_ac97_codec         91948  1 snd_ymfpci[/B]
ac97_bus                1616  1 snd_ac97_codec
snd_seq                44452  0 
snd_pcm                61088  2 snd_ymfpci,snd_ac97_codec
snd_opl3_lib            9052  1 snd_ymfpci
snd_timer              17608  4 snd_ymfpci,snd_seq,snd_pcm,snd_opl3_lib
snd_hwdep               6976  1 snd_opl3_lib
snd_page_alloc          8132  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         6448  1 snd_ymfpci
snd_rawmidi            18452  1 snd_mpu401_uart
iTCO_wdt               10444  0 
iTCO_vendor_support     2812  1 iTCO_wdt
ppdev                   8200  0 
i2c_i801               10284  0 
parport_pc             22748  0 
r8169                  28452  0 
snd_seq_device          6352  3 snd_seq,snd_opl3_lib,snd_rawmidi
snd                    46416  10 **snd_ymfpci,snd_ac97_codec,snd_seq,snd_pcm,snd_opl3  _lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmi  di,snd_seq_device**
soundcore               5672  1 snd
mii                     4120  1 r8169
parport                29300  2 ppdev,parport_pc
nouveau               499356  2 
ttm                    34264  1 nouveau
drm_kms_helper         22688  1 nouveau
drm                   135064  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            4820  1 nouveau
i2c_core               23120  4 i2c_i801,nouveau,drm,i2c_algo_bit

$ dmesg .. only partial output.

Yamaha DS-1 PCI 0000:06:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Yamaha DS-1 PCI 0000:06:05.0: firmware: requesting yamaha/ds1_dsp.fw
Yamaha DS-1 PCI 0000:06:05.0: firmware: requesting yamaha/ds1_ctrl.fw
Yamaha DS-1 PCI 0000:06:05.0: PCI INT A disabled
Yamaha DS-1 PCI: probe of 0000:06:05.0 failed with error -16


Does this help?

---

