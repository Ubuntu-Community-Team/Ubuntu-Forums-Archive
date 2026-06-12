---
title: "PCMCIA USB 2.0 hub problem"
date: 2008-11-26
forum: Hardware
---

### Post by karpago on 2008-11-26
:confused:
I installed on my Compaq Armada E500 an USB 2.0 PCMCIA Cardbus 32 hub with 4 USB ports.

The card is not working on my laptop with Ubuntu 8.10 and to be sure that the card is not defective I tested it positively on a different laptop with Windows XP.

Reading dmesg log it seems that there are some errors in reading my USB flash disk that is perfectly working if I connect it to the on board USB 1.1. port or to any USB 2.0 port on other PCs.

As I'm absolutely a novice with linux/Ubuntu system I hope in your help.

I attached two dmesg log: the first one when I connect the USB disk on the hub and the second one when I connect it to the standard USB port on the motherboard.

Many thanks

---

### Post by karpago on 2008-11-28
Someone can help me?

Thanks

---

### Post by karpago on 2008-12-02
No help?

---

### Post by karpago on 2008-12-09
Very good forum .....

Thanks for your help.

---

### Post by Marblemike on 2008-12-13
Hi there.

I've been having a similar problem and haven't got any help either - I don't think many people use pcmcia cardbus adapters. I actually use kubuntu so described my problem here: [http://kubuntuforums.net/forums/index.php?topic=3100116.new#new]("http://kubuntuforums.net/forums/index.php?topic=3100116.new#new").

What I've found out is that the device is installed, just extremely slow. Whenever you plug something in, you have to detect it by typing "sudo lsusb" a few times. Somehow, that causes the device to be detected. It may seem like it is not responding while doing the lsusb, but it is. You can watch what's happening using a kernel log program, I use KSystemLog in KDE, I'm not sure what you'd use in gnome.

Anyway, it takes ages, but eventually your mouse/flash disk etc starts to respond. Unfortunately, its completely useless because its so slow you can't do anything. The mouse has visible jumps and is uncontrollable because of the slow device. I also tested it under XP, where it is fast so its definitely a linux issue.

Please let me know if you come across anything that helps, I'll keep looking myself.

---

