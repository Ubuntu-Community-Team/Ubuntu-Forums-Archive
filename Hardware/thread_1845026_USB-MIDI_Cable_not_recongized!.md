---
title: "USB-MIDI Cable not recongized!"
date: 2011-09-16
forum: Hardware
---

### Post by phyr0 on 2011-09-16
I've bougt a usb-midicable but it wasnt reognized.  If i launch dmesg i've this output:   [ 1825.060878] usb 5-2.4: new full speed USB device using ohci_hcd and address 5 [ 2140.608846] usb 5-2.4: USB disconnect, address 5 [ 2142.180881] usb 5-2.4: new full speed USB device using ohci_hcd and address 6   and if make lsusb:  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 006: ID 552d:4348

---

### Post by phyr0 on 2011-09-16
sorry! on firefox the editor make some noises.
ok on dmesg i've this output:

> 
[ 1825.060878] usb 5-2.4: new full speed USB device using ohci_hcd and address 5
[ 2140.608846] usb 5-2.4: USB disconnect, address 5
[ 2142.180881] usb 5-2.4: new full speed USB device using ohci_hcd and address 6


and by lsusb

> 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 006: ID 552d:4348  
Bus 005 Device 004: ID 1241:1503 Belkin Keyboard


552d:4348 is my usb-midicable, but nothing searching on google.

Can someone help me about?

---

### Post by cladisch on 2011-09-16
It's unlikely that a USB MIDI device is not recognized.  Is snd-usb-audio loaded?  Does it appear in /proc/asound/cards and in the output of "aplaymidi -l"?

Please show the output of "lsusb -v" for this device.

---

### Post by Nighto on 2011-12-11
Hi, I'm having the same problem.

The device shows up on lsusb:

```
$ lsusb | grep 552d
Bus 006 Device 003: ID 552d:4348 
```

The modules are loaded:

```
$ lsmod | grep snd_
snd_usb_audio         118064  0 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_hda_codec_idt      70553  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
snd_pcm                96755  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  16 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
```

It shows up on /proc:

```
$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 45
 1 [Midi           ]: USB-Audio - USB Midi
                      USB Midi at usb-0000:00:1d.1-2, full speed
```

And aplaymidi -l lists it:

```
$ aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 20:0    USB Midi                         USB Midi MIDI 1
```

However, the device doesn't shows up on any MIDI programs. I tried with zynaddsubfx and with JACK (qjackctl).

Any suggestions?

Best,
Nighto

---

