---
title: "? before uninstall/reinstall"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Homer_H on 2009-06-29
I have a triple boot system on a laptop with xp,vista and ubuntu. I already had 3 partitions before installing ubuntu. Either I screwed up on the install or ubuntu put itself on 3 gb partition. I can't download updates because there is not enough room. i can't enlarge the partition using disk manager in vista or ubuntu because you can only change the first three partitions. i like ubuntu and want to uninstall then reinstall without messing up xp and vista. i currently boot with grub to ubuntu first with the other operating system option to get to xp and vista. When i unstall does grub go away too? Will this cause boot problems to other systems? Are there instructions for this somewhere? Suggestions anyone?

---

### Post by dtoronto on 2009-06-29
gpart is probably what you're looking for

```
$sudo apt-get gpart
```

from this you can use the GUI to repartition and adjust your hard drive.

---

### Post by philcamlin on 2009-06-29
> **dtoronto said:**
> gpart is probably what you're looking for

```
$sudo apt-get gpart
```from this you can use the GUI to repartition and adjust your hard drive.


thats what you want :)

---

### Post by Homer_H on 2009-07-02
sorry, i just said i used partition manager in vista and ubuntu instead of saying gparted.  
info in gparted: installed as a subfolder? under /dev/sda4 extended partition: - as /dev/sda6 - (dark blue square)  file system: - ext3, mount point: / - size: 2.81 gb unused: 208 mb. when i highlight this and go to partition everything is greyed out except unmount and that does nothing either. that is why i was asking about uninstalling and starting over. thanks

---

