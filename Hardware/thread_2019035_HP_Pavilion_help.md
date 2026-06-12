---
title: "HP Pavilion help"
date: 2012-07-06
forum: Hardware
---

### Post by TheKingOfComputers on 2012-07-06
What up guys I got a BIG issue tonight. So I just went out and bought a brand new HP Pavilion HPE 1210 desktop (costed me an arm and a leg...)  I get home and I use the pendrive thing on Ubuntu's website to try making bootable usb stick. My brand new install of Ubuntu's 12.04 64 bit iso is on there, and I go to boot from it... I click install and it starts going. Then, it freezes, a few blinking green cursors randomly appear on the code and my system freezes. The power button dont work, nothin. I had to unplug it. Now I try installing another iso, and my systems download speed is 1000% slower (going from 3142 kb/s to 102 kb/s after the defective install and force shut down)...

Any insight is graciously accepted.

---

### Post by Bucky Ball on 2012-07-06
Have you run Ubuntu directly from the dongle? Always a good idea before installing. Boot from the USB and 'Try Ubuntu', not 'Install Ubuntu'. Everything ok? If not, start working that out before install.

When you boot from the pendrive and get to the options screen, hit F6 and you will be presented with options. Choose 'nomodset' and continue. That may fix you install problem.

PS: When you are in the Live desktop from the USB, open Gparted (partition manager) and have a look at what is currently on the drive. You might want to wipe things, although this can all be done during install at the partitioning section if you choose 'Something Else' and partition manually rather than letting Ubuntu do it automatically (default setup totally unsuitable for me). 

Good luck. ;)

---

### Post by TheKingOfComputers on 2012-07-06
Ok I will try that. Im just extremely worried because this brand new $1100 machine with great Nvidia graphics and 8 gigs of RAM has just gotten considerably slower after the failed install and force shut down. Do you think I damaged my PC?

---

### Post by Bucky Ball on 2012-07-07
VERY Doubtful. You may just have confused the MBR or something. 

Try getting to a desktop by booting the LiveUSB and having a look in Gparted. If there's any residual partitions left over from the attempted install kill them. ;)

PS: Also, make sure you use the nomodset option if you're having trouble booting into anything after the options screen.

---

### Post by TheKingOfComputers on 2012-07-07
Ok thank you so much Bucky... Installed and my PC is working normally :)

---

### Post by Bucky Ball on 2012-07-07
Brilliant news! Please mark your thread as solved from 'Thread Tools' to help others and enjoy that sweet sounding machine ... ;)

---

