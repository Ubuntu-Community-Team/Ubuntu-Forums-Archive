---
title: "ubuntu server 9.10 SATA problem: frozen, timeout, ++"
date: 2010-04-06
forum: Hardware
---

### Post by ottopaul on 2010-04-06
I have installed ubuntu 9.10 server on a Dell Dimension 8250. In order to get a big harddisk I installed a STLab SATA 150 PCI Raid Card and a 2TB WD Green Caviar disk.

The new disk is not working properly. When I copy files to it or read files via MediaTomb, it freezes after a few seconds.

Logs shows "Exception.... frozen", "hard resetting link", timeout and a lot of other stuff that I do not understand. After searhing the Internet for help for a few days, I now enter this post and hope that someone can help me. See some logs attached. Please ask for more if you can help me.

By the way - I have tried some grub config without success: Changed /etc/default/grub, added "pci=nomsi acpi=off noapic" after "quiet splash" and ran update-grub. Did not help. Actually I think it failed even faster after these changes.

Please help me - I want this computer to work as a media server.

[ATTACH]152532[/ATTACH]

[ATTACH]152533[/ATTACH]

[ATTACH]152534[/ATTACH]

---

### Post by ottopaul on 2010-04-09
I tried to change the SATA cable, because I read much about cable problems. It seemed to help. I could watch several minutes of video via MediaTomb, but after a while the problem got back the same way.

Does anyone know if there is something special I have to do with my combination of a WD20EARS disk and a SiL 3512 controller on a PCI 150 motherboard?

---

