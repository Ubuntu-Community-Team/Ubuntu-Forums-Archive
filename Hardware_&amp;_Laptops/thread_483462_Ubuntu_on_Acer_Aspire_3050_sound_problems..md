---
title: "Ubuntu on Acer Aspire 3050 sound problems."
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by A.P. on 2007-06-24
I've look around here a bit before registering and I've seen a few people who have problems with their sound on the above mentioned laptop. I managed to install Ubuntu perfectly fine and everything works except... The only way I get sound is by plugging in my head phones. I assume this means Ubuntu is detecting my sound card on my laptop it's just not configured correctly. I've heard about this "acpi=off" thing one can do when installing Ubuntu. So I tried this I reinstalled and when booting the Live CD I pressed F6 in order to bring up that command line like thing. Apparently you are supposed to add "acpi=off" on the end of there and sound should work. But it didn't. How ever it did work on PC Linux OS 2007 on the same machine. So I think perhaps I just have not typed "acpi=off" in the correct place when installing Ubuntu. Could someone perhaps post an example of the typical line of text that should be in that place along with where "acpi=off" should be put?

---

### Post by A.P. on 2007-06-24
Anyone?

---

### Post by rob-acer on 2007-07-03
A.P.

I have an Acer 3050-1150 with the same problem.  Try adding the following two lines to the end of the alsa-base file using sudo gedit. This file is located in /etc/modprobe.d/alsa-base:
```

alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3
```

This worked for me and I now have full sound.

There are several posts on sound problems with the Acer 3050 and a moderator should probably consolidate them.

- Rob

---

