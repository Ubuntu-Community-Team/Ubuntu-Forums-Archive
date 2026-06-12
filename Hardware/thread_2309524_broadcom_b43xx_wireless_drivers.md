---
title: "broadcom b43xx wireless drivers"
date: 2016-01-11
forum: Hardware
---

### Post by timotheus3 on 2016-01-11
[B]percieved problem:
[/B]
my wireless card is a broadcom b4318, which did not work out of the box and i tried getting the linux drivers to work but i couldnt get it sorted so i just went for the old ndiswrapper option. which works fine,

what i would like to know is is there any advantage to use the proper linux drivers? does it effect speed, because i would like to use the linux drivers but im pretty novice and its all a bit much without clear specific instructions.

**solution: **

it was my fault, i made the amatuer mistake of forgetting to reboot after trying to install the packages for my wireless firmware, I also may have messed something else up following the misleading instructions on  finding the right firmware driver of an error message while booting up, and subsequently trawling the internet for solutions

i retried and it seems to be working fine now unencryped and with WPA-PSK with no extra config needed by installing the packages:

b43-fwcutter
firmware-b43-installer
[I]

i edited out the other question about Sis Video card[/I]

---

### Post by Bucky Ball on 2016-01-11
Welcome. You have two issues here. The network question should be posted in ***Networking and Wireless***. 

I advise you improve your chances of support by editing out the network question(s) and posting them there. We prefer one support issue per thread as it avoids confusion and gives you the best chance of getting support. Good luck.

---

### Post by mörgæs on 2016-01-12
This should give some inspiration:
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

