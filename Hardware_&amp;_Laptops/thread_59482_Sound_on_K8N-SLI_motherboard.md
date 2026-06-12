---
title: "Sound on K8N-SLI motherboard"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by D@ffy on 2005-08-24
Hellow,

I have a pretty frustrating sound problem. No matter what guide on this forum I follow, it won't work. My system is an MSI K8N-SLI motherboard with SB Live! 24 bit soundcard on-board and an AMD Ahtlon64 3000+ processor. MSI doesn't seem to deliver any drivers for Linux as far as I noticed. My OS is Ubuntu 5.04 AMD64 version on the 2.6.10-5 kernel.

Here's a description:
After installation of Ubuntu, "lsmod|grep snd" gives me nothing and in lspci I see thqt my sound card is recognized as an SB AudigyLS, not right of course. When I try to test the sound system in System -> Preferences -> Select sound system, I always get an error that building a test pipeline has failed, no matter which one I choose. (ALSA, OSS, ESD) When I try to run alsamixer I get "function snd_ctl_open failed for default: No such file or directory".
So I followed the guide in the first post here: [http://ubuntuforums.org/showthread.php?t=19307&highlight=ca0106](http://ubuntuforums.org/showthread.php?t=19307&highlight=ca0106)
All went well, no errors that I noticed of, but still no sound, still testing pipeline errors, still the same alsamixer error. Totem media player also won't start (as before) because it gives me the error "ALSA device "default" does not exist".

So now the driver is installed but still no sound, here are some outputs that may be relevant:
lsmod | grep snd:
```

snd_ca0106             30532  0
snd_ac97_codec         80720  1 snd_ca0106
snd_pcm_oss            63392  0
snd_mixer_oss          20864  1 snd_pcm_oss
snd_pcm               102796  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              26376  1 snd_pcm
snd                    66056  6 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11168  1 snd
snd_page_alloc         11400  2 snd_ca0106,snd_pcm

```
(this one has changed after installation of the driver, it was empty before)

lspci:
```

0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:01:0d.0 Multimedia audio controller: Creative Labs SB Audigy LS
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00f9 (rev a2)

```
(still the same, as you see the sound card is detected wrongly)

ls -al /lib/modules/2.6.10-5-amd64-generic/kernel/sound/pci:
```

drwxr-xr-x  15 root root  4096 2005-08-24 01:49 .
drwxr-xr-x  10 root root  4096 2005-08-24 01:49 ..
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 ac97
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 ali5451
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 au88x0
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 cs46xx
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 emu10k1
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 ice1712
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 korg1212
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 mixart
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 nm256
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 rme9652
-rw-r--r--   1 root root 20234 2005-04-05 14:29 snd-als4000.ko
-rw-r--r--   1 root root 28863 2005-04-05 14:29 snd-atiixp.ko
-rw-r--r--   1 root root 24515 2005-04-05 14:29 snd-atiixp-modem.ko
-rw-r--r--   1 root root 30849 2005-04-05 14:29 snd-azt3328.ko
-rw-r--r--   1 root root 20213 2005-04-05 14:29 snd-bt87x.ko
-rw-r--r--   1 root root 47958 2005-04-05 14:29 snd-cmipci.ko
-rw-r--r--   1 root root 31242 2005-04-05 14:29 snd-cs4281.ko
-rw-r--r--   1 root root 26843 2005-04-05 14:29 snd-ens1370.ko
-rw-r--r--   1 root root 33453 2005-04-05 14:29 snd-ens1371.ko
-rw-r--r--   1 root root 33166 2005-04-05 14:29 snd-es1938.ko
-rw-r--r--   1 root root 39544 2005-04-05 14:29 snd-es1968.ko
-rw-r--r--   1 root root 28004 2005-04-05 14:29 snd-fm801.ko
-rw-r--r--   1 root root 48577 2005-04-05 14:29 snd-intel8x0.ko
-rw-r--r--   1 root root 28739 2005-04-05 14:29 snd-intel8x0m.ko
-rw-r--r--   1 root root 31578 2005-04-05 14:29 snd-maestro3.ko
-rw-r--r--   1 root root 34098 2005-04-05 14:29 snd-rme32.ko
-rw-r--r--   1 root root 35045 2005-04-05 14:29 snd-rme96.ko
-rw-r--r--   1 root root 34551 2005-04-05 14:29 snd-sonicvibes.ko
-rw-r--r--   1 root root 41100 2005-04-05 14:29 snd-via82xx.ko
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 trident
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 vx222
drwxr-xr-x   2 root root  4096 2005-08-24 01:49 ymfpci

```
(as you see no ca0106, but I installed the driver???)

If anyone has suggestions for this problem, they're welcome. I have the impression I'm not the only one here who doens't get this combination of ca0106 on-board and amd64 to work...

Thx a lot,
D@ffy

---

### Post by D@ffy on 2005-08-25
Noone who can give a possible solution? Or somethin I can do to find what the problem might be? Can't do anything with this distro if my sound doens't work... :( Maybe I should install the i386, but if possible I'd rather not do that.

---

