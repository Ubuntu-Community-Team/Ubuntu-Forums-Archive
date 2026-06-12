---
title: "[PSA] Fix for the dreaded ESSX8336 for Ubuntu (And all Debian based distros, really)"
date: 2023-04-30
forum: Hardware
---

### Post by nebratheforsaken on 2023-04-30
Greetings. I do apologize if I have created this thread in a wrong category, but I figured hardware section would be appropriate for this.

If you are like me, and have the God forsaken ESSX8336 chip in your laptop, fear not, you can finally have sound just by running a few scripts.

gnickm on github has been gracious enough to create a comprehensive guide on how to get the chip working. I cannot for the life of me remember where I found this repo, and I wished I have found it long ago, because he has created this almost a year ago.

[https://github.com/gnickm/sof-essx8336-debian-fix](https://github.com/gnickm/sof-essx8336-debian-fix)

**NOTE**: If you are running kernel version 5.17 or newer, you can skip step 3 in his instructions. With 22.04 and newer versions of Ubuntu running kernel versions well newer than 5.17, I'd imagine pretty much everybody would want to do this.

P.S. - I genuinely wish this guy had his paypal on his github profile so that I can tip him. Everybody who has this sound chip knows the pain, but thanks to this guy, the pain is finally over. On behalf of all of us stuck with this sound chip, thank you, gnickm <3

---

### Post by rzg01 on 2023-08-05
Great ! Worked in Debian 12.


These days there was an update of the Kernel and the sound began to work (I'm not sure how this happened). But in this version from github the volume got louder.


Although the sound is working, the sound is very shrill (at least in my case).


Thank you.

---

### Post by rcbrandao on 2023-10-19
On Ubuntu 23.10 all I had to do was run the setup-alsa.sh script ([https://raw.githubusercontent.com/gnickm/sof-essx8336-debian-fix/main/setup-alsa.sh](https://raw.githubusercontent.com/gnickm/sof-essx8336-debian-fix/main/setup-alsa.sh)). That alone fixed my sound problem. I'm on a live session and it still worked. No reboot required.
Thanks!

---

