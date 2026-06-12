---
title: "AMD Unsupported hardware"
date: 2014-01-23
forum: Hardware
---

### Post by ziman19962 on 2014-01-23
I recently switched from windows to Ubuntu 12.04. I have a Radeon R9 270X, I installed the drivers from the prompt that came up on the top right corner of the screen but when I restart it still has the watermark. Is there a way I can fix this?

---

### Post by ziman19962 on 2014-01-23
Bump. I really need help

---

### Post by sandyd on 2014-01-23
Instructions at [http://ubuntuforums.org/showthread.php?t=2074962](http://ubuntuforums.org/showthread.php?t=2074962)

If you need help applying them - post the output of
```

cat /etc/ati/signature
```

---

### Post by ziman19962 on 2014-01-23
> **sandyd said:**
> Instructions at [http://ubuntuforums.org/showthread.php?t=2074962](http://ubuntuforums.org/showthread.php?t=2074962)

If you need help applying them - post the output of
```

cat /etc/ati/signature
```
So I need to use the beta drivers?

---

### Post by ziman19962 on 2014-01-23
I have the drivers installed on my system using the additional drivers thing, but the watermark is still there.

---

### Post by ziman19962 on 2014-01-23
> **sandyd said:**
> Instructions at [http://ubuntuforums.org/showthread.php?t=2074962](http://ubuntuforums.org/showthread.php?t=2074962)

If you need help applying them - post the output of
```

cat /etc/ati/signature
```
 Also those drivers are old.

---

### Post by sandyd on 2014-01-24
no - instructions on how to remove the watermark are there - dont do the driver install but the instructions on how to remove the watermark
Basically
replace the UNSIGNED line in /etc/ati/signature
with
```

9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc
```

You can get newer drivers at [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) if you want, that may support your card

---

