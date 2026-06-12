---
title: "Asus sound card not playing"
date: 2015-05-09
forum: Hardware
---

### Post by robbie 348 on 2015-05-09
Hi, asus xonar dgx sound refuses to work in any *buntu flavor or version. What's strange is it works perfectly with Linux Mint or Zorinos. I even did a full install of Ubuntu 14.04.2 with all updates and upgrades thinking that would fix it, but no. Alsamixer sees the card, so does pulseaudio, but I can't get any output. I guess I can keep using Mint as I quite like it, it's just frustrtating me now I can't make it work. Is there any way to find what driver Mint is using and copy it to Ubuntu?
I did a search and found some fixes but none did it. Any ideas?
Thanks, Rob.

---

### Post by Yellow Pasque on 2015-05-09
> Is there any way to find what driver Mint is using and copy it to Ubuntu?
The driver is a kernel module, and if Mint is based on Ubuntu kernel, they should be using the same module/driver.
Maybe alsa info will give a clue (or not): [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

