---
title: "Bluetooth headset pairs OK but no sound"
date: 2015-11-14
forum: Hardware
---

### Post by caffewmilk on 2015-11-14
Hi,

I ordered a USB bluetooth adapter for my laptop, plugged it in, and it was recognized right away.

So I proceeded to pair my bluetooth headset with the laptop. It paired fine but I get no audio through the headset.

Audio is still coming out through laptop speakers.

Laptop: Dell Latitude E6410
Distro: Ubuntu Mate 14.04, blueman and bluez tools are installed

Please let me know if you need more information.

Thank you.

---

### Post by jeremy31 on 2015-11-15
Post the result of ```
pactl list short
```

---

### Post by efflandt on 2015-11-16
I don't know what Mate uses for a desktop. But in Sound Settings, what is set as your Output device? When I used a wireless headset I had to manually select that device (it could do either analog or digital).

---

