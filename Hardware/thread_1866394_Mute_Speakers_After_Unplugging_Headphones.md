---
title: "Mute Speakers After Unplugging Headphones"
date: 2011-10-21
forum: Hardware
---

### Post by GonzalitoUY on 2011-10-21
Just Updated from Natty (new installation, starting from scratch), and yesterday everything was fine, but just now I tested my headphones, and all is right...until I unplug them...then, no more seound from my speakers.
I check on alsamixer, before inserting the headphone jack, music is playing fine (picture 1), when I put the headphones, the speakers are muted as normal (picture 2), but then, when I unplug, the speakers are unmuted, but their volume is set as 0 (picture 3)?
I know the old "connect headphones, speakers are unmuted", but this is a new one for me, and didn't happen on 11.04
Laptop is a Dell M5010R (has to disable acpi to make it work, same as in 11.04, no other problems, sound was working fine), 11.10 64 bits, AMD Phenom X3, and here's the info from the sound card
```
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

```

---

### Post by robinlouis on 2011-11-15
I had the same problem. I managed to solve it by going to Sound Settings, under the Output tab, choose Analog Speakers from the dropdown menu and unmute volume. That should do it. Hope this works for you. By the way, I'm using Ubuntu 11.10, Gnome 3 on a Dell Vostro 1510.

Cheers.

---

