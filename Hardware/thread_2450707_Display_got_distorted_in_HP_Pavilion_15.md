---
title: "Display got distorted in HP Pavilion 15"
date: 2020-09-19
forum: Hardware
---

### Post by rintu6329 on 2020-09-19
Ubuntu Version - 20.04 LTS 
Laptop Maker - HP
Laptop version - pavilion 15 ec-0062ax
Cpu - Ryzen 5 3550H with vega 8 graphics 
Gpu - Geforce GTX 1050 3GB Max-Q
Ram - 8gb 2400MHz DDR4.


I just bought the laptop and dual booted Ubuntu 20.04 LTS with Win10. After installation of Nvidia driver the Nvidia settings page appeared blank but the issue was fixed because I found the solution in askubuntu.
Now that I can access the Nvidia settings but after a week when I tried to log in, the screen displayed like this [https://ibb.co/ZLnTrz1](https://ibb.co/ZLnTrz1) 
Then I tried adding nomodeset in the grub and reinstalling the Nvidia driver but neither of them solved the issue. So I fresh installed Ubuntu again without installing the Nvidia driver but it didn't work and the same issue appeared again.

---

### Post by CelticWarrior on 2020-09-19
Welcome.

What was that solution you found at AU exactly?
How are you installing the Nvidia drivers and which version?

---

### Post by rintu6329 on 2020-09-19
This is the solution i found i ask ubuntu - [https://askubuntu.com/questions/1177248/nvidia-gtx-1650-not-detected-in-ubuntu-18-04-3](https://askubuntu.com/questions/1177248/nvidia-gtx-1650-not-detected-in-ubuntu-18-04-3))
And i installed the driver through additional driver and the version is 440. tried 435 but same thing happened.

---

### Post by CelticWarrior on 2020-09-19
Did you disabled Secure Boot in UEFI?

---

### Post by rintu6329 on 2020-09-20
Ya i did

---

