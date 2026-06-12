---
title: "Solution for old sound cards! (ISA)"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by Pjotr123 on 2007-01-03
Finally! An easy solution for installing old sound cards with an ISA connection. Using alsaconf, which was sadly missed in the newer Ubuntu releases. No need to buy a new PCI sound card anymore!

Thanks to Dennis Kaarsemaker, a moderator from Ubuntu Netherlands. He has been so kind as to create self-installing packages with alsaconf in them, both for Ubuntu 6.06 (Dapper Drake) and for Ubuntu 6.10 (Edgy Eft). He has made them available for download on his website.

You can get them here:
Ubuntu 6.06 (Dapper Drake):
[http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.10-1ubuntu14seveas1_i386.deb](http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.10-1ubuntu14seveas1_i386.deb)

Ubuntu 6.10 (Edgy Eft):
[http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.11-6ubuntu2seveas1_i386.deb](http://seveas.ubuntulinux.nl/~dennis/alsa-utils_1.0.11-6ubuntu2seveas1_i386.deb)

How to use:
- download the file
- start a graphical explorer with root rights: 
in the terminal: gksudo nautilus
- doubleclick the file
- after installation: in the terminal:
sudo alsaconf
- make no own choices in the questions you are asked, always accept the proposed answer

Ready! Your old ISA sound card makes sound again!

Greeting, Pjotr.

---

### Post by Quillz on 2007-01-09
Before I try this, would you happen to know if this will fix my sound card? I have this one: ```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

```

---

### Post by halitech on 2007-03-04
thank you for this, it worked like a charm in Xubuntu 6.06 with an Opti 16 ISA sound card. now I just need to install thge codecs so I can actually listen to something :)

---

### Post by halitech on 2007-03-30
It's gone :(

does anyone know how to get an Opti 16 sound card working? I know I should get a PCI card but it's for my nephew and I'm broke and have 2 of these cards I'd rather use if possible. I had the file listed above and I have emailed the webmaster to see if he still has it but would like to get it going again this weekend.

---

