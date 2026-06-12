---
title: "No sound coming from speakers!"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by xtxzt on 2008-02-09
I have an[ HP  Pavilion dx6650us laptop]("http://reviews.cnet.com/laptops/hp-pavilion-dx6650us-core/4505-3121_7-32722189.html") and no sound is coming from the built in speakers! It worked fine when I first installed Ubuntu but now I can't hear any sound. Not even the system beep for some reason. Did I mess up the drivers for it? How can I fix this? Please help. I want to avoid a complete reinstall of Ubuntu... :confused:

---

### Post by tangibleorange on 2008-02-09
What happens when you type this in a terminal:

> alsamixer

---

### Post by xtxzt on 2008-02-09
> **tangibleorange said:**
> What happens when you type this in a terminal:

I get this:

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: Realtek ID 268                                                         &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]                                            &#9474;
&#9474;                                                                              &#9474;
&#9474;                       &#9484;&#9472;&#9472;&#9488;                        &#9484;&#9472;&#9472;&#9488;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;
&#9474;                       &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;                       &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                     100<>100                    100<>100                     &#9474;
&#9474;                    < Master >                     PCM                        &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by Yellow Pasque on 2008-02-09
Upgrade to ALSA 1.0.16 with these scripts (very easy)
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

Also, try adding "options snd-hda-intel model=3stack" into the /etc/modprobe.d/alsa-base file.

---

### Post by xtxzt on 2008-02-09
> **Temüjin said:**
> Upgrade to ALSA 1.0.16 with these scripts (very easy)
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

Also, try adding "options snd-hda-intel model=3stack" into the /etc/modprobe.d/alsa-base file.

Upgrading ALSA didn't work and when I try to save als-base it tells me that I don't have permissions.

---

### Post by Yellow Pasque on 2008-02-09
You need to open alsa-base with sudo gedit. Also, check the mixer again to make sure things aren't muted. (ALSA has a nasty habit of doing that).

---

### Post by xtxzt on 2008-02-09
> **Temüjin said:**
> You need to open alsa-base with sudo gedit. Also, check the mixer again to make sure things aren't muted. (ALSA has a nasty habit of doing that).

Okay, I edited alsa-base, but now when I try to start the mixer I get this:
alsamixer: function snd_ctl_open failed for default: No such file or directory

EDIT: Alsamixer now works after a restart and I've made sure its not muted, but I still don't hear any sound. :(

---

### Post by xtxzt on 2008-02-13
*bump*
Please help! :(

---

