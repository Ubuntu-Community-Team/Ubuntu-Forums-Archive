---
title: "M66SE Sound Troubles"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by lishevita on 2008-01-02
Hello,

   I have an Infinity M66SE (same thing as the Clevo M66SE) and I'm having troubles with the sound. Sound through the speakers works just find. Sound through the Mic and the Headphones, not so much.

   The mic doesn't work at all. The headphones at least have some sound, but it's like "line out" kind of sound... you know, just a steady sound level where changing the volume makes no difference. The sound level is fairly quiet, too. 

  I have messed with alsamixer, but no joy. I have SoundMixer in my panel, still no joy. 

    I'm suspecting that there is something driver-ish that isn't right, since on the Windows partition these same things didn't work until I loaded a separate driver from a cd that came with the computer. Any ideas?

Here's the card info that I get from alsamixer:
&#9474; Card: HDA VIA VT82xx                                                                  &#9474;
&#9474; Chip: Generic 1106 ID 1708 

and here's what lspci | grep -i audio says:
06:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

---

### Post by balaknair on 2008-01-02
open a terminal and enter the following command
```
cat /proc/asound/card0/codec#* | grep Codec
```

this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A
Next find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

(the alsa-config should also be on your system at usr/src/(your kernel version)/sound/alsa/alsa-configuration.txt)

in that page find your card model and check the details given
eg
```
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)

```
select the description that best matches your system(eg a 5.1 surround system with 6 audio-out channels/ports would be 6stack)

then go back to the terminal and type
```
sudo nano /etc/modprobe.d/alsa-base

```
Paste this into the last line of the file
```
options snd-hda-intel model=MODEL

```
replace MODEL with your model(6stack, 3stack, laptop etc.)

reboot.

if this doesn't work you might have to consider recompiling the alsa-kernel(though if you followed the ubuntuforums guide above I guess you've already tried it.
These steps are just a part of the howto guide at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I've only mentioned the steps that worked for me with the Via 82xx HDA card(like yours) with Gutsy 7.04, 7.10, and with Mandriva 2008- recompiling the kernel with Gutsy led to my sound card not being detected at all and I had to purge alsa and try again, that's why I mentioned just the tips that worked for me.
If it works please post a reply and mark the thread as solved.
Lotsa luck

---

