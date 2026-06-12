---
title: "Hotplug won't run USB policy agent"
date: 2005-08-06
forum: Hardware &amp; Laptops
---

### Post by Geir Smestad on 2005-08-06
I have installed the gnomad2 package to be able to access my Zen Xtra mp3 player. The program runs nicely as root, but as user I get the error message "usb_set_configuration: Operation not permitted". I therefore installed a USB policy agent in /etc/hotplug/usb (files nomadjukebox and nomadjukebox.usermap) to set the right permissions for the USB device. However, the nomadjukebox script doesn't execute when I plug in the player. The usb.agent script in /etc/hotplug/ detects my player, and as far as I can see the ID flags in nomadjukebox.usermap match the IDs that my player provides. I am also quite sure that the policy files have the right permissions set. I get no error messages when I plug in the player.

Do any of you know what point I'm missing?

---

