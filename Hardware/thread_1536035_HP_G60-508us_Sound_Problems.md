---
title: "HP G60-508us Sound Problems"
date: 2010-07-21
forum: Hardware
---

### Post by thelethargarian on 2010-07-21
I have had my HP G60-508us laptop computer for just about a year. I have ran both Ubuntu and Xubuntu on it. The only problem it has that bothers me is that plugging something into the headphone jack doesn't mute the built-in speakers. I know that there are *many* threads about this, but none of them seem to have the solution for my laptop. The only one that has some success is adding
```

options snd-hda-intel model=dell-vostro enable=1 index=0

```
to **/etc/modprobe.d/alsa-base.conf**. It enables the mute function when headphones are plugged in, but then the microphone (both built-in and jack) stops working. Does anyone know what model name might work for my computer?


Running
```

cat /proc/asound/card0/codec#* | grep Codec

```
returns
```

Codec: Conexant ID 5067
Codec: Intel G45 DEVCTG

```

Thank You for any help you can give!

---

