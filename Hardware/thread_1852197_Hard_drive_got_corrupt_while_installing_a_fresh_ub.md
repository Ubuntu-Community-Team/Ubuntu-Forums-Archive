---
title: "Hard drive got corrupt while installing a fresh ubuntu 11.04. Need help to recover!!!"
date: 2011-09-29
forum: Hardware
---

### Post by tapas.dib on 2011-09-29
I was using ubuntu 11.04 along with windows as dual boot until today. I like to work more on ubuntu and I was having issues with my installation - error msg: \tmp not detected. So I decided to format my laptop and reinstall only ubuntu 11.04. 

During the installation I got an error and now the hard drive is corrupt and I am not able to mount it or format it either. Please help me solve this problem.

Thank you
Tapas

---

### Post by judoka9999 on 2011-09-29
Have you looked at the SMART errorlog on the device from the ubuntu live environment?

IE,
sudo apt-get install smartmontools
sudo smartctl -l error /dev/sda

It could just be the drive is dieing.

---

