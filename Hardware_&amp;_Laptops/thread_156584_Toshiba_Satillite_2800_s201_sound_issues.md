---
title: "Toshiba Satillite 2800 s201 sound issues"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by Rikostan on 2006-04-07
This machine was driving me crazy. I installed a few different versions of ubuntu on It, like edubuntu, kubuntu, Breezy and dapper and none of them would get far past GDM.
I would hear the drums from the GDM screen, log on, hear the first few seconds of the start up sound and it would stop.

The machine was not frozen. I could ctrl-alt-F1 to get to command line session, but it seemed the Gui was locked.

Finally I saw a command to kill esd, so I tried that. I did a killall esd and I was able to get into gnome just fine, but of course with no sound.
I stopped the sound server from starting up and rebooted and I could get into gnome just fine, but still no sound of course. I would hear the drums at the first part of GDM though!

So I changed everything I could to use alsa instead of esd, but nothing has changed.

I saw a lot of other posts here dealing with no sound on laptops, so I tried pretty much everything I could, but still to no avail. At this point I don't even remember all the changes I have made, so I am getting ready to install again, so I can start from scratch, but first I wanted to see if anybody here had any ideas.

I am at work at the moment, so I can not post any logs or anything, but I will post everything I can think of tonight. I will also post what steps I have already taken(that I still remember).

Besides the sound issues edubuntu is running fine on this machine. I want to give it to my youngest daughter to use in place of her windows laptop, but she really needs sound.


TIA for any advice you can offer.

---

### Post by Rikostan on 2006-04-07
some more info...
lsmod | grep snd
snd_ymfpci             58944  3
gameport               14824  1 snd_ymfpci
snd_ac97_codec         83932  1 snd_ymfpci
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  4 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10624  1 snd_ymfpci
snd_timer              24164  4 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               8896  1 snd_opl3_lib
snd_page_alloc         10600  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         7296  1 snd_ymfpci
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8460  2 snd_opl3_lib,snd_rawmidi
snd                    54884  15 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9600  1 snd

---

### Post by Rikostan on 2006-04-07
lspci

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:05.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:05.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:05.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:05.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 09)
0000:00:08.1 Serial controller: Xircom Mini-PCI K56Flex Modem
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 11)0000:06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

### Post by ptmmatssc on 2006-04-14
Wow  , wish I could tell you what's wrong . Am using the same laptop and have not had any sound probs at all .Have Breezy 5.10 live running right now and actually got everthing working no prob .

---

### Post by Tom Tiger on 2006-04-15
That is odd,  I've tested a 2800 (101 or 301) a while back when 5.10 was just out and there were no problems.  You could try a different live linux distro, like Knoppix, allthough I don't think it will make a difference.

There is one thing you can try.  Activate the DMA for the drives, it sounds weird but I've had a Knoppix version with alsa problems (3.81 I think) in which activating dma solved the problem.

L8tr...  Tom

---

