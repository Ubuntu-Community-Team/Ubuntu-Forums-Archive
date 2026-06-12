---
title: "Sound can't decide if it works or not."
date: 2011-07-30
forum: Hardware
---

### Post by PIDGINZ on 2011-07-30
Hi all

I've just installed Ubuntu 10.04 64 bit on my main PC next to windows 7 64 bit (on a different hard drive), and so far I've had nothing but trouble with getting my sound working. 

First, my specs: Core 2 Quad Q9550 @ 3.4GHz, 4GB RAM, GTX460 1GB, and an Envy24(HT or PT, can't remember atm) sound card (I don't use onboard sound) all sitting on an Asus P5K Premium.

Now when sound works, it works well and fine, and I have absolutely no issues with it. But sometimes (actually more often than not) when I boot up I have no sound whatsoever. If I'm particularly unlucky then I get only the right speaker on my headphones outputting sound. Usually a reboot fixes it, but I've just had 3 boots in a row with no sound at all.

I have no idea what's causing this, and I don't really want to change to my motherboard's onboard sound (intel hd audio) purely because I like the sound of my Envy24 card.

Any ideas?

---

### Post by PIDGINZ on 2011-07-31
Bump. I'm in ubuntu right now and sound is still not working. :(

```
logan@logan-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````
logan@logan-ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Device 0e22 (rev a1)
01:00.1 Audio device: nVidia Corporation Device 0beb (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
05:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

``````
logan@logan-ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             7598  1 
snd_ice1724           116991  1 
snd_ice17xx_ak4xxx      3155  1 snd_ice1724
snd_ac97_codec        123086  1 snd_ice1724
ac97_bus                1450  1 snd_ac97_codec
snd_ak4xxx_adda         8572  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_ak4114              9260  1 snd_ice1724
snd_pcm_oss            40495  0 
snd_mixer_oss          16304  1 snd_pcm_oss
snd_pcm                84921  4 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss
snd_page_alloc          8532  1 snd_pcm
snd_pt2258              3583  1 snd_ice1724
snd_i2c                 5369  2 snd_ice1724,snd_pt2258
snd_seq_dummy           1782  0 
snd_seq_oss            31188  0 
snd_seq_midi            5957  0 
snd_rawmidi            22959  2 snd_ice1724,snd_seq_midi
snd_seq_midi_event      7331  2 snd_seq_oss,snd_seq_midi
snd_seq                57322  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22533  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69078  16 snd_ice1724,snd_ac97_codec,snd_ak4xxx_adda,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_pt2258,snd_i2c,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39381  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5843  1 fbcon
softcursor              1533  1 bitblit
joydev                 10484  0 
asus_atk0110            9554  0 
serio_raw               4982  0 
soundcore               8394  1 snd
nvidia              11995020  40 
vga16fb                11900  1 
vgastate                9251  1 vga16fb
intel_agp              29149  0 
agpgart                38844  2 nvidia,intel_agp
hwmon_vid               3098  0 
coretemp                5730  0 
r8169                  38149  0 
mii                     5237  1 r8169
sky2                   45792  0 
usbhid                 40128  0 
hid                    81871  1 usbhid

```Not sure what else is needed. I could try reloading the driver but I don't know which driver to reload. I'm assuming it's snd_ice1724.

EDIT: I just rebooted, and now I only have sound out of my right headphone speaker again.
```
logan@logan-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICE1724 [ICEnsemble ICE1724], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICE1724 [ICEnsemble ICE1724], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```That's different this time, the top one is in use?

EDIT: Rebooted again, now sound is working. Nothing else that I can see has changed. :confused:

---

### Post by PIDGINZ on 2011-07-31
Is there really nobody that knows anything about this?

---

### Post by PIDGINZ on 2011-08-01
For anybody that actually reads this, I found
```
ice1724: No matching model found for ID 0x12140324
ice1724: Invalid EEPROM version 1
```
In my kernel log, so I tried a bunch of different models in /etc/modprobe.d and came up with nothing. I then discovered that my sound card is actually an Envy24 Tremor, which means it has the VT1723 chip and not the VT1724 chip. I promptly gave up, took the card out, and enabled my onboard sound and I now have sound with less bass, but I suppose I can get used to it. Quality is far better than I remember though, maybe these linux drivers have got one up on windows drivers :P

Well that was fun.

---

### Post by FormatSeize on 2011-08-01
> **PIDGINZ said:**
> Is there really nobody that knows anything about this?
Probably.
 
Yesterday, when I changed my RAM sticks, the sound stopped working. When I would boot into Slackware, I would get a message that says something along the lines of "One or more sound devices are missing. Would you like KDE to permanently forget about this device?" At first, I just ignored it, since the sound was working. Finally, though, I got tired of seeing the message every time I entered the X environment, so I told it to forget about the drivers and never show me that message again. 
 
Then it happened. The sound stopped working. I booted into Windows, and there was no sound there either. So while I was in Windows, I did all the updates, but there was still no sound. Then I went to Google, and eventually found some piece of crap home-brewed software, which was the only one that was Microsoft certified, but still nothing.
 
Bored of going in circles, I made a plea for help to a friend over a social network. He basically just made fun of me, and said that I didn't know anything about computers. Finally, though, I looked up the part number for my motherboard. From there, I saw that I had Intel onboard integrated sound. That, in turn, gave me very specific things to search for without getting lost in Google-World. 
 
I went to the  site I needed to get to, reinstalled the drivers (no charge!), rebooted, and everything worked fine. I would suggest finding what your drivers are and reinstalling them.

---

