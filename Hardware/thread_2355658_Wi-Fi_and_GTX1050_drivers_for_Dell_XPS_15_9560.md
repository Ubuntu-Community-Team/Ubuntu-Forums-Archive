---
title: "Wi-Fi and GTX1050 drivers for Dell XPS 15 9560"
date: 2017-03-15
forum: Hardware
---

### Post by pieter512 on 2017-03-15
Hi, 
I just installed Ubuntu 16.04.2 LTS on my new Dell XPS 15 9560 (2017), in dual-boot with Windows 10.
I'm having problems with the Wi-Fi and GPU drivers:
5GHz Wi-Fi networks work fine, and network-manager lists all 2.4GHz networks, but I can't connect to my 2.4GHz network, it just fails to connect, and asks for my wireless encryption key again and again. I'm assuming that this is a driver issue, since it does work in Windows. 
My network card is a Killer Wireless-AC 1535 (Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)).

The second problem is my NVIDIA GTX1050: If I go to System Settings > Software & Updates > Additional Drivers, no graphics drivers are listed, just the Processor microcode firmware for Intel CPUs. Is there an official repository to get the NVIDIA driver? Or should I just download it from the NVIDIA site. (I haven't done this yet, because the .run drivers from NVIDIA have bricked my previous system in the past.)
I need the CUDA toolkit as well. Does this include the drivers, or do I have to install them separately?

Thanks, 
Pieter

---

### Post by Autodave on 2017-03-15
For the Nvidia card, I would try the repositories first: there are numerous drivers there. The very last thing I would try would be the drivers from Nvidia's website.

As for the WiFi, I am no expert there at all. But, I have a Dell laptop. And I have / had the same problem as you. I have installed 16.04 Ubuntu and Xubuntu on it since I received it. And, I have had to re-enter the wireless password 10-15 times before it accepts it. Why? No idea. I just know that I have had to do it and eventually it worked.

---

### Post by pieter512 on 2017-03-15
Thanks for your reply!

> **Autodave said:**
> For the Nvidia card, I would try the repositories first: there are numerous drivers there. The very last thing I would try would be the drivers from Nvidia's website.
What repository? This one? [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/375.39-0ubuntu2](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/375.39-0ubuntu2)
Do I just run apt-get install nvidia-375 libcuda1-375 ? Why doesn't it show up in the additional drivers window?

> **Autodave said:**
> [COLOR=#000000] And, I have had to re-enter the wireless password 10-15 times before it accepts it.
[/COLOR]Tried that, doesn't work. :(

Pieter

---

### Post by Yellow Pasque on 2017-03-15
> **pieter512 said:**
> Do I just run (sudo) apt-get install nvidia-375 libcuda1-375 ? 
Yes.

> Why doesn't it show up in the additional drivers window?
Because the card is relatively new compared to the information in the (PCI ID) database Ubuntu's utility uses to match cards with drivers. It seems they don't update it after release. [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1639019](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1639019)

---

### Post by pieter512 on 2017-03-16
I installed the Nvidia drivers: first I tried nvidia-378 but that bricked my system, then I installed nvidia-375 from the shell and that fixed it. CUDA works as well, but I haven't installed the toolkit yet, because I didn't want to brick it again.

The first thing on my list is now the Wireless driver. Currently, I'm using my phone to tether over USB, which is extremely inconvenient. How should I fix this?

Thank you for the replies,
Pieter

Update: since I installed the NVIDIA drivers, Unity is completely messed up every time I resume from stand-by...

---

