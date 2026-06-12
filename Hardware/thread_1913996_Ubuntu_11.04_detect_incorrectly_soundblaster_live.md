---
title: "Ubuntu 11.04 detect incorrectly soundblaster live"
date: 2012-01-23
forum: Hardware
---

### Post by robson22 on 2012-01-23
Welcom 
First thing is sorry about my english.

When i use command: lspci | grep audio
the result is
```
[00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
```
this is my integred sound card.
When i use command: lspci
the result is
```
01:06.0 Unassigned class [ffff]: Creative Labs SB Live! EMU10k1 (rev 0a)
```

Please help.

---

### Post by MoreOrLess on 2012-01-23
Are you having issues related to this? If not, don't worry about it. One thing you can try is updating the pci ids
```
sudo update-pciids
lspci
```

---

### Post by robson22 on 2012-01-23
Yes I have issues with that. I dont have sound:(. Alsamixer dont detect soundblaster live. I try the: sudo update-pciids, lspci and nothing change.

---

### Post by MoreOrLess on 2012-01-24
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by robson22 on 2012-01-24
Here is output from this scripts:
[http://www.alsa-project.org/db/?f=e7448f50f23bfd001115ae22505a3fd6e17edac8](http://www.alsa-project.org/db/?f=e7448f50f23bfd001115ae22505a3fd6e17edac8)
I look it and recognised cards is only NVidia nForce2 with ALC650F.
There is no soundblaster live:cry:

---

### Post by bluexrider on 2012-01-24
go to your sound preferences and under Hardware check Profile. you should have a list of compatible configurations.

Here is a manpage [http://manpages.ubuntu.com/manpages/natty/man4/snd_emu10kx.4freebsd.html](http://manpages.ubuntu.com/manpages/natty/man4/snd_emu10kx.4freebsd.html)

---

