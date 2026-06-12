---
title: "Compaq laptop issues."
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by Thesuperchang on 2007-11-12
Hello, I have a Presario V3021AU laptop:
Spec..
CPU - AMD Turion X2 @ 800Mhz per core
RAM - 512MB DDR2
HDD - 160GB Samsung
Graphics - Nvidia 6150 Go 256MB

Anyways, I'm running Ubuntu 7.10 Gutsy Gibbon 32-bit edition. My problems are that;
1. I can't seem to install anything with the "Sudo" command stuff. This is stopping me from getting the latest graphics drivers and what not.

2. My wireless connection isn't working. It was working when I had XP going but not with Ubuntu. I've found a google article that explains how to get it up and running but that requires me being able to install via use of the terminal.

Thanks in advance.
C. Anderson

---

### Post by DeadToad on 2007-11-12
If you can't get wireless to work, then simply plug the ethernet cable from your modem/router into the wired network jack on the laptop to access updates via the terminal window.
Good luck.
DeadToad

---

### Post by Thesuperchang on 2007-11-12
I've got the laptop wired now so I got internet and I've also figured out why it would install any updates. This is corrected but I can't seem to get the ndiswrapper utility. I type in
sudo apt-get install ndiswrapper-common
it does its thing then acts for the Ubuntu 7.10, I insert the disk and then nothing! Any suggestions?

Thanks in advance,
C. Anderson.

---

### Post by Thesuperchang on 2007-11-13
Never mind, I figured it all out. I uninstalled the Gnome network manager and installed a different programme call witch which recognized my wireless card instantly. I'd recommend this programme to anyone who can't get Ubuntu's stock programme to work with their card.

---

