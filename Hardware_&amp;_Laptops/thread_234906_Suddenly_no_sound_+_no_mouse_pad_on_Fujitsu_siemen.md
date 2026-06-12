---
title: "Suddenly no sound + no mouse pad on Fujitsu siemens"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by pau on 2006-08-12
Hi,

my laptop was the perfect laptop until yesterday. Suddenly the mouse pad is dead and the sound doesn't work. I've noticed that the mouse pad always becomes a bit mad (the pointer springs abruptely from left to right, top to bottom) after a suspend-to-ram or a new reboot but it is a matter of a few seconds. When gnome is loaded everything is fine... Until yesterday. Now the pad is as if it was dead... and the sound too... For instance, when launching xmms I get

```
elachistos| xmms conte_paolo                                                                                                                           

Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: no s'ha pogut obrir el fitxer objecte compartit: El fitxer o directori no existeix

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: no s'ha pogut obrir el fitxer objecte compartit: El fitxer o directori no existeix

Gtk-WARNING **: No s'ha trobat un mòdul carregable al module_path: «libindustrial.so»,

Gtk-WARNING **: No s'ha trobat un mòdul carregable al module_path: «libindustrial.so»,

Gtk-WARNING **: No s'ha trobat un mòdul carregable al module_path: «libindustrial.so»,

Gtk-WARNING **: No s'ha trobat un mòdul carregable al module_path: «libindustrial.so»,

Gtk-WARNING **: No s'ha trobat un mòdul carregable al module_path: «libindustrial.so»,

Gtk-WARNING **: No s'ha trobat un mòdul carregable al module_path: «libindustrial.so»,
Message: device: default

** WARNING **: oss_open(): Failed to open audio device (/dev/dsp): El fitxer o directori no existeix
```

It means "libgail.so: it's been impossible to open the shared file" "no loadable module in module_path" and "the file or directory doesn't exist"

It seems that the sound card has disappeared from the configuration, because in "sound" the "default card" is marked in grey

More information

```
elachistos| gnome-sound-properties                                            
GTK Accessibility Module initialized
Bonobo accessibility support initialized
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver return ed error: El dispositiu no és vàlid
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned er ror: El dispositiu no és vàlid
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: El dispositiu no és vàlid
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: El dispositiu no és vàl id
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
```

And my lspci

```
elachistos| lspci                                                                                                                                          ~
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
0000:01:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ab)
0000:01:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 03)
0000:01:0a.3 System peripheral: Ricoh Co Ltd R5C576 SD Bus Host Adapter (rev 01)
0000:01:0a.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter
0000:01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:0d.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
```

I am fearing that it's related to the upgrade I did recently and possibly I should change to xfree (using xorg) but this doesn't explain the sound problem, right?

HELP!

I don't want to reinstall ubuntu, it's taken me ages to configure the laptop like I have it now (for instance with XGL, but also tons of other personal things)

---

### Post by pau on 2006-08-15
bump...

no help at all? #-o

---

### Post by pau on 2006-08-16
rebump rebump bump bump

---

### Post by pau on 2006-08-18
rebump + HEEEEEEEEEELP!!

with the last cairo upgrade a LOT of X-things are not working!

I must enter with gnome safe-mode, otherwise it doesn't work AT ALL

I can click and click and click and the pointer just doesn't react...

**DAPPER, I HATE YOU!**

I think I'm going to either downgrade to breezy or change the distro... a debian one with gnome, but NOT DAPPER

---

### Post by pau on 2006-08-21
[SIZE="4"]SOMEBODY PLEASE HELP MEEEEEE!!![/SIZE]

I don't want to reinstall ubuntu and lose ALL work I've put into this laptop after the installation, I just don't want, I cannot afford to spend so much time, I want a simple answer... come on, guys, I know some of you can help me

[-o<

---

### Post by pau on 2006-08-21
BTW...

```
elachistos| aplay -l                                                                   
aplay: device_list:221: no soundcards found...
```

It doesn't find the card! But sometimes yes... rarely but sometimes yes

---

### Post by pau on 2006-08-21
and also btw, sometimes after suspend-to-ram I get

```
codec_read 0: semaphore is not ready for register 0x2c
```

and the laptop doesn't resume and is frozen...

Really, dapper is a pain...

---

### Post by pau on 2006-08-22
I take it back: it's a hardware problem

Tried different live cds and the mouse pad and sound were also dead

---

