---
title: "Safely removing USB HDD"
date: 2010-06-05
forum: Hardware
---

### Post by xtracool_protik on 2010-06-05
Hey guys,
 I've 2 USB HDDs. One of them simply can't be removed safely. On clicking safely remove it shows up a dialogue box saying :

> Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-4)
SYNCHRONIZE CACHE: OK
STOP UNIT: FAILED: No such file or directory


When I tried it removing through gparted I got some error saying:
> Text ended before matching quote was found for ". (The text was 'sh -c 'umount -v "/media/P'TIK"'')

I even tried formatting the HDD still it didn't solve anything
There is a bug thread about it here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/571194?comments=all](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/571194?comments=all)

Does anyone have any opinion?
Thanks

---

### Post by arrange on 2010-06-05
The problem could lie in the label: P'TIK. Have you tried changing it?

---

### Post by xtracool_protik on 2010-06-05
just tried changing it even tried keeping default "New Volume" but it didn't help

---

