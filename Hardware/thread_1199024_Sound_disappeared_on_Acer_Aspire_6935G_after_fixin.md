---
title: "Sound disappeared on Acer Aspire 6935G after fixing problems with wifi adapter"
date: 2009-06-28
forum: Hardware
---

### Post by larinam on 2009-06-28
Hello.
Had problems with wifi, found solvage in installing package linux-backports-modules-jaunty.
wi-fi now doesn't disconnect after closing my laptop, all ok. But now i have no sound. After restart while playing mp3 or video with sound there was crackling from my speakers. After the next reboot sound dissapeared at all.
To get sound after first installation i followed thease instructions:
 [Finally I've added this lines at the end of: /etc/modprobe.d/alsa-base.conf ]("http://www.linlap.com/wiki/acer+aspire+6935g")
   [URL="http://www.linlap.com/wiki/acer+aspire+6935g"]alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1
options snd-hda-intel model=auto
options snd-hda-intel single_cmd=1[/URL] 
  [ and sounds works well, but no headphones ]("http://www.linlap.com/wiki/acer+aspire+6935g")

there were sound befor installing as i said  linux-backports-modules-jaunty. uninstallation of the package didn't return sound back.
now i have stable internet but no sound.
please, help solve my problem.

---

### Post by larinam on 2009-06-29
up. can somebody help me?

---

### Post by larinam on 2009-06-30
pump it

---

### Post by larinam on 2009-07-02
is useless to ask for help here?

---

