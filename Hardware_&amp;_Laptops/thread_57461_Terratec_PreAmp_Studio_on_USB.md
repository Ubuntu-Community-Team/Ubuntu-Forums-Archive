---
title: "Terratec PreAmp Studio on USB"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by strandlooper on 2005-08-16
Hi
I want to use this nice USB device to pick my vinyl collection to the hard drive which is not aproblem on M$ XP. It seems that I need a little help to get it work on my favorite OS.

Here what I found on my Acer Travelmate 8100 Hoary 5.04 with some modifications due to sound, wifi and ACPI work arounds.

**lsusb**
................
Bus 004 Device 003: ID 0ccd:3556 TerraTec Electronic GmbH
................

**lsmod | grep snd**

snd_usb_audio          68160  0
snd_usb_lib            13824  1 snd_usb_audio
snd_rawmidi            22816  1 snd_usb_lib
snd_seq_device          8204  1 snd_rawmidi
snd_hwdep               8608  1 snd_usb_audio
snd_hda_intel          15872  4
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  5 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  14 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  2 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
usbcore               104188  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

Actual the device is not mounted corretly. On MS XP it was necessary to switch from "Realtek HD Audio rear input" to "phone PreAmp USB" in the sound and audio properties.

Any idea to get it work?

Thank you in advance.

Cheers Strandlooper

---

