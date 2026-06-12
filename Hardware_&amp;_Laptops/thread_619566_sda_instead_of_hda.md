---
title: "sda instead of hda"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by dlublink on 2007-11-21
Hello,


What kernel modules are responsable for making the hdX appear as sdX ?

Thanks,

David

---

### Post by travist120 on 2007-11-21
I am unsure of what modules would do this, but there is a reason why there is SDA and HDA. I think the reason might be size, and the type of cable that is used to connect to the mother board.

---

### Post by EXCiD3 on 2007-11-21
hda means its connected via ide and sda means its a sata drive (if im not mistaken) but i have no clue as to what does this.

---

### Post by dlublink on 2007-11-22
It's an IDE drive that is listed as SDA. I am told that this is to make the interface to disks more generic and less complicated for programmers, when I was using Gentoo it was seen as HDA.

---

### Post by loganm10 on 2007-11-22
ya all HDD's show up as sdaX in Ubuntu, Im not sure what is responsible for doing this though, its the same in openSUSE for sure too though

---

### Post by nick_h on 2007-11-22
Since Feisty pata drives now use the sata/scsi drivers.

---

### Post by Tweenk on 2007-11-22
IDE drives are listed as /dev/sdaX when you are using the new parallel ATA controller drivers instead of the IDE ones. This isn't an Ubuntu peculiarity, it's supposed to be like this for all new releases of the kernel. If you're not happy with this, you have 3 options:
a) Create symlinks in the /dev directory to point to the sda drives:
$ **sudo ln -s /dev/hda1 /dev/sda1**
b) Add custom udev rules to /etc/udev/rules.d - this option is more complicated, but it will get rid of the /dev/sdaX files. I'm not familiar enough with udev rules to tell you more.
c) Do not include the Parallel ATA drivers in a custom kernel. Parallel ATA and Serial ATA drivers are in one kernel config section and Generic IDE support under another. Enable the IDE driver for your chipset and disable the entire PATA/SATA section.

---

