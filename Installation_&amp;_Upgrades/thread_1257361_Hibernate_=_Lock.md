---
title: "Hibernate = Lock"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by FMaz008 on 2009-09-03
Hi everyone !

I have a little problem that I'll explain:
since the last kernel update, I've an old problem that I never encountered before. :(

When I try to hibernate, the computer hard drive run a little bit, like if the memory was dumped, and then, the screen simply lock.

Please note that the normal sleep work very well...

Here is the original --unsolved-- subject:
[http://ubuntuforums.org/showthread.php?t=438705](http://ubuntuforums.org/showthread.php?t=438705)

---

### Post by phillw on 2009-09-03
I don't know if this will help at all, but for some background on sleep / hibernate etc. this thread may help ...

[http://ubuntuforums.org/showthread.php?t=1235660&highlight=phillw](http://ubuntuforums.org/showthread.php?t=1235660&highlight=phillw)

I don't recall where i got the information from for that one - but if any of it is 'near' what you need - I'll go and have another look.

Regards,

Phill.

---

### Post by FMaz008 on 2009-09-03
Hum, well, I've checked my grub/menu.lst file, and the options seems the same between the kernels version available.

I've no previous options with acpi=force.


Is their a place where I could find a log with revelant informations ?
(And I still don't understand why I don't receive an error message... it's really a weird behavior.)

---

### Post by phillw on 2009-09-04
These articles may or may not be applicable for your situation,

[http://linux.com/archive/feature/55988](http://linux.com/archive/feature/55988)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190095](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190095)

I guess you have popped your details of the laptop, but if u'd post your laptop make & spec, how u have the disk sliced and version of ubuntu - I'll have a further look for you.

Phill.

---

### Post by FMaz008 on 2009-09-04
Hi, 

Well, thanks for your help ! It's really appreciated.

My laptop is a Lenovo thinkpad x61s, and my specs should be something like:
Intel Core Solo processor L7500 (1.6GHz)
Memory  2GB (2x1gb)
Hard drive 	S-ATA 160GB 7200rpm
Display 	12.1inch TFT display
Graphics 	Intel X3100
(...)


And for the partitions of the drive:
(I'm proud, because I think I've found the good command by myself :popcorn:)
```

laptop:~$ sudo fdisk -l /dev/sda

Disque /dev/sda: 160.0 Go, 160041885696 octets
255 têtes, 63 secteurs/piste, 19457 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x7c822d0c

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1               1         640     5139456   27  Inconnu
La partition 1 ne se termine pas sur une frontière de cylindre.
/dev/sda2   *         640       11376    86229996    7  HPFS/NTFS
La partition 2 ne se termine pas sur une frontière de cylindre.
/dev/sda3           12107       19457    59043600    5  Etendue
La partition 3 ne se termine pas sur une frontière de cylindre.
/dev/sda4           11377       12107     5866560    b  W95 FAT32
La partition 4 ne se termine pas sur une frontière de cylindre.
/dev/sda5           12107       19152    56586568+  83  Linux
/dev/sda6           19152       19457     2456968+  82  Linux swap / Solaris

```


Do you need anything else ?

---

### Post by phillw on 2009-09-05
The model number turned out to be enough for me :D

You will be delighted to know that there is an active thread (conversation) running on these forums for your model.

[http://ubuntuforums.org/showthread.php?t=817897](http://ubuntuforums.org/showthread.php?t=817897)

I will gladly point you over to them and am sure that they will be assist you much more quickly than I could.

They run that laptop under various releases of Ubuntu - So, I'm sure they have come across your problem.

It is always a pleasure to help :-)

Enjoy Ubunutu & welcome to this forum, IMHO, the best there is.

Phill.

---

