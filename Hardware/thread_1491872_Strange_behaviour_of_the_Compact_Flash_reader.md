---
title: "Strange behaviour of the Compact Flash reader"
date: 2010-05-24
forum: Hardware
---

### Post by baruchel on 2010-05-24
Hi, I never noticed this bug with previous releases. Now I use 10.04 Lucid Lynx. When I insert some CF (compact flash) card in my internal card reader (provided with my Dell Inspiron 530), it is correctly mounted THE FIRST TIME I insert it. At that time dmesg gives:

```

[   68.238883] sd 4:0:0:0: [sdb] 8027712 512-byte logical blocks: (4.11 GB/3.82 GiB)
[   68.243245] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   68.256746] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   68.256753]  sdb: sdb1

```

If I unmount it and insert it again without having restarted the computer, it seems to be not detected. I can't mount my card again unless I restart the computer! Nothing more is returned by dmesg after the following steps: unmount CF card, remove it, insert it again (which means that the last line in dmesg will be the line above). Is this bug known? Is there some quick workaround for using my CF card twice in a session without having to restart the computer?

---

### Post by dino99 on 2010-05-24
in fact there are 2 questions: 

is the reader automaticaly mounted at boot up ?
internal or usb reader ?

maybe install libccid and firmware-addon-dell with synaptic

some checkings:
sudo update-pciids && update-usbids
sudo apt-get install -f
sudo dpkg --configure -a

about trouble: maybe a wrong fstab settings (not easy to tweak)
the easy way: install mountmanager to set your prefs about devices and partitions (system admin mountmanager)

---

### Post by baruchel on 2010-05-24
My card reader is internal.

Obviously mu bug seems to be the same as in [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/504440](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/504440)
What I want to do with my right-click button is to "unmount" the filesystem, but it looks like nautilus does a little more, doesn't it? I will have a try of unmounting from the command line in order to see if the CF card is detected when I reconnect it. Best regards.

---

### Post by dino99 on 2010-05-24
mountmanager is the easy way to manage devices and partitions

---

### Post by dino99 on 2010-05-24
> **baruchel said:**
> My card reader is internal.

Obviously mu bug seems to be the same as in [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/504440](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/504440) [COLOR="Blue"]post #9 is interesting[/COLOR]
What I want to do with my right-click button is to "unmount" the filesystem, but it looks like nautilus does a little more, doesn't it? I will have a try of unmounting from the command line in order to see if the CF card is detected when I reconnect it. Best regards.

looking the report and the 9 comment, its strange that it cant dynamicaly detect it

---

