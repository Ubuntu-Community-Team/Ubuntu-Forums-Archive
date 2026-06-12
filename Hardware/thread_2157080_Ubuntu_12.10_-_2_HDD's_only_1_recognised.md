---
title: "Ubuntu 12.10 - 2 HDD's only 1 recognised"
date: 2013-06-24
forum: Hardware
---

### Post by mesmerize08 on 2013-06-24
Hey guys,

Was hoping someone could give me some quick advice.

Running Ubuntu 12.10

Have 2 NTFS hard drives but Ubuntu is only showing one of them. They are both exactly the same types of drives, both 3TB NTFS that I just pulled out of my Windows PC. I've had other NFS hard drives in before and had no problems.

Tried all the obvious things like unplugging and re trying, restarting the computer etc. Is there something I'm missing?

Thanks for the advice.
Matt0

---

### Post by dino99 on 2013-06-24
ubuntu (linux) works with EXT3/4, so i suppose ubuntu is not yet installed on your system (note: if you are using wubi, forget about it, its a abandonware)

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by mesmerize08 on 2013-06-24
Sorry, I should have been clearer.

Ubuntu 12.10 is installed on its own hard drive (EXT).

I have 2 other hard drives (NTFS) with media on both but Ubuntu is only recognising one of them. (these hard drives were in my Windows Desktop working perfectly)

Previously in my Ubuntu system I had the OS hard drive, and 3x NTFS drives running like champs.

Decided to switch up my setup and use the Ubuntu system as a server. Set everything up nicely and was going great with the past hard drives, but for some reason now that I've swapped the hard drives around only 1 of them is being recognised.

Hope this clarifies things
thanks

---

### Post by Bashing-om on 2013-06-24
mesmerize08; Hi,

Swapping drives around and let us presume that the drive's mapping in bios no longer corresponds to what the operating system has the drives mapped at. Maybe try updating/generating the device.map file will help the system to identify the drives ? From the ubuntu install, terminal command:
```

grub-mkdevicemap

```
now what does the system see ?
```

sudo fdisk -lu

``` 

Another thought, was that drive ever in a "raid" array ? Such that there is embedded "meta" data present on the disk ?
-will take raid tools to see and remove it -

[INDENT][INDENT]just my thoughts[/INDENT][/INDENT]

---

