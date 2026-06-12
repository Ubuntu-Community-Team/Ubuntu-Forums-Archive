---
title: "No soundcard detected (Dell E6430)"
date: 2015-09-08
forum: Hardware
---

### Post by martin167 on 2015-09-08
Dear all,

I have tried some of the known solutions for this problem, and now need a bit more personal help.

I have no sound, soundcard is not detected at all.
Previously it worked intermittently. Troubles started when motherboard was replaced a couple of days ago (due to Ethernet problems). Then I reinstalled alsa and it worked after reboot (could have been unrelated). Thereafter it sometimes worked and sometimes didn't. Linux on live USB also shows "dummy output".

I need help how to know if it is a hardware issue before sending it to repairs


alsa-info [http://www.alsa-project.org/db/?f=505cff5beeda83345a6563d4fb3bacb3a8c43f27](http://www.alsa-project.org/db/?f=505cff5beeda83345a6563d4fb3bacb3a8c43f27)


```
martin@laiuskraad:~$ sudo aplay -l
aplay: device_list:268: no soundcards found...
```

```
lspci -v | grep -A7 -i "audio"
```
returns nothing

```
martin@laiuskraad:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108GLM [NVS 5200M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
0c:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)
```


```
martin@laiuskraad:~$ grep "snd-" /etc/modprobe.d/*
/etc/modprobe.d/alsa-base.conf:install sound-slot-0 /sbin/modprobe snd-card-0
/etc/modprobe.d/alsa-base.conf:install sound-slot-1 /sbin/modprobe snd-card-1
/etc/modprobe.d/alsa-base.conf:install sound-slot-2 /sbin/modprobe snd-card-2
/etc/modprobe.d/alsa-base.conf:install sound-slot-3 /sbin/modprobe snd-card-3
/etc/modprobe.d/alsa-base.conf:install sound-slot-4 /sbin/modprobe snd-card-4
/etc/modprobe.d/alsa-base.conf:install sound-slot-5 /sbin/modprobe snd-card-5
/etc/modprobe.d/alsa-base.conf:install sound-slot-6 /sbin/modprobe snd-card-6
/etc/modprobe.d/alsa-base.conf:install sound-slot-7 /sbin/modprobe snd-card-7
/etc/modprobe.d/alsa-base.conf:install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
/etc/modprobe.d/alsa-base.conf:install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
/etc/modprobe.d/alsa-base.conf:install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-intel8x0m index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-caiaq index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-ua101 index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-us122l index=-2
/etc/modprobe.d/alsa-base.conf:options snd-usb-usx2y index=-2
/etc/modprobe.d/alsa-base.conf:# Ubuntu #62691, enable MPU for snd-cmipci
/etc/modprobe.d/alsa-base.conf:options snd-cmipci mpu_port=0x330 fm_port=0x388
/etc/modprobe.d/alsa-base.conf:# Keep snd-pcsp from being loaded as first soundcard
/etc/modprobe.d/alsa-base.conf:options snd-pcsp index=-2
/etc/modprobe.d/alsa-base.conf:# Keep snd-usb-audio from beeing loaded as first soundcard
/etc/modprobe.d/alsa-base.conf:options snd-usb-audio index=-2
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-intel8x0m
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem

```


```
lsmod | grep snd
``` is empty

I've reinstalled alsa-base alsa-tools alsa-utils pulseaudio linux-sound-base padevchooser pavucontrol pulseaudio-utils libasound2 linux-image-3.13.0-63-generic linux-image-extra-3.13.0-63-generic 
and more.

All the best

---

### Post by martin167 on 2015-09-08
Some changes happened. In the meantime I've installed VMware player, windows XP, and pulseaudio-module-zeroconf pulseaudio-module-x11 paprefs
VMware kind of detected ALSA sound card, but windows was unable to play on it. I suspect it came online for a while and then died again.

now I still have Dummy Output, but additionally

```
martin@laiuskraad:~$ sudo lspci -v | grep -A10 -i "audio"
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: Dell Device 0534
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f7e30000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Root Complex Link
        Kernel driver in use: snd_hda_intel

```


```
martin@laiuskraad:~$ lsmod | grep snd                                                                                                                                                                                                        
snd_hda_intel          31032  0 
snd_hda_codec         136263  1 snd_hda_intel
snd_hda_core           56618  2 snd_hda_codec,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_page_alloc         18710  3 snd_pcm,snd_hda_intel,snd_hda_core
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69322  9 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
```

updated alsa-info at [URL="http://www.alsa-project.org/db/?f=24cfa03813a7f2fd5d965d6bfd05ea09942a0b88"]http://www.alsa-project.org/db/?f=24cfa03813a7f2fd5d965d6bfd05ea09942a0b88
[/URL]
[SOLVED] due to the problem being hardware (motherboard)

---

### Post by Yellow Pasque on 2015-09-08
> snd_hda_intel: model=generic

Did you add this before or after you replaced the mobo?

---

### Post by martin167 on 2015-09-09
After.

The motherboard was replaced in warranty, so I have no idea if they might have botched the job up or not. I didn't install a new OS, but used the old drive as it was.

---

### Post by Yellow Pasque on 2015-09-09
Either way, I wold get rid of the model=generic line and get a new link to alsa info when booting without it.
[http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/](http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/)

---

### Post by martin167 on 2015-09-09
OK, its taken out now. The soundcard hasn't come online since the last alsa-info (so everything is according to the first alsa-info). Cannot get a beep out of it, looks like a hardware issue?

---

### Post by martin167 on 2015-09-11
Update: Got new automatic update with kernel 3.13.0-64 (thanks!), but hadn't rebooted yet, so it hasn't taken effect. I was fiddling with my virtual machines again when I noticed that ALSA: HDA Intel PCH was available. And the soundcard was up (on kubuntu which is native OS) and played audio and everything. Anyway, I expect this not to last, so yet another alsa-info for future reference: [http://www.alsa-project.org/db/?f=4fcf8f30330be4ef407bc6eb4b02116ae4c4d07e](http://www.alsa-project.org/db/?f=4fcf8f30330be4ef407bc6eb4b02116ae4c4d07e)

---

