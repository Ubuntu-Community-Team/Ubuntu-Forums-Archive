---
title: "Soundcard detection problem"
date: 2010-03-10
forum: Hardware
---

### Post by Nuckinfuts on 2010-03-10
Laptop: ZT Affinity PC (never heard of it? neither had I)

on 9.10 and on 10.04 alpha, the soundcard fails to be properly detected, sound works fine on 8.04, 8.10, and 9.04 out of the box

Details:
[http://www.alsa-project.org/db/?f=14c81040539d08331355ac834fd4c87fdf04aaf8](http://www.alsa-project.org/db/?f=14c81040539d08331355ac834fd4c87fdf04aaf8)

From 9.10:
```

nuckin@nuckin-laptop:~$ sudo aplay -l
aplay: device_list:223: no soundcards found...

```
```

nuckin@nuckin-laptop:~$ find /lib/modules/`uname -r` | grep snd
/lib/modules/2.6.31-20-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/oss/snd-pcm-oss.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/oss/snd-mixer-oss.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/seq/snd-seq-device.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/seq/snd-seq.ko
/lib/modules/2.6.31-20-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.31-20-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.31-20-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.31-20-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.31-20-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.31-20-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.31-20-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko

```

**From 8.04 Installation**
```
nuckin@nuckin-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: LSI Si3054
```

---

### Post by khelben1979 on 2010-03-11
I think the main problem lies with the Linux kernel and that the sound module for your sound chip don't get initilized upon reboot.

If you manage to find which sound module to initialize for your specific sound chip, you have solved the problem. You then use the insmod or modprobe command.

To my own experience, by downloading ALSA source packages from the ALSA project page, you can have the sound working by configuring up the source and installing, but it's not recommended for newbies. You can check [this thread]("http://ubuntuforums.org/showthread.php?t=455147&highlight=HowTo+HP+DV2000+compile+alsa+resolve+issues+(mic,+jack,+AC-power,auto+mute)") if you're interested.

---

### Post by Nuckinfuts on 2010-03-11
I've done custom kernels and compiling from source before but I would like to avoid that as much as possible since I don't have the time currently to be manually updating custom compiled code.

I've tried "sudo modprobe snd-hda-codec-realtek" which did nothing, and I've been going down the list of ALC883 options to try in /etc/modprobe.d/alsa-base.conf to try and get it working, any other configuration ideas would be greatly appreciated.

---

### Post by Nuckinfuts on 2010-03-18
anyone have any more ideas?  Would alsa source really be a worthy try since the source isn't any newer than the karmic packages?

---

### Post by Yellow Pasque on 2010-03-19
Did you try:
```
sudo modprobe -v snd-hda-intel
```
Look at the end of dmesg after you do that if it doesn't work:
```
dmesg | tail -n 20
```

To use the most recent ALSA release: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by Nuckinfuts on 2010-03-19
Thank you for the reply, I tried your modprobe and nothing happened:

```
nuckin@nuckin-laptop:~$ sudo modprobe -v snd-hda-intel
[sudo] password for nuckin: 
nuckin@nuckin-laptop:~$ dmesg | tail -n 20
[   42.413970] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   42.413977] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
[   42.413980] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
[   42.413983] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
[   42.413988] cfg80211: Current regulatory domain updated by AP to: US
[   42.413990] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   42.413993] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   53.002527] wlan0: no IPv6 routers present
[   83.510012] Clocksource tsc unstable (delta = -111173724 ns)
[  112.280642] wlan0: authenticate with AP 00:17:0f:e7:bd:42
[  112.282392] wlan0: authenticated
[  112.282399] wlan0: associate with AP 00:17:0f:e7:bd:42
[  112.287393] wlan0: RX ReassocResp from 00:17:0f:e7:bd:42 (capab=0x421 status=0 aid=80)
[  112.287400] wlan0: associated
[  172.288624] wlan0: authenticate with AP 00:17:0f:e5:ec:e2
[  172.480060] wlan0: authenticate with AP 00:17:0f:e5:ec:e2
[  172.483148] wlan0: authenticated
[  172.483155] wlan0: associate with AP 00:17:0f:e5:ec:e2
[  172.491521] wlan0: RX ReassocResp from 00:17:0f:e5:ec:e2 (capab=0x421 status=0 aid=112)
[  172.491528] wlan0: associated
nuckin@nuckin-laptop:~$ 

```

I don't see any soundcard information in that.

---

