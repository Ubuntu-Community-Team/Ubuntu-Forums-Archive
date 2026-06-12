---
title: "Fast Track Pro (audio interface) in 24bit 96khz mode in normal Ubuntu possible?"
date: 2018-03-09
forum: Hardware
---

### Post by ultragamer2 on 2018-03-09
I have a USB 1 Fast Track Pro audio interface and I want to get it working in 24bit 96khz mode.

Has anyone got this usb audio device to work properly? There was some older info on the internet about having to recompile the kernel which as as linux newbie is too difficult.
But this new information says it can work without this recompiling but it's for Arch linux [https://wiki.archlinux.org/index.php/Professional_audio#M-Audio_Fast_Track_Pro](https://wiki.archlinux.org/index.php/Professional_audio#M-Audio_Fast_Track_Pro)

I have standard Ubuntu 17.10 installed, is there a way to get it to work with this setup without any recompiling? Does anyone know who has it or if there is a recent setup guide?
I know it only supports one way playback or recording at 96/24.

I have jackd installed.

---

### Post by ultragamer2 on 2018-03-18
So far I tried setting these two settings in

etc/pulse/daemon.conf

 default-sample-format = s24le
 default-sample-rate = 96000

But when I set 96000 in jackd and start it, it always shows 48000 in the window display which is the low quality class compliant mode sample rate of the M-audio fast track pro. So it would also not be doing 24bit but 16bit class compliant mode.

---

### Post by ultragamer2 on 2018-03-18
Here's some more info from the sound card.

**stream1 file**

M-Audio FastTrack Pro at usb-0000:00:1a.0-1.4, full speed : USB Audio

Playback:
  Status: Stop
  Interface 2
    Altset 2
    Format: S24_3BE
    Channels: 2
    Endpoint: 3 OUT (ADAPTIVE)
    Rates: 44100, 48000
  Interface 2
    Altset 5
    Format: S24_3BE
    Channels: 2
    Endpoint: 3 OUT (ADAPTIVE)
    Rates: 8000 - 48000 (continuous)

Capture:
  Status: Stop
  Interface 4
    Altset 2
    Format: S24_3BE
    Channels: 2
    Endpoint: 5 IN (SYNC)
    Rates: 8000 - 48000 (continuous)



So it seems to need be (big endian)

I changed the sample format in pulse daemon.conf to big endian (but there is no support for 3be) all I could choose was s24be.

But it's supposed to do 96khz. Does anyone know how to unlock 96khz? (I know it can only do 96khz one way on one output or input due to it being usb1).


Also another thing is it seems a **lot** softer in Ubuntu (volume in pulse settings at 100% and in audacious 100%).
Where as on full volume that used to be very loud on the amplifier is now not very load at all at full volume.
Are there any other volume settings for devices somewhere in ubuntu config files that might be down low somehow?

---

