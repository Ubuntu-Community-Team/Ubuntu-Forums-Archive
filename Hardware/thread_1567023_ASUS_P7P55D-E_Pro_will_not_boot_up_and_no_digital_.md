---
title: "ASUS P7P55D-E Pro will not boot up and no digital audio"
date: 2010-09-03
forum: Hardware
---

### Post by ojuano on 2010-09-03
Some time ago I posted in this forum a message requesting help for Ubuntu 10.04 not booting all the time and not having digital audio (spdif) on my ASUS P7P55D-E Pro motherboard. After much digging around I came up with a solution that works well for me. I upgraded my kernel to version linux-image-2.6.35-19-generic-pae. In order to upgrade your kernel copy and paste this link to your browser's address window:

[http://lug.mtu.edu/ubuntu/pool/main/l/linux/linux-image-2.6.35-19-generic-pae_2.6.35-19.28_i386.deb](http://lug.mtu.edu/ubuntu/pool/main/l/linux/linux-image-2.6.35-19-generic-pae_2.6.35-19.28_i386.deb)

Once downloaded to your home/username/Downloads folder double click on the file. The Package Installer would install the new version kernel. Once installed, reboot the computer and bingo! the digital audio (spdif) would work (once selected on the "Sound Preferences" located under the speaker icon on the top panel) and Ubuntu will boot up all the times.

Enjoy! :D

If some one has a better way, please add to this thread.

---

