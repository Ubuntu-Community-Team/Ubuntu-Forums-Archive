---
title: "Acer Extensa 5230 wireless lan working in Hardy"
date: 2009-02-21
forum: Hardware
---

### Post by magic-neophyte on 2009-02-21
Dear people,

Found such a simple fix for enabling the wireless lan (wlan) on my Acer laptop, running Ubuntu Hardy Heron 8.04.2 LTS, that I simple have to share it. First make sure you are connected to the internet using a regular network cable. 

Update your PCI ID's (so Ubuntu will identify your network hardware properly) by typing in a terminal:

sudo update-pciids

Now you can see what kind of wlan chip is in your laptop.

lspci | grep Ath 

[...]
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
[...]

You need the ath9k driver for this device. There are many complex instructions on the internet to compile it yourself. However, it is also included in the Ubuntu backports. Enable backports in Menu > System > Administration > Software Sources > tabsheet Updates [enable Unsupported updates (hardy-backports)]

Then update your package lists using: sudo apt-get update

To install the ath9k driver, type: sudo apt-get install linux-backports-modules-hardy

Now reboot and the wireless lan light should turn on. You can now use the network manager to connect to your wireless network. 

Enjoy! If you still have problems with this exact hardware and Ubuntu version, let me know, so I can update this fix.

---

### Post by tarcbram on 2009-11-20
Hi,
I have exact the same hardware and ubuntu version and I followed the simple procedure explained.

At the end the signal strenght is about 50% and the wireless lan works only when I'm very close to the wireless access point.

When the laptop is 3/4 meters far from access point the signal strenght is 0% and the wlan doesn't work.

Could you help me to solve the problem.

Thanks in advance for any help/suggestion.

---

