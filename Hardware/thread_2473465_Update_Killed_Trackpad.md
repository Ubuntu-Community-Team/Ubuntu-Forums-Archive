---
title: "Update Killed Trackpad"
date: 2022-04-05
forum: Hardware
---

### Post by al.andersen on 2022-04-05
I'm using focal on an Asuz Zenbook UX392FN with an NVidia GP108M (GeForce MX150) card. The system has run fine, until yesterday when I got both an NVIDIA and Grub update. 

Upon booting up this morning, I found that the trackpad doesn't work -- cursor stuck in upper left corner. I can access programs using the keyboard, and looking in Settings I see it finds no trackpad. I tried to revert the NVIDIA driver, but that didn't work, and I tried to set it to change the NVIDIEA metapackage 470 (proprietary) tested driver to the Noveau driver, which didn't work on reboot either. Unfortunately, I can't figure out how to put it back to the 470 driver (movement keys went down the list but I can't get them to go back up).

Anyway, how do I get my trackpad working again? I can open a Konsole (using KDE) OK, and I can use Ctrl-Alt-F2 for a full terminal.

Help?!?!

---

### Post by al.andersen on 2022-04-05
I think I have it fixed... everything seems to work OK. I made a minor modification to Grub /etc/default/grub

old: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
new: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash psmouse.proto=bare&#8221;
sudo update-grub
sudo reboot

I was then able to go back to my NVIDIA 470 driver and with another reboot everything seems to be working OK.

---

