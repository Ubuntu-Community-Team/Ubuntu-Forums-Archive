---
title: "USB pen drive dead?"
date: 2011-09-19
forum: Hardware
---

### Post by ricardofilipemoreira on 2011-09-19
[FONT=Arial]Hi, I have a 8GB pen drive that I used to create a LiveUSB boot disk of ChromiumOS ([http://chromeos.hexxeh.net/wiki/doku.php?id=linux_instructions](http://chromeos.hexxeh.net/wiki/doku.php?id=linux_instructions)) with usb-imagewriter (frontend for dd). I had used it some times and worked fine except once when it gave and error and the flash drive became unusable.
Ubuntu and Windows detect the drive as plugged but act like a card reader with no card inserted, Disk Utility (and the correspondent in Windows) shows the drive plugged in /dev/sdc but has no partition and when I try to create partition table or format the drive, it says "No medium found".
I tried sudo dd if=/dev/zero of=/dev/sdc and using shred to wipe the drive but all commands say there is no medium found. GPartEd doesn't find the drive. FDisk says "Unable to open /dev/sdc". Steps in [http://ubuntuforums.org/showthread.php?t=1139960&highlight=USB+pen+drive+dead%3F&page=3](http://ubuntuforums.org/showthread.php?t=1139960&highlight=USB+pen+drive+dead%3F&page=3) don't help either.
Is there any way to reformat the drive so it can be used again? Any help is appreciated.
Tried Ubuntu 11.04 11.10 and Win7
Thanks[/FONT][FONT=Arial]
[/FONT]

---

