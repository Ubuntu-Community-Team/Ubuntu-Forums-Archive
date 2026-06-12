---
title: "Wireless not working - Please help"
date: 2012-09-11
forum: Hardware
---

### Post by thrainpa on 2012-09-11
I have a Dell 15r N5110 which uses Intel Centrino Wireless-n 1030.
I am using Ubuntu 12.04.

The problem I am having is that I can successfully connect to my router via the card, but when I try to load up a webpage (say, google) it just doesn't happen and when I check 'connection information'  is says the speed is 1Mb/s .

Can anyone help me fix this?
What other information might you need from me?

P.S. Apparently this laptop is 'approved for ubuntu', I think not. >.>

---

### Post by Carl.Spackler on 2012-09-11
Please post output of:
```
inxi -b
```

and 

```
lsmod
```

---

### Post by thrainpa on 2012-09-11
inxi -b does nothing.

lsmod gives:
```
USER@COMPUTER:~$ lsmod
Module                  Size  Used by
iwlwifi               332525  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
joydev                 17693  0 
bnep                   18281  2 
rfcomm                 47604  12 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
arc4                   12529  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
psmouse                87692  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  18288  2 
serio_raw              13211  0 
bluetooth             180104  23 bnep,rfcomm,btusb
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
mac_hid                13253  0 
wmi                    19256  1 dell_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  473035  3 
drm_kms_helper         46978  1 i915
soundcore              15091  1 snd
drm                   242038  4 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            18248  0 
uas                    18180  0 
usb_storage            49198  1 ums_realtek
r8169                  62099  0
```

However, by disbaling 'n' in iwlwifi I have managed to get it to work.

Is there a way of getting it to work WITH 'n' channel?

---

### Post by Carl.Spackler on 2012-09-11
Strange 'inxi -b' did nothing...

Maybe you can it to work with N. 

Is this i386 or X86_64?

also please post to give us info on the iwlwifi module:

```
modinfo iwlwifi
```

---

### Post by thrainpa on 2012-09-11
X86_64

```
USER@COMPUTER:~$ modinfo iwlwifi
filename:       /lib/modules/3.2.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
srcversion:     FA59DCECC20E2AB6A93E663
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000266bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000066bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000426bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000226bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000026bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004466bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004266bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004066bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004464bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004264bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004064bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004466bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004266bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004066bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004426bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004226bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004026bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001341bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-30-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)

```

and yeah 'inxi -b' gives:
```
USER@COMPUTER:~$ inxi -b
inxi: command not found

```

---

### Post by Carl.Spackler on 2012-09-11
Is this on battery and while plugged in that it slows down with 'N' enabled?

Have you check this out?
[http://ubuntuforums.org/showpost.php?p=11269674&postcount=2](http://ubuntuforums.org/showpost.php?p=11269674&postcount=2)

---

### Post by Carl.Spackler on 2012-09-11
You might also check out Jupiter for laptop power management if the power management ends up being your problem. I have it installed on my laptop and it made a large difference in battery usage as well as overall performance and I know that it has wifi card power management options when used.

---

### Post by bkratz on 2012-09-12
> **thrainpa said:**
> I have a Dell 15r N5110 which uses Intel Centrino Wireless-n 1030.
I am using Ubuntu 12.04.

The problem I am having is that I can successfully connect to my router via the card, but when I try to load up a webpage (say, google) it just doesn't happen and when I check 'connection information'  is says the speed is 1Mb/s .

Can anyone help me fix this?
What other information might you need from me?

P.S. Apparently this laptop is 'approved for ubuntu', I think not. >.>



Sometimes iwlwifi gets confused when it has to deal with "G" and "N" modes at the same time. This will be just temporary (until the next reboot) but try.

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1

```


If it helps return and we will make it permanent.

---

### Post by varunendra on 2012-09-12
What if it's just a minor configuration issue (seems more probable to me) rather than a hardware one, like no DNS or gateway...

To verify that, please post outputs of (while the wifi shows as 'connected'):
```
ifconfig
iwconfig
cat /etc/resolv.conf
route -n
ping -c4 google.com
```

---

