---
title: "Headphone jack won't work, sony vaio ar520e"
date: 2009-02-07
forum: Hardware
---

### Post by Yahthatsme on 2009-02-07
Using ubuntu 7.10. Tried both ALSA and OSS, tried having the headphones plugged in from the start, muting and unmuting master volume/headphone volume. OSS doesn't even have a headphone option. At a loss here, I'm rather new to linux still. Thanks!

---

### Post by dox_drum on 2009-02-07
Check that the capture entry in alsamixer has volume.

Write in the terminal

```
alsamixer
```

and with the Tab key change to Capture. For giving or taking out volumen use the up, down arrows.

Hope will be that simple.

Enjoy.

---

### Post by Yahthatsme on 2009-02-07
> **dox_drum said:**
> Check that the capture entry in alsamixer has volume.

Write in the terminal

```
alsamixer
```

and with the Tab key change to Capture. For giving or taking out volumen use the up, down arrows.

Hope will be that simple.

Enjoy.

Ok, I tried that, still no headphone sound. Upgraded to 8.04 LTS to see if that would help, still nothing.

---

### Post by dox_drum on 2009-02-07
Try with the following HowTo

[[COLOR="Navy"]http://ubuntuforums.org/showthread.php?p=4928900[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4928900")

It help me a lot.

Regards.

---

