---
title: "raid 1 setup(two disks) show up in disk utility as two drives."
date: 2018-08-16
forum: Hardware
---

### Post by kinghat on 2018-08-16
i have an on board Marvell 88SE9172 sata controller set to raid mode and have a raid 1 setup with 2 drives. im dual booting between win 10 and ubuntu 18.04.1 with each OS on separate SSDs on a totally different controller. the raid shows up fine in win 10 after installing drivers for the marvell controller but im having a hell of a time figuring out how to get it to show the raid properly in ubuntu. its shows up as two separate disks in the disk utility and they dont show up at all in the 'other locations' in files. the raid 1 is not for an OS its just for storage.

i found this guy: [http://theangryangel.co.uk/blog/marvell-88se9172-sata3-under-linux-as-of-320/](http://theangryangel.co.uk/blog/marvell-88se9172-sata3-under-linux-as-of-320/)

and this: [https://patchwork.ozlabs.org/patch/155387/](https://patchwork.ozlabs.org/patch/155387/)

i also found some info here: [https://ipfs.io/ipfs/QmXoypizjW3WknFiJnKLwHCnL72vedxjQkDDP1mXWo6uco/wiki/List_of_Marvell_Technology_Group_chipsets.html](https://ipfs.io/ipfs/QmXoypizjW3WknFiJnKLwHCnL72vedxjQkDDP1mXWo6uco/wiki/List_of_Marvell_Technology_Group_chipsets.html)

as well as this guy with no response: [https://askubuntu.com/questions/675624/use-marvell-88se9172-sata-controller-for-hw-raid-1](https://askubuntu.com/questions/675624/use-marvell-88se9172-sata-controller-for-hw-raid-1)

lspci shows:

[ATTACH=CONFIG]280755[/ATTACH]

these are all pretty old posts. am i SOL on this one?

---

