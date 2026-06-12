---
title: "Inspiron3200 -- Sound + Vid Probs..."
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by aleXL on 2005-05-09
**_VIDEO_**

Sorted the problem with the vidoeo by changing Xorg's default depth from 24 to 16 iin etc/X11/Xorg.conf...

[U]
**SOUND**[/U]

I've been looking at a similar problem in the Thinkpad600E... seems to be similar? Beeps at start-up... alsa...

Soundcard should be a CS4236b... so wot's opl3 doing there too?

Any help'd be greatly appreciated...

My lsmod(edited):

Module                  Size  Used by
snd_opl3_lib           10112  0
snd_hwdep               9220  1 snd_opl3_lib
snd_cs4236_lib         16000  0
snd_mpu401_uart         7168  0
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd_cs4231_lib         24832  1 snd_cs4236_lib
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_timer              23300  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    50276  11 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_cs4231_lib,snd_pcm

lspci:

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)

---

