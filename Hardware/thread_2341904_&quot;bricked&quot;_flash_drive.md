---
title: "&quot;bricked&quot; flash drive?"
date: 2016-11-01
forum: Hardware
---

### Post by jlh68 on 2016-11-01
I was trying to have an encrypted flash drive (16 gb).  I used the Gnome cryptsetup and the Ubuntu flash derive format (LUKS + Ext4).  I somehow got the flash drive to be encrypted, but it somehow messed up. I tryed to encrypt it again and had two passwords for individual 16-gb partitions (concurrent partitions).
I tried to reformat to get only one encrypted 16-gb partitions, but it did not work and now my computer will not see the flash drive when inserted. Is is bricked or is it salvagable?

---

### Post by sudodus on 2016-11-02
We don't know yet, which means that there is hope :-) See these links and links from them,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

I suggest that you try to wipe the pendrive with ***mkusb*** according to the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

-o-

See also this link describing how to get a persistent live system with an additional user with encrypted home (the ecriyptfs method)

[Posts #428-431](https://ubuntuforums.org/showthread.php?t=1958073&p=13558751#post13558751)

---

