---
title: "Logitech quickcam pro for notebooks issues"
date: 2009-01-16
forum: Hardware
---

### Post by acimmarusti on 2009-01-16
Version: Ubuntu 8.10 Intrepid Ibex

This webcam is fully supported by the UVC video linux driver. It is claimed to work out of the box for versions of ubuntu greater than 7.10. However I found this not to be true. The webcam did not work with luvcview, camorama, ekiga, cheese and skype. So I had to compile from source the latest UVC video drivers.

$ lsmod | grep uvc
uvcvideo 64780 0
compat_ioctl32 9344 1 uvcvideo
videodev 47488 1 uvcvideo
v4l1_compat 21892 2 uvcvideo,videodev
usbcore 148848 6 uvcvideo,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd

This made the webcam work under luvcview and under skype (with certain conditions). However, functionality for ekiga was bizarre (the built in mic appears to work, but not the webcam). As for cheese and camorama the webcam never worked.

I can't seem to get the built-in mic to work with 'arecord'. I followed the instructions outlined here to test my usb-mic with ALSA: [http://www.audacityteam.org/wiki/index.php?title=USB_mic_on_Linux](http://www.audacityteam.org/wiki/index.php?title=USB_mic_on_Linux) (my initial hope was to be able to use with audacity, since gnome-sound-recorder is broken in intrepid).

The output obtained is in the attached file. I know that if I am able to make the mic work with alsa, then It will work with everything. But I just don't know what to do.

When I run ekiga (2.0.12) and I use the following settings for my webcam:
Video plugin: V4L2
Input Device: UVC Camera (046d:0991)
Format: NTSC (america)
Channel: 0

I get a pop-up window that says:
Error while opening video device UVC Camera (046d:0991)

Your driver doesn't seem to support any of the color formats supported by Ekiga.
Please check your kernel driver documentation in order to determine which Palette is supported.

It's puzzling, because as I stated above when I do 'lsmod | grep uvc' I get v4l1 and not v4l2. Nevertheless I have tried using V4L as video plugin which yields the same window with a different message:

Error while opening video device UVC Camera (046d:0991)

Your video driver doesn't support the requested video format.

I had not noticed this before, but I get the following message in my terminal when I run ekiga:

libv4l2: error setting pixformat: Input/output error

This is of course related to the message I get on the pop-up window when I use V4L2. I tried reinstalling libraries related to V4L2 to no avail.

I followed instructions outlined here: [http://www.audacityteam.org/wiki/index.php?title=USB_mic_on_Linux](http://www.audacityteam.org/wiki/index.php?title=USB_mic_on_Linux)

$ lsmod | grep snd
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
snd_atiixp             24204  4 
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_atiixp_modem       20360  5 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_ac97_codec        111652  2 snd_atiixp,snd_atiixp_modem
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                83204  8 snd_usb_audio,snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              29960  2 snd_seq,snd_pcm
snd                    63268  30 snd_usb_audio,snd_hwdep,snd_atiixp,snd_seq_oss,snd_atiixp_modem,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              15328  1 snd
snd_page_alloc         16136  3 snd_atiixp,snd_atiixp_modem,snd_pcm
usbcore               148848  6 uvcvideo,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd

$ cat /proc/asound/cards
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with unknown codec at 0xc0003400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xc0003800, irq 17
 2 [U0x46d0x991    ]: USB-Audio - USB Device 0x46d:0x991
                      USB Device 0x46d:0x991 at usb-0000:00:13.2-6, high speed
$ cat /proc/asound/pcm
01-00: ATI IXP MC97 : ATI IXP MC97 : playback 1 : capture 1
00-00: ATI IXP AC97 : ATI IXP AC97 : playback 1 : capture 1
02-00: USB Audio : USB Audio : capture 1

$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: U0x46d0x991 [USB Device 0x46d:0x991], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ alsamixer -c 2

$ arecord -f cd -D hw:2,0 -d 20 ~/Desktop/test.wav
Recording WAVE '/home/candres/Desktop/test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
arecord: set_params:959: Channels count non available

---

