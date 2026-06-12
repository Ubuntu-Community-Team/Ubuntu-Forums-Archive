---
title: "WIFI keeps disconnecting randomly"
date: 2015-06-17
forum: Hardware
---

### Post by plymaker100 on 2015-06-17
I'm using xubuntu 14.04 and I have updated my Kernel 3.18 after updating WIFI keeps disconnecting in short times and I have to close and open it again to connect to my router  Note: it disconnects from my router only and when I close it and open it it connects again I'm using Toshiba Satellite C655D-S5508

---

### Post by Pilot6 on 2015-06-17
What is the point of installing an unsupported kernel?

You can install a supported 3.19 by

sudo apt-get install linux-generic-lts-vivid

And also give output of

lspci -knn | grep Net -A2

this will show what wireless adapter you have.

---

