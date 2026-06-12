---
title: "Low Skype mic volume on a Dell Vostro 1400"
date: 2009-08-20
forum: Hardware
---

### Post by muadnu on 2009-08-20
I know this has been discussed a million times, but I just can't get it to work.

The issue is, well, the internal mic volume on my Dell Vostro 1400 using Skype is just unbearably low. I have tried everything in the forums, but nothing.

This has been happening ever since pulseaudio was introduced, but in previous Ubuntu versions I could just uninstall pulseaudio and get it to work. Strangely enough, this didn't solve it in Jaunty.

Some info on my specs:

```
$ cat /proc/asound/pcm
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 3
00-01: STAC92xx Digital : STAC92xx Digital : playback 1

$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 21

$ lsmod | grep snd
snd_hda_intel         557492  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by muadnu on 2009-08-22
I'm sorry to bump this, but I don't know what else to try. My wife is using this laptop and one of the main things she needs it for is Skype. The laptop is Windows-free, and she's loving it so far, so I wouldn't feel very good installing XP just for Skype. (I guess I could downgrade Ubuntu, or install Hardy and dual boot, but it doesn't sound like a good solution...)

---

### Post by xopher_mc on 2009-08-29
Hey there had a similar problem on my wife's ubuntu machine.


if you follow the instructions for comment 109 onwards should fix it for you.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998?comments=all]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998?comments=all")

---

### Post by muadnu on 2009-08-29
Thanks for the suggestion. But just yesterday I got it working by downloading the new Skype beta. The mic volume was still lower than it should have been, but nothing compared with what it was before. Then I used padevchooser to boost the volume a bit and now it works fine.

---

### Post by raisen on 2009-08-30
> **muadnu said:**
> Thanks for the suggestion. But just yesterday I got it working by downloading the new Skype beta. The mic volume was still lower than it should have been, but nothing compared with what it was before. Then I used padevmanager to boost the volume a bit and now it works fine.

Sorry for stealing your thread but what is padevmanager? I did a google search but couldn't find any result besides your own post. :)

---

### Post by muadnu on 2009-08-30
> **raisen said:**
> Sorry for stealing your thread but what is padevmanager? I did a google search but couldn't find any result besides your own post. :)

Well, my mistake. I meant padevchooser (I edited the post now). Once you install it and open it, you can go to "Manager" and then somewhere (devices maybe?) you can look for the input device and boost the volume.

---

### Post by raisen on 2009-08-30
> **muadnu said:**
> Well, my mistake. I meant padevchooser (I edited the post now). Once you install it and open it, you can go to "Manager" and then somewhere (devices maybe?) you can look for the input device and boost the volume.

Great, thanks. I was looking for something like that. I'll give it a try.

---

### Post by Nachoo on 2009-08-30
Hi there!

I have the padevchooser installed but I don't find where to do the boost thing. My internal mic works but it is way too low. 

I'm using jaunty and padevchooser 093.

thanks!

---

### Post by muadnu on 2009-08-31
Start padevchooser, then click on the icon on the tray and go to manager. Then go to the devices tab, and choose sources->alsa_input (or something like that) and then properties. The last property is volume, which you can set to more than 100%. In my case it works ok with 125%. Hope it helps!

---

