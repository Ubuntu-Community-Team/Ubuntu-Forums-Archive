---
title: "ASUS K50IN Graphic card &amp; network problem"
date: 2010-09-19
forum: Hardware
---

### Post by AienTech on 2010-09-19
Hi
I just installed ubuntu 10.04 on my asus k50in, at first i had graphical bug, but i solved it, i'm now in ubuntu but in 800*600!!! in top of my screen i don't have "hardware driver" shortcut, and i cant run it from system> preference..!!!!

i run terminal and execute ```
sudo apt-get update
``` and it shows me: ```
"50 line of error"... W: Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```i can use "wget" to download files, but i can't use it(terminal, not "wget") to update or upgrade my system.

oh and my "software source", "synaptic package manager" cannot work, i think they use terminal.
and i'm new to linux and ubuntu :)

---

### Post by AienTech on 2010-09-19
Please!!!! help me!!! someone...

---

### Post by AlexC. on 2010-12-02
Hey AienTech! I have the same laptop as yours for work and I'm using the 10.10 maverick dist which does not appear to have these problems (I installed 10.10 directly). You can try and install that one from scratch or even update via apt-get but first run through these (have the cd in the cd-rom):

```

sudo apt-get check
sudo apt-get upgrade
sudo apt-get update

```

This should check, repair, update and upgrade the indexes. Then you could go for:
```

sudo apt-get dist-upgrade

```

Tell me if something else changed. You can PM me (or even add me on Yahoo if you want to discuss more about the k50in)

NOTE: maverick should also recognize your video card instantly (I'm guessing it's the same: G102M) and it should allow you to start "Additional Drivers" from where you can activate them.

---

