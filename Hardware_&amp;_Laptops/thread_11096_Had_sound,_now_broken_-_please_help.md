---
title: "Had sound, now broken - please help"
date: 2005-01-13
forum: Hardware &amp; Laptops
---

### Post by jakes on 2005-01-13
I've just installed Warty on my Toshiba Tecra 8100 laptop - it was working great, system sounds were working, and after installing the w32codec pack and was able to play mp3s. Then at some point sound stopped working. All I have done is to install some software, specifically Thunderbird, Java and Azureus bittorrent client, but I think the problem occurred after restarting. When I try to play mp3s or test system sounds, it seems as it is attempting to play something - all I hear is a very high frequency noise. Turning the Master or PCM volume down in alsa mixer changes the level of this noise.
I read in another thread that PCM output is muted on the Tecra 8100 - this isn't my problem, I've checked - and I was initially hearing things.
The soundcard this laptop uses is a Yamaha DS-XG (YMF774), and it is being recognised as the default soundcard.
Here is some further info:
> jacob@laptop-ubuntu:~ $ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:05.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:05.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:05.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:05.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:07.0 Communication controller: Lucent Microelectronics 56k WinModem (rev 01)
0000:00:09.0 IRDA controller: Toshiba America Info Systems FIR Port Type-DO
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 20)
0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/MX-MV (rev 11)0000:06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
> jacob@laptop-ubuntu:~ $ lsmod
Module                  Size  Used by
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ds                     17796  4
ipv6                  230020  8
af_packet              20872  2
snd_ymfpci             58180  3
snd_ac97_codec         59268  1 snd_ymfpci
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_ymfpci,snd_pcm_oss
snd_opl3_lib            9728  1 snd_ymfpci
snd_timer              23172  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9120  1 snd_opl3_lib
snd_page_alloc         11144  2 snd_ymfpci,snd_pcm
gameport                4736  1 snd_ymfpci
snd_mpu401_uart         7296  1 snd_ymfpci
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd                    50660  13 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
8139too                23936  0
8139cp                 19072  0
mii                     4864  2 8139too,8139cp
crc32                   4608  2 8139too,8139cp
yenta_socket           19328  1
pcmcia_core            63156  2 ds,yenta_socket
donauboe               15360  0
irda                  167360  1 donauboe
crc_ccitt               2432  2 donauboe,irda
uhci_hcd               29328  0
usbcore               104292  3 uhci_hcd
pci_hotplug            30640  0
intel_agp              20512  1
agpgart                31784  1 intel_agp
floppy                 54996  0
rtc                    12216  0
pcspkr                  3816  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
evdev                   9088  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  3
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  772
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb 
If there's any further info that I can supply to diagnose the cause of this problem, please let me know - I'm pretty new at Linux so I may have missed something important. I'm liking ubuntu, but I'd really like to get this fixed.
Thanks in advance,
jakes.

---

### Post by wallijonn on 2005-01-13
what do your /var/log logs show, like kern.log? You should be able to scroll backward and look for changes.

---

### Post by jakes on 2005-01-13
Thanks for replying, wallijonn - I've found the kern.log and had a look through it, but I'm not really sure what I'm looking for.
lspci identified the soundcard as 0000:00:0c.0 - looking for this in the kern.log file, it seemed to be doing the same thing each time, ie:
> Jan 13 01:20:15 localhost kernel: PCI: Found IRQ 11 for device 0000:00:05.2
Jan 13 01:20:15 localhost kernel: PCI: Sharing IRQ 11 with 0000:00:0c.0 
Is it a problem that they're sharing an IRQ? However, this is occurring from the beginning of the log (since installation), so I'm not sure this is the problem.
Is there something else i should be looking for? Are there other logs I should look at?
Should I post the contents of my kern.log file (it's just that its quite long)?
Thanks,
jakes

---

### Post by jakes on 2005-01-14
Ok, some further info - I am able to play and hear cds, but still nothing with when trying to play mp3 and systems sounds.
cheers, 
jakes

---

### Post by wallijonn on 2005-01-14
If it's .mp3s, then see if re-install ALSA, vorbis, etc. will fix your problem.

Just do a search in SPM for mp3 and sound.

---

### Post by jakes on 2005-01-14
Dude, you are so cool!  =D> 
Reinstalling alsa worked a treat! Should have thought of that myself, I guess.
Thankyou so much for your helpful pointers, to a newb.
Cheers, mate  :grin: 
jakes.

---

