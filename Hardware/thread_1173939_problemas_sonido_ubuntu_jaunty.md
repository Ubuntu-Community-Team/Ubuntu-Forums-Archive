---
title: "problemas sonido ubuntu jaunty"
date: 2009-05-30
forum: Hardware
---

### Post by milkocepeda on 2009-05-30
Hola:
Tengo un HP mini y no tengo sonido, pregunté en un foro de Chile y me dijieron que digitara unos comandos y no pasó nada, estos fue lo que me arrojo la terminal:
mcepeda@mcepeda-laptop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
mcepeda@mcepeda-laptop:~$ lsmod| grep snd 
snd_hda_intel         435636  3  
snd_pcm_oss            46336  0  
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0  
snd_seq_oss            37760  0  
snd_seq_midi           14336  0  
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd 62628 15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
Necesito ayuda. 
Gracias Milko

---

### Post by etnpnys on 2009-05-30
Tu estas en el forum de ingles - nadie te entienden...

---

