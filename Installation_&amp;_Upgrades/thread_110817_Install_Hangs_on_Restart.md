---
title: "Install Hangs on Restart"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by William_in_Kanata on 2005-12-31
AMD Athlon 64 processor
2GB Memory
MSI RS482M4 motherboard - on board everything.
Kubuntu installing on hdb (120 Gb Drive) 64 bit distribution
Windows XP Pro on hda.
grub installed on hda for dual boot and that works correctly

During the initial phase of the install I had to use "noapic nolapic" to get it started, but once started, ran to completion with no observed problems. Removed the CD from the drive, and restarted.

On restart, boot seems to start normally, and runs for a few seconds and then hangs after displaying the lines

Setting Up Networking                                 [OK]
Starting Hotplug subsystem
 
After a few seconds the initial boot screen is replaced with text mode screen with the same messages. 

On trying the boot from the recovery mode it starts up fine, and runs through the startup process, and eventually hangs after displaying these lines:

[35.642246] snd-hda-intel: can't be loaded
  missing kernel or usermode driver snd-hda-intel
  8139too: already loaded
  8139cp: already loaded

The boot lines in both cases include the "noapic nolapic" options.

So am I just being impatient? I let it sit for a good 1.5 to 2 minutes, with no action.

Thanks for any help or suggestions that you may have.

---

### Post by Orta on 2005-12-31
The exact same thing happens to me, however my version is different - using Ubuntu 5.10. I also tried using irqpoll without luck. My computer setup (it´s a laptop), if helps:
- Pentium M 750 1.86GHz
- 2x 512MB RAM DDR2
- Mobile Inter 915GM/GMS,910GML Express OR ATi Radeon Mobility X700 128MB (the computer has a switch) 
- HD: Samsung HM080JI Sata
- Sony DVDRW DW-Q58A
- Realtek AC'97 audio (unsure about model)
- Intel PRO/Wireless 2915ABG
- Realtek RTL8110S/8169S Gigabit Ethernet
- Motorola SM56 Data Fax Modem

Thank you very much.

---

### Post by bigphil on 2006-08-26
Hi,
Have you seen this post:
[http://www.linuxquestions.org/hcl/showproduct.php?product=3207&cat=myprod](http://www.linuxquestions.org/hcl/showproduct.php?product=3207&cat=myprod)
Does it help?

Cheers,
Phil

---

