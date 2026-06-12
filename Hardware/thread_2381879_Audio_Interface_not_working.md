---
title: "Audio Interface not working"
date: 2018-01-06
forum: Hardware
---

### Post by jonandtice on 2018-01-06
I have a Line 6 Helix (guitar multi-effects pedal) that acts as an audio interface over USB.  Although it is listed as a sound card
```
~$ cat /proc/asound/cards
 0 [Loopback       ]: Loopback - Loopback
                      Loopback 1
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 304
 2 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf7700000 irq 306
 3 [Alpha          ]: USB-Audio - Lexicon Alpha
                      Lexicon Lexicon Alpha at usb-0000:03:00.0-2, full speed
 4 [HELIX          ]: USB-Audio - HELIX
                      LINE 6 HELIX at usb-0000:03:00.0-1, high speed

```
it is not recognized as an audio device.
```
~$ cat /proc/asound/pcm
00-00: Loopback PCM : Loopback PCM : playback 8 : capture 8
00-01: Loopback PCM : Loopback PCM : playback 8 : capture 8
01-03: HDMI 0 : HDMI 0 : playback 1
01-07: HDMI 0 : HDMI 0 : playback 1
01-08: HDMI 0 : HDMI 0 : playback 1
01-09: HDMI 0 : HDMI 0 : playback 1
02-00: ALC887-VD Analog : ALC887-VD Analog : playback 1 : capture 1
02-01: ALC887-VD Digital : ALC887-VD Digital : playback 1
02-02: ALC887-VD Alt Analog : ALC887-VD Alt Analog : capture 1
03-00: USB Audio : USB Audio : playback 1 : capture 1

```
I think the issue can be seen in dmesg:
```
[74449.448191] usb 1-1: new high-speed USB device number 8 using xhci_hcd
[74449.651241] usb 1-1: New USB device found, idVendor=0e41, idProduct=4244
[74449.651245] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[74449.651247] usb 1-1: Product: HELIX   
[74449.651249] usb 1-1: Manufacturer: LINE 6
[74449.651250] usb 1-1: SerialNumber:    2804389
[74449.673547] usb 1-1: parse_audio_format_rates_v2(): unable to retrieve number of sample rates (clock 16)
[74449.677222] usb 1-1: parse_audio_format_rates_v2(): unable to retrieve number of sample rates (clock 16)

```

Is this something I need to contact the manufacturer about or is there a workaround?

---

### Post by jonandtice on 2018-04-24
Bump

---

