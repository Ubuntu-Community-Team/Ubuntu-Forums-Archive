---
title: "Cnet CWD-845 driver"
date: 2010-07-18
forum: Hardware
---

### Post by ComputerJy on 2010-07-18
Hi all, need your help again

I've got a cwd-845 cnet wireless dongle. When I connect it to my computer, Ubuntu identifies it perfectly and I get "Wireless Network (Ralink 802.11g WLAN USB Dongle)" with a list of networks below. The thing is I cannot connect to any networks. It just the wlan icon shows like its trying to connect for a couple of minutes then I get "Disconnected" message. I tried it on another machine running Windows and it worked really fine. I hate this whole incompatible hardware thing

Please help. I've looked all around for instructions and I found how to build but I kept getting an error when running make. Any easier ways to install the driver?

Please

I'm running lucid: Linux 2.6.32-24-generic #38-Ubuntu SMP i686 GNU/Linux

---

### Post by ComputerJy on 2010-07-18
In case it helps, I tried using the module-assistant and got an error in the build phase

---

### Post by ComputerJy on 2010-07-19
Ok, After way too many tries I got it to work. All I had to do was install the package install linux-backports-modules-wireless-lucid-generic

> sudo apt-get install linux-backports-modules-wireless-lucid-generic

---

