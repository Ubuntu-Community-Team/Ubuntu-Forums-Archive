---
title: "Post-install issues"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by Orta on 2006-01-01
Hello,

I have successfully installed Ubuntu on my laptop. However, when the first boot starts (so that additional packages are installed etc), the computer hangs on the item "starting hotplug subsystem". This splashscreen then turns into the regular command line text with the splashscreen items marked as [ok] except for "starting hotplug subsystem". Control alt del doesn't even work, the only way to get out of this is to turn the computer off.

I have tried a number of possible solutions I've seen around the forums (adding instructions to the boot command, on GRUB), but unfortunately none seemed to help. These included noapic, nolapic, irqpoll and others...

The computer is a Tsunami Speeder 259 ([website]("http://www.tsunami.pt/notebooks/speeder_259_detalhes.htm"))which I think it's only sold here in Portugal. The specs are as follows (may have missed something):
- Pentium M 750 1.86GHz
- 2x 512MB RAM DDR2
- Mobile Inter 915GM/GMS,910GML Express OR ATi Radeon Mobility X700 128MB (the computer has an external switch)
- HD: Samsung HM080JI Sata
- Sony DVDRW DW-Q58A
- Realtek AC'97 audio (unsure about model)
- Intel PRO/Wireless 2915ABG
- Realtek RTL8110S/8169S Gigabit Ethernet
- Motorola SM56 Data Fax Modem
- American Megatrends BIOS ver2.00 / KBC ver2.00

Please I really need help, I'm **really** desperate. Many thanks in advance.

--Orta

---

### Post by anil_robo on 2006-01-01
Control+C will let you abort the command where your system hangs. Press Control+C when your system is booting and saying "starting hotplug subsystem". You should be able to boot this way.

---

