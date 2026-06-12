---
title: "AsRock Q1900-ITX no Sound via HDMI"
date: 2016-01-21
forum: Hardware
---

### Post by TimHf on 2016-01-21
Hi,

I have a problem with my new Media Center PC based on a Q1900-ITX Board by AsRock
I have no sound via HDMI. First I tried it with Kodibuntu, then with Ubuntu 15.10.

aplay -l does not show any HDMI Audio devices only the 7.1 Sound Chip. 

It seems that there is a problem with the driver. 
Under Ubunutu I installed the Intel Graphics for Linux, provieded by  01.org, with no improvement. With Kodibuntu it was not possible...

Is someone using the same mainboard with working audio? Or has somebody else an idea?

Thank you!

Tim

---

### Post by Yellow Pasque on 2016-01-21
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Vladlenin5000 on 2016-01-21
Are you sure you have enabled "Onboard HDMI HD Audio" at UEFI (Advanced tab)? It is usually disabled by default...

---

### Post by TimHf on 2016-01-22
> **Vladlenin5000 said:**
> Are you sure you have enabled "Onboard HDMI HD Audio" at UEFI (Advanced tab)? It is usually disabled by default...

Thank you Vladlenin! This was die solution

---

