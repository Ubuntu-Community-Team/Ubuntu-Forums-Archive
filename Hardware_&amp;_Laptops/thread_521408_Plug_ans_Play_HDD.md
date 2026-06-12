---
title: "Plug ans Play HDD"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by JParkus on 2007-08-09
I got stuck working on my wife aunts computer (XP system AMD Athlonx2 2gig RAM). Since I had it I figured I would see if my HDD would boot and to my suprise it did ! All I had to do was "sudo dpkg-reconfigure -phigh xserver-xorg" . I was just wondering how many people knew about this and what is the limit. I only have a P3 with a gig of ram and never expected it to reconfigure itself to boot a machine thats 8 years newer.

---

### Post by kidders on 2007-08-10
Hi there,

What do you mean by "what is the limit"?

It's probably worth pointing out that an install from a P3 won't run terribly well on an Athlon X2, since it'd be the wrong bitness ... but it ought to at least work.

---

### Post by JParkus on 2007-08-11
By the limit I mean CPU and it seemed to work well after I changed some of the settings and rebooted.

---

### Post by kidders on 2007-08-11
Well, "sudo dpkg-reconfigure -phigh xserver-xorg" does nothing except reset the configuration of your X server, so it doesn't have much to do with your CPU. Ubuntu will run on a wide range of processors however, within the limits of its system requirements. ([https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements))

---

