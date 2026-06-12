---
title: "Realtek ALC892 No sound"
date: 2013-07-19
forum: Hardware
---

### Post by screaminj3sus on 2013-07-19
I just installed ubuntu on my desktop. It has a biostar tz68+ z68 motherboard with Realtek ALC892 sound (at least thats what alsamixer says the sound card is). I get no sound at all from my speakers. Tried playing with alsa mixer to no avail. The hardware seems to be detected and I don't see anything important muted, but no sound at all from my speakers. Running ubuntu 13.04 64-bit.

---

### Post by Yellow Pasque on 2013-07-19
Since it's fairly recent hardware, the first thing I would try is the latest driver/kernel module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
Direct link: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201307180559%7Eraring1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201307180559%7Eraring1_all.deb)

---

### Post by screaminj3sus on 2013-07-19
Unfortunately installing that did not seem to change anything (i installed the package and rebooted).

I also tried following this afterwards which didn't help at all either: [http://community.linuxmint.com/tutorial/view/1236](http://community.linuxmint.com/tutorial/view/1236)

Finding it very hard to find any recent information about linux on this chipset :(

---

### Post by Yellow Pasque on 2013-07-19
Try one more thing:
```
rm -r ~/.config/pulse; pulseaudio -k
```
If that doesn't help, file a bug (and please link us to the bug)
```
ubuntu-bug audio
```

---

### Post by screaminj3sus on 2013-07-19
> **Temüjin said:**
> Try one more thing:
```
rm -r ~/.config/pulse; pulseaudio -k
```
If that doesn't help, file a bug (and please link us to the bug)
```
ubuntu-bug audio
```

Alright, when I get home I'll try that and if it doesn't work I'll report a bug. In the meantime I might just get myself an asus xonar on amazon lol.

---

### Post by Yellow Pasque on 2013-07-19
If you have good headphones or speakers, a Xonar is worth it. I have a cheap Xonar DG as a backup sound card and it has good analog playback quality (though recording and front headphone jack are not supported on it for Linux :( )

---

