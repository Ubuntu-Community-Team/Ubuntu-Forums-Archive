---
title: "Anyone have a fix for SD card Acer Aspire One"
date: 2008-12-23
forum: Hardware
---

### Post by stchman on 2008-12-23
Hello all, I am still having problems with the Acer Aspire One SD card readers.

Seems as though that if they are populated then no problem.  If they are empty then sticking an SD card in does nothing.

Does anyone have a quick fix.  I tried this and no dice.

[http://ubuntuforums.org/showthread.php?t=974525](http://ubuntuforums.org/showthread.php?t=974525)

Thanks.

---

### Post by stchman on 2008-12-30
I found this fix that was actually in the Hardy documentation.

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Create a file /etc/modprobe.d/aspireone with the following content:

```
####################################################################
# Module options for the Acer AspireOne
#
# Enable USB card reader
options pciehp pciehp_force=1
install sdhci for i in 2381 2382 2383 2384; do /usr/bin/setpci -d 197b:$i AE=47; done; /sbin/modprobe --ignore-install sdhci
```

The commands are only 2 lines.  The documentation makes it look like three lines.

Next put:
```
pciehp
```

In your /etc/modules to load up at startup.  Reboot.

This works like a champ for BOTH SD card readers.

---

