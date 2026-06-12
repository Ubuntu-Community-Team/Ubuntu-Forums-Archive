---
title: "Samsung N150 wifi problem (total newbie)"
date: 2011-06-14
forum: Hardware
---

### Post by wilbur-force on 2011-06-14
Hi. I recently (successfully) installed ubuntu via wubi on my Dell.

I then managed to convince my wife to let me install it on her Samsung N150 - claiming it would speed up her web browsing.

Two days later and i still cant get her wifi to work :(  ive googled loads. I have updated to 10.10 and i have (i think) installed Broadcom drivers. Ive also checked for hardware drivers and its telling me 'no proprietory drivers'.

Can anyone help ? Please be gentle .... ive been tinkering with Linux a bit, and adb to Android, but im way off being classed as an xpert :p

---

### Post by walt.smith1960 on 2011-06-14
Hi and welcome.  The standard first step is to open a terminal and type this: "lspci".  Copy and paste the results.  You should see a line about "network controller".  This will be the identity of your wireless device.  Even though the machine is a Samsung the wireless chip may be something from Broadcom, Atheros, Ralink, RealTek or Intel.  Broadcom has several different chips that may have different software and installation procedures such as the need to blacklist other interfering software.

---

### Post by lorebett on 2011-06-15
Hi
wireless on N150 works for me... it worked on Kubuntu Maverick and it works after upgrade to Kubuntu Natty... are you sure that wireless is enabled in network settings?

---

