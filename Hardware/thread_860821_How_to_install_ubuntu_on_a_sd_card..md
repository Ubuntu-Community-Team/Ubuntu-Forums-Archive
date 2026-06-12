---
title: "How to install ubuntu on a sd card."
date: 2008-07-15
forum: Hardware
---

### Post by heduardo on 2008-07-15
Motivation:

My notebook sata controller is dead and i have no cash to buy a new one, im currently on vacation and had an idea yesterday. Ive got a 16gb sd card which i bought to use with my camera, but the camera only recognizes up to 4gb's. So its kinda of useless.

Requirements: 

1. An external usb cd-rom. (Or a internal if your sata controller is still breathing)

2. An usb flash drive. (My notebook cannot boot directly from the sd drive)

3. A standard Ubuntu-Cd, not the alternative.

HOW TO:

Step One: Boot from the Live Cd. Once the boot is complete, insert your flash drive and sd card.

Step Two: Open up a terminal and type dmesg and look for your disks devices names (My sd is /dev/mmcblk0). Make sure ubuntu has found both of them.

Step Three: Start the instalation process and go normally until you reach the Partitioner.

Step Four: Choose Manual and do the following:

4.1 - Create a ext2 partition at the flash disk start, and set the mount point to /boot. 256mb will do fine

4.2 - Create a swap partition on your flash drive or your sd. I tried both. Due to size limitations i created a swap partition equal to my total ram size(2gb).

4.3 - Create and ext2/3 partition on your sd card and install Ubuntu normally.

Step Five - Set your bios to boot from the flash disk and start Ubuntu normally.

PS: This my first "how to" ever. Apologies for any mispelling, English it is not my primary language.

---

