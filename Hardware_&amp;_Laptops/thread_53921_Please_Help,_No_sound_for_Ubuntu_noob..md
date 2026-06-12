---
title: "Please Help, No sound for Ubuntu noob."
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by acidtrip on 2005-08-02
I've run the ALSA sound debug script, However as I'm a total noob to the linux world I only have a very vague idea on what the problem is (I assume it's probably something very simple) Anyway, If anyone could let me know if the results look good or bad that would be appreciated very much! The problem could be turned down volume controls somewhere or an incorrectly selected device or module,etc, so if you think it could be, could you let me know where to change it.

Thanks alot!

[b]ALSA Audio Debug v0.0.9 - Tue Aug  2 22:37:29 BST 2005
[http://alsa.opensrc.org/?page=aadebug](http://alsa.opensrc.org/?page=aadebug)

Kernel ----------------------------------------------------
Linux wes 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  11 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Jun 24 2005 for kernel 2.6.10-5-386.
0 [V8237          ]: VIA8237 - VIA 8237
                     VIA 8237 with CMI9761 at 0xc000, irq 22
  0: [0- 0]: ctl
 17: [0- 1]: digital audio playback
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: VIA 8237 : VIA 8237 : playback 4 : capture 1
00-01: VIA 8237 : VIA 8237 : playback 1 : capture 1

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D1p  timer

CPU -------------------------------------------------------
model name      : AMD Athlon(tm) XP 3200+
cpu MHz         : 2198.607

RAM -------------------------------------------------------
MemTotal:       906660 kB
SwapTotal:      369452 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
[/b]

---

