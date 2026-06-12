---
title: "No sound and I've tried almost everything"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by morticul on 2006-10-31
Hi all.

I can run xmms, play a song, and I see the little spectrogram dancing but I hear absoutely no sound. Every control of alsamixer is at 100% and unmuted. In win-xp, I can hear the sounds so it is not a hardware problem.

I wen trough both of those howto and still no sound :
1) [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
2) [http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

the output of aadebug is :

```


$ ./aadebug

ALSA Audio Debug v0.1.0 - Tue Oct 31 20:12:28 EST 2006
http://alsa.opensrc.org/index.php?page=aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux dev3 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_intel8x0           33692  2
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with ALC202 at 0xfeaffc00, irq 201
 20: [0- 4]: digital audio playback
 27: [0- 3]: digital audio capture
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2c  pcmC0D3c  pcmC0D4p  timer

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 2.66GHz
cpu MHz         : 2665.729

RAM -------------------------------------------------------
MemTotal:      1296064 kB
SwapTotal:     1132540 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation E7205 Memory Controller Hub (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)



```

I've switched from ubuntu to kubuntu via apt-get. I feal that it might be related, but I don't know if the sound was working before. One weird thing is that I was able to completely remove the alsa driver and select alsa driver from kcontrol/sound_&_multimedia/sound_system/hardware and still getting the same behaviour of xmms throwing no error and no sound. 

please help me!!! I just don't know what to do anymore.

---

### Post by Sef on 2006-11-01
This is how I get sound:

> Here's how I got sound on my via82xx:

I commented out 3 lines and changed the 2 to 0 in the 82viaxx line. To comment out a line, put a # before it. I commented out one line above 'options snd-via82xx-modem index=-0' and the two lines below.

Code:

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; } # Prevent abnormal drivers from grabbing index 0 options snd-bt87x index=-2 options snd-atiixp-modem index=-2 #options snd-intel8x0m index=-2 options snd-via82xx-modem index=-0 #options snd-usb-audio index=-2 #options snd-usb-usx2y index=-2

Save and exit.

Then System > Preferences > Sound and changed the bottom one to

Then changed sound capture to Via 82C686A/B 50rev.

If you don't have any sound after that, reboot and you should have sound.

[http://www.ubuntuforums.org/showthread.php?t=289388&highlight=sound]("http://www.ubuntuforums.org/showthread.php?t=289388&highlight=sound")

---

### Post by morticul on 2006-11-01
Ok I found the problem !!!

I have to MUTE jack det (jack detect [ off ]) in alsamixer.
How come I have to MUTE something in order to hear it !!! ;)

---

