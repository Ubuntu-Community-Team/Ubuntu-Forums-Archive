---
title: "Installing new NIC - boot problems"
date: 2011-11-30
forum: Hardware
---

### Post by Raf Berkvens on 2011-11-30
Hi all

This is my very first Ubuntu Forums post. I hope I follow every convention correctly.

I have a Ubuntu 10.04.3 Server running on an old machine of mine. I installed it with a PCI wireless network interface card which was completely out of order. There is an extra wired network interface directly on the motherboard which I use to access the server with SSH. 

Recently I obtained a used wireless network interface card. This card was operational when the machine it belonged to went out of use. I plugged the card into the Ubuntu Server machine and tried to boot, to no avail. I get BIOS beeps, POST runs, Ubuntu sometimes get to the part where it outputs "init: ureadahead main process (xxxx) terminated with status 4" ([which is not causing the boot failure]("http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04")) and sometimes even "AppArmor" is launched. But most of the time it crashes before that. Whatever happens, I never get so far as being able to log in.

Some more on the server machine: the reason I made it a server was that the video card had crashed. I run only in command line.

Technical specs:
Ubuntu 10.04.3 LTS
old NIC: Linsys WMP54G (antenna broken)
new NIC: Skyr@cer Pro PCI 154 
there is no wlan0 device installed

TL;DR: Ubuntu won't start after wireless network card plugged into PCI slot.

PS: I have no graphical interface. If you would have me try something, please include command line input.

---

### Post by Raf Berkvens on 2012-02-05
Bump?

---

