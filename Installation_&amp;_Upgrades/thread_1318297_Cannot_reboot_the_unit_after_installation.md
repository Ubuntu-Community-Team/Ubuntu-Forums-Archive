---
title: "Cannot reboot the unit after installation"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by Thomas1477 on 2009-11-07
This is what I am getting after the unit reboots after the installation:
Grub loading
Error:no such device:d9d54e3f-ad23-41a3-96d9-bebfcb0a4c81
Failed to boot default entries
Press any key to continue...

If you press any key you get same error, if you press the enter key you get;
GNU Grub 1.97~beta4
* Ubuntu, Linux 2.6.31-14-generic
* Ubuntu, Linux 2.6.31-14-generic (recovery mode)
* Memory test (memtest86+)
* Memory test (memtest86+, serial console 115200)

If you press enter to try to boot from the highlighted item you get nothing,if you press key you go back to:

Grub loading
Error:no such device:d9d54e3f-ad23-41a3-96d9-bebfcb0a4c81
Failed to boot default entries
Press any key to continue...

Anyone have any ideas???

Somewhere in the forums I read a post about video drivers that stated:
"After installing but before shutting down the unit install the video driver for your video card."
This worked for me. I am now up and running on 9.10,also using Ubuntu to post this item.

---

