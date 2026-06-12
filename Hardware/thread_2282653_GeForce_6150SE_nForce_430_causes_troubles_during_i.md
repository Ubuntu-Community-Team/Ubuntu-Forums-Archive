---
title: "GeForce 6150SE nForce 430 causes troubles during installation"
date: 2015-06-15
forum: Hardware
---

### Post by dolphintweety on 2015-06-15
Is there a way to install Ubuntu with the Nvidia drivers already loaded? During my first login to my desktop right after installation of Ubuntu 14.04, the screen froze completely and I had to press the power button to turn off the computer - keyboard and mouse frozen as well. I didn't experience such problems in 12.04. Finally, I was able to enable the proprietary nVidia driver really quick after login. I also experienced the same problem with Linux Mint (just installed it out of curiosity ;)) yet even WORSE: I couldn't even login to cinnamon. I had to boot into root terminal and install those damn drivers following some instructions I found through Google. 

It's working now but it would be nice to load the drivers during installation.

*PS: My next computer won't have any Nvidia [-(*

---

### Post by Vladlenin5000 on 2015-06-16
Ubuntu doesn't install nvidia drivers by default but I thought Mint did?... :confused::confused::confused:

---

### Post by VMC on 2015-06-16
I have the same integrated video. I use 'nomodeset' at the end of the 'linux' line of grub. Then from terminal "sudo apt update". After that, I can install nvidia drivers.

---

