---
title: "Bluez sco/mono bluetooth headsets (like moto H350)  and alsa?"
date: 2008-08-17
forum: Hardware
---

### Post by pjomega on 2008-08-17
I was wondering if anybody had had any success using the suggested implementation of bluetooth audio (ie, just the bluez stack and alsa). I'm currently using the stock bluez-3.26, and i've tried both alsa 1.0.15 and freshly compiled 1.0.17. The a2dp streaming works fine. I've used a stereo motorola H850 headset with no problems. It connects and 'aplay -D bluetooth $SND' works beautifully. However i've had no luck with lower end mono/ear clip head sets (tried a moto H350 and a scala 700). They connect, 'hcitool info' returns all the correct information, and hcidump dumps packets during communication. Alsa just doesn't seem to be able to communicate properly. 

For a stereo headset, .asoundrc:
pcm.bluetooth {
 type bluetooth
 device $MAC 
 profile "hifi"
}
==>perfect

For a mono headset:
pcm.bluetooth {
 type bluetooth
 device $MAC 
 profile "voice"
}
==>
'aplay -D bluetooth $SND' returns
"aplay: set_params:959: Channels count non available"

(just so there's no confusion, it's a low quality headset; profile "hifi" gives an alsa bad i/o error)

It looks like alsa is looking for the number of channels on the device and not getting anything back. I'm not really sure where to look to troubleshoot this. Any advice would be appreciated.

Many thanks.
pj

---

