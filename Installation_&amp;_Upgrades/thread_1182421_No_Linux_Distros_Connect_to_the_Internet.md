---
title: "No Linux Distros Connect to the Internet"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by mcrisp5 on 2009-06-08
Hey,

I need some help. I recently bought a new Gigabyte motherboard (M61PME-S2P) and 4gb of ram. i intended to wipe the entire dual boot set up i had before and just run ubuntu 9.04 as the main operating system and have windows as a vm. problem is once i upgraded the hardware, the original copy of windows didn't work (kinda was expected) but ubuntu worked fine... exept it wouldn't connect to the internet. so i backed all my files up and wiped my internal drives. i installed a fresh copy of ubuntu 9.04 on my 40gb drive leaving the 250gb drive (which ubuntu waas on originally) for data.

on the live cd, the internet wasn't working. in the installation, the internet wasn't working either. so i tried mandriva, openSuSE 11.1, fedora 10 and Mint 7's live CDs all with the same issue. 

My guess is that the CDs don't come with the drivers for the intergated network on the gigabyte motherboard... and seeing how i can't connect to the internet, the drivers can't be downloaded. can anyone steer me in the right direction? i've been searching all the different forums for the past 2 days now. if i can't work it out... i'll try the next fedora. it's suppose to be released tomorrow i think..


cheers

---

### Post by cariboo on 2009-06-08
Could you open an Applications-->Accesories-->Terminal and type:

```
lspci
```

and paste the output in your next post.

---

### Post by sendblink23 on 2009-06-08
.. hope u manage to get it running

---

### Post by retrovelo on 2009-06-18
I have the same board, a Gigabyte M61PME-S2P, and both the 9.0.4 live CD and fresh install found the internet just fine. Is there perhaps  an issue with your LAN and/or DHCP?

---

### Post by markbuntu on 2009-06-18
Did you firewall your router?

---

