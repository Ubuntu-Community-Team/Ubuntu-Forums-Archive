---
title: "Constant screen freezes on Lenovo Z50."
date: 2015-10-11
forum: Hardware
---

### Post by Northernen on 2015-10-11
Hello.

I have a Lenovo Z50, on which I am running Ubuntu 14.04. I am suffering with constant screen freezes; it can happen 10+ times a day. It has to do with the graphics card, as the machine doesn't actually crash, just the display (so if Spotify is running, the music can still be heard, I just can't move the cursor).

Since I use an external monitor at home, I solve it by remove and re-inserting the HDMI cable, but when I am away, the only solution is to do a hard reboot. I've tried waiting it out, but having it stand over night, I've ascertained that it's not just intermittent.

I am running Nvidia prime. I have checked the syslog, but it doesn't say anything about the Nvidia drivers. I am getting errors on my network card, so I tend to stay away from using WiFi when possible. It probably either has to do with the Nvidia drivers, or with the network card.

I've included some dumps below. If you need more, please ask, as this is getting quite frustrating.

```
uname -a
Linux lenovo-z50 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

```
lspci | grep -i nvidia
03:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)

```

```
dpkg --get-selections | grep -i nvidia
nvidia-346                    install
nvidia-opencl-icd-346    install
nvidia-prime                  install
nvidia-settings               install

```

---

### Post by Northernen on 2015-11-02
Bump.

---

