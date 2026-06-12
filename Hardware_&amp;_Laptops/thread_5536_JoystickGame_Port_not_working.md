---
title: "Joystick/Game Port not working"
date: 2004-11-19
forum: Hardware &amp; Laptops
---

### Post by electroglas on 2004-11-19
I am trying use a dictation controller that is wired like a 4 button Gravis gamepad through the game port, but am not having any luck.

The card is a SoundBlaster 16 PCI with CT4750 printed on the PCB and CT5880 on the chip. The PC is a Dell PowerEdge 2550.

I am very new to Linux, but here is what I have found so far:

**I don't see any reference to JS0 in /dev or /dev/input and sound is working fine**

**lsmod shows the game port module:**

snd_ens1371            23012  3
snd_rawmidi            23204  1 snd_ens1371
snd_seq_device          7944  1 snd_rawmidi
snd_pcm_oss            48168  1
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85384  2 snd_ens1371,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_timer              23172  1 snd_pcm
snd_ac97_codec         59268  1 snd_ens1371
snd                    50660  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_ac97_codec
soundcore               9824  4 snd
**gameport                4736  1 snd_ens1371**


**gedit /etc/modutils/alsa-base shows:**

above snd-pcm snd-pcm-oss
**options joystick=0x200**


**lspci shows:**

0000:00:00.0 Host bridge: ServerWorks CNB20HE Host Bridge (rev 23)
0000:00:00.1 Host bridge: ServerWorks CNB20HE Host Bridge (rev 01)
0000:00:00.2 Host bridge: ServerWorks CNB20HE Host Bridge (rev 01)
0000:00:00.3 Host bridge: ServerWorks CNB20HE Host Bridge (rev 01)
0000:00:02.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 04)
0000:00:0e.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
0000:00:0f.0 ISA bridge: ServerWorks OSB4 South Bridge (rev 50)
0000:00:0f.1 IDE interface: ServerWorks OSB4 IDE Controller
0000:00:0f.2 USB Controller: ServerWorks OSB4/CSB5 OHCI USB Controller (rev 04)
0000:01:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5700 Gigabit Ethernet (rev 12)
0000:02:02.0 PCI bridge: Intel Corp. 80960RM [i960RM Bridge] (rev 02)
0000:02:04.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
0000:03:04.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
0000:03:04.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)


I know the controller works in XP. I don't know how to test the buttons in Ubuntu to see if the game port/controller are working.

Any help would be greatly appreciated.

---

### Post by electroglas on 2004-11-19
bump

---

### Post by daikane on 2004-12-27
:sad: very same problem here.

---

### Post by Soulman on 2004-12-29
Have you tried using root to see if your joystick works.  I've found in the past that I had permissions problems in regards to being able to use the joystick.  Sounds like it should work.  So see about running your program using sudo and see what happens.  Then it's just figuring out which device to configure for your user usage.

---

