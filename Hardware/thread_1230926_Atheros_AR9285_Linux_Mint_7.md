---
title: "Atheros AR9285 Linux Mint 7"
date: 2009-08-03
forum: Hardware
---

### Post by Wamellx on 2009-08-03
I am a Linux beginner (I still use Windows as my main, but I have Ubuntu 9.04 on my comp). I recently installed Linux Mint 7 on my friends laptop. I understand this is just ubuntu with some extra features and it still has the reliability and even more usability than ubuntu. He was floored with how stunning it looks, though, not with the fact that the Atheros AR9285 wireless card in his HP Pavilion DV6 laptop. I tried installing MadWifi, didn't work. I tried the "sudo apt-get install linux-backports-modules-jaunty" fix, didn't work. I know this is a problem with the gnome kernel, I just don't know what to do about it. I am a beginner so if you could make you fix as easy as possible it will be greatly appreciated. I am really close to just putting Vista back on his comp. Thank you.

---

### Post by glide on 2009-08-26
I also have AR9285 device on a eee1005 laptop,
I am using Jaunty and it's not detected.
[quote="lspci | grep -i network"]
AR9285 Wireless Network Adapter (PCI-Express)
[/quote]

---

### Post by Mizukusai on 2009-09-23
Activate "backports" repository and install 
linux-backports-modules-jaunty

---

