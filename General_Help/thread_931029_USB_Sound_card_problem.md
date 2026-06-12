---
title: "USB Sound card problem"
date: 2008-09-26
forum: General Help
---

### Post by ragidom on 2008-09-26
Hi there,

I've got a problem with usb sound card (c-media) in pretty 'antique' samsung laptop under ubuntu hardy. 

Few days ago it stopped working. I have no sound, no music only strange noise. Sound card is ok, I've checked it out on diferetn computer and on my one just after installing os and in both cases SC worked fine, so it isn't sound card fault. 

Problems have started when I installed upgrades, non free codecs and ubuntu-restricted-extras packages - then the music's over:( 

OS was installed properly, with default settings (ubuntu hardy, gnome, default sound demons, I am rather experienced linux user (over 2 years, mandriva, fedora, and now ubuntu for last half a year), I have checked sound card driver, sound demons (alsa, pulse, e.g.) and didn't find any solution.

Any ideas? Please help

---

### Post by Crafty Kisses on 2008-09-26
I'd like to see the results of this command:
```
lsusb
```

---

### Post by ragidom on 2008-09-27
> **Codename said:**
> I'd like to see the results of this command:
```
lsusb
```

Here u are:

Bus 001 Device 002: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 001: ID 0000:0000

---

