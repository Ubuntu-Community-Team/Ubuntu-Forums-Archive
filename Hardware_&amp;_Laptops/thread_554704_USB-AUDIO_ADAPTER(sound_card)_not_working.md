---
title: "USB-AUDIO ADAPTER(sound card) not working"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by magarwal on 2007-09-19
I have an ACER Laptop with Intel Pentium M725 Processor(1.6 Ghz).....whose inside soundcard(Realtek) accidently stopped working due to some power distortion.So, i purchased an USB audio adapter(5.1 surround card) from market but its not working in ubuntu.although the sound card is detected by the system and it shows it as C-Media USB HeadPhone set (Alsa mixer) and the other sound card is also shown as Realtek alc260(OSS mixer) ...the realtek is the inside one which had stopped working ...so do i have to disable the realtek one to make the USB one work..???please help me...??

---

### Post by KalTorak on 2007-12-07
work with alsa-base in modprobe.d
take a look here at my post [http://ubuntuforums.org/showthread.php?t=492241]("http://ubuntuforums.org/showthread.php?t=492241")

---

