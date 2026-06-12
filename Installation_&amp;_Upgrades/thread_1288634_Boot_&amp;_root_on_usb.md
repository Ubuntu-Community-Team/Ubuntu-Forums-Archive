---
title: "Boot &amp; root on usb"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by bolo.- on 2009-10-11
An installation question. Tried google, but I probably don't know enough about this to get a good query composed.

Need to install a server os. Plan to use 8.04. Would like to install boot and root on a usb drive and everything else on partitions placed on lvm on raid 1 sata disks. Cannot seem to find out how to install just boot and root on usb drive. The reason is to allow a simple reboot with a new usb drive if problems or updates occur in root or boot, while all data (including swap and temp) gets caught in the raid 1. The usb drive will remain in the usb port unless it fails or needs upgrading. This will remove minor bootable issues with mirrored drives and boot and root data aren't crucial. This is an idea, not a super must-do situation.

I suspect this is really simple, but I want to be sure before I configure a new server because this hasn't been done here. And, certainly, we have a lot of ideas that don't seem so good once a few people start commenting on them.

---

### Post by stlsaint on 2009-10-11
well i would suggest this:
1) use a liveusb to install..useful for troubleshooting.
2) if your wanting Raid setup see [here]("https://help.ubuntu.com/community/FakeRaidHowto") as ubuntu isnt very keen on raid.
3) [LVM]("http://en.wikipedia.org/wiki/Logical_volume_management") is easy to setup once you do some research on it.

Also when setting up a server i suggest you always refer to the [UbuntuServerGuide.]("https://help.ubuntu.com/9.04/serverguide/C/index.html")

---

### Post by Mighty_Joe on 2009-10-12
[This topic]("http://ubuntuforums.org/showthread.php?t=1278743") may interest you.

---

