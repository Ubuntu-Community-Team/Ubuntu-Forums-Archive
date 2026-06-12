---
title: "Yamaha UR 22 sound interface"
date: 2013-11-15
forum: Hardware
---

### Post by codeysatfa on 2013-11-15
Hi everybody

I'm brand new to Ubuntu and while most have worked flawless from install, i'm trying to get my sound interface working and only drivers from yamaha are win and mac.

I'm supposed to enter this somewhere in sound/usb/quirks-table.h:

{ 
        USB_DEVICE(0x0499, 0x1509), 
        .driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) { 
                /* .vendor_name = "Yamaha", */ 
                /* .product_name = "Steinberg UR22", */ 
                .ifnum = QUIRK_ANY_INTERFACE, 
                .type = QUIRK_COMPOSITE, 
                .data = (const struct snd_usb_audio_quirk[]) { 
                        { 
                                .ifnum = 1, 
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE 
                        }, 
                        { 
                                .ifnum = 2, 
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE 
                        }, 
                        { 
                                .ifnum = 3, 
                                .type = QUIRK_MIDI_YAMAHA 
                        }, 
                        { 
                                .ifnum = 4, 
                                .type = QUIRK_IGNORE_INTERFACE 
                        }, 
                        { 
                                .ifnum = -1 
                        } 
                } 
        } 
},

Can anyone tell me how to actually do that? I believe i may have found the right folder, it just wount let me create anything.
Hints on what to read up on to get this are also greatly appreciated :)

Best regards

---

