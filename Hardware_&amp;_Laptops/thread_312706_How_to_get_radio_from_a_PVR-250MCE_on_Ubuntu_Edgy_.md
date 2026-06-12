---
title: "How to get radio from a PVR-250MCE on Ubuntu Edgy and MythTV?"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by piec2 on 2006-12-04
Hi,

I've been trying to get FM radio out of a PVR-250MCE card under Ubuntu Edgy for the last 2 days, but I can't get it to work.

IVTV when it loads seems to indicate the card has radio, as shown in the log below:
```

 ivtv:  ==================== START INIT IVTV ====================
 ivtv:  version 0.7.0 (tagged release) loading
 ivtv:  Linux version: 2.6.17-10-generic SMP mod_unload gcc-4.1
 ivtv:  In case of problems please include the debug info between
 ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
 ivtv:  any module options, when mailing the ivtv-users mailinglist.
 lirc_dev: IR Remote Control driver registered, at major 61
 lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.

 lirc_mceusb2: USB remote driver for LIRC v0.22
 lirc_mceusb2: Martin Blatter <martin_a_blatter@yahoo.com>
 usb 1-3: reset full speed USB device using ohci_hcd and address 2
 input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
 ts: Compaq touchscreen protocol output
 lirc_dev: lirc_register_plugin: sample_rate: 0
 lirc_mceusb2[2]: Philips eHome Infrared Transceiver on usb1:2
 usbcore: registered new driver lirc_mceusb2
 ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
 GSI 21 sharing vector 0x32 and IRQ 21
 ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [APC7] -> GSI 16 (level, low) -> IRQ 50
 PCI: Setting latency timer of device 0000:00:05.0 to 64
 NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8776  Mon Oct 16 21:53:43 PDT

 ivtv0: Autodetected Hauppauge WinTV PVR-250 card (cx23416 based)
 ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
 ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 50
 ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
 tveeprom 0-0050: Hauppauge model 32552, rev C168, serial# 8113852
 tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
 tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
 tveeprom 0-0050: audio processor is MSP4448 (idx 27)
 tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
 tveeprom 0-0050: **has radio**, has no IR remote
 tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
 NET: Registered protocol family 17
 tda9887 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
 saa7115 0-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
 msp3400 0-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
 msp3400 0-0040: **MSP4448G-A2 supports radio**, mode is autodetect and autoselect
 ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
 ivtv0: Encoder revision: 0x02050032
 ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
 ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
 ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
 ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
 ivtv0: Create encoder radio stream
 tuner 0-0061: type set to 47 (LG NTSC (TAPE series))
 ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
 ivtv:  ====================  END INIT IVTV  ====================

```

I have tried Gnomeradio but it doesn't appear to tune to anything (even when using scanning). I also tried kradio and that didn't work either (after installing the whole kubuntu desktop!).

The device /dev/radio exists, so that's not the problem.

I even tried /dev/video24 which has is an audio feed, however that doesn't seem to yield any results and even if it did the FM radio on my cable provider are scarses (only a few stations are supported). That's why I would rather like to use the FM tuner built into the PVR-250 MCE which is fed by a separate external antenna.

I did also get MythStream to work, unfortunately some of the local radio stations I prefer do not generate an internet feed and some use a weird feed through Flash which doesn't seem to work with MythStream.

Help !

---

### Post by superm1 on 2006-12-05
Silly possible solution, /dev/radio exists - but what are its permissions?  can you read them as the user you are running gnome radio as?

---

### Post by piec2 on 2006-12-05
It could have been the problem (it was set to 660, but I set it to 666 and that didn't change anything :(

---

### Post by superm1 on 2006-12-06
I'm not sure what beyond this, you might want to consult with the ivtv mailing list for help as I expect ubuntu usage of the radio features are fairly scarce.

---

### Post by piec2 on 2006-12-07
Yup, it's confirmed: it's a bug in the kernel.
[http://www.ivtvdriver.org/index.php/Howto:Radio_tuner](http://www.ivtvdriver.org/index.php/Howto:Radio_tuner)
The tuner on the PVR-250MCE is the same as on the PVR-150MCE

Looks like I will have to wait until the new kernel for Ubuntu is ready (since I'm currently using Edgy which is 2.6.17).

---

### Post by superm1 on 2006-12-07
Ah.... That's a bit annoying :)

An alternative can be to try to download the kernel source, patch the file yourself and build it, but that is probably a bit more work then you want to handle.

I say just hold off until feisty with its 2.6.20, unless you really want to get your hands dirty.

---

