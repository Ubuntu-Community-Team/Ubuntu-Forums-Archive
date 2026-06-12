---
title: "USB Fup"
date: 2010-07-01
forum: Hardware
---

### Post by Yellobes on 2010-07-01
I've got a patriot 4 gb flash drive here, partitioned 2.5 gb FAT/ 1.5 gb EXT2. I wrote ubuntu 10.04 to the drive via "universal usb installer" from pendrivelinux.com on a windows 7 laptop. The installer includes a custom bootloader and "casper-rw" persistence. The drive was then inserted into another offline windows 7 pc, booted, the host hard drive was mounted and gstreamer codecs were installed. The system was then shut down, the drive removed.
    Upon restarting the machine, windows preformed a recovery operation and all user data was lost.
    Why did this happen, how can I prevent it from happening again? Was it a flaw in the unconfigured persistence script? Has anybody else experienced similar? How can I keep this from happening again? Do you think the files are still there on the host machine?

---

