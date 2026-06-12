---
title: "Installation of 10.04 hangs at 89% on HP Pavilion zd7000"
date: 2010-05-03
forum: Hardware
---

### Post by noway on 2010-05-03
The laptop used to have 9.04 which worked just fine. I decided to upgrade to 10.04 so I downloaded ubuntu-10.04-desktop-i386.iso and did a clean install, removing everything from the hard drive. At 89% when it says "looking for packages to remove" the installation hangs.

---

### Post by noway on 2010-05-03
I tried with ubuntu-10.04-alternate-i386.iso and now it stops at 82% during: Configuring software-center

---

### Post by antmenj on 2010-05-03
It died at 89% for me so your not the only one.  Hardy was very rough around the edges at first but after 8.04.2 it wasn't bad.  I'm not about to trash my old install just yet.

---

### Post by noway on 2010-05-05
I solved this by doing a command line install and then **sudo aptitude install ubuntu-desktop**. The option for advanced install didn't show up in my native language so I needed to choose english when it asks for language in the beginning, then I could choose whatever language for the actual system. Possibly related to this bug [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/573764](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/573764)

Ubuntu is now installed and works fine.

---

### Post by Niets on 2010-06-08
I have a zd7000 with the same problem and the alternate ISO CD worked just fine.

---

