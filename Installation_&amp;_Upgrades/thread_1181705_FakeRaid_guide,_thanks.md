---
title: "FakeRaid guide, thanks"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Gorlist on 2009-06-08
Just quick post to thank the authors who wrote the FakeRaid guide found here: 

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Installed on Intel X38, with two 300gig drives using RAID0. First installed WinXP with a partition size of 300GIG, then Ubuntu on the remainder. Only deviations from the guide is I used the standard Ubuntu installer to setup my partition manually, with it defined to EXT4 :)

To boot into Ubuntu I had to generate a .bin file, for example:

```
dd if=/dev/mapper/isw_cabidfddci_ARRAY6 of=/linuxboot.bin bs=512 count=1
```

(ideally do this before you restart, however I had to reload from the Live CD and chroot over to main array)

Transfered it to a third spare drive (as I have no floppy), booted into XP shunting the file into C drive and adding the following to my boot.ini:

```
c:\linuxboot.bin="Ubuntu Linux" /fastdetect
```

Also thanks to:  [http://www.linuxquestions.org/questions/susenovell-60/boot-linux-suse-using-boot.ini-from-windows-xp-244728/](http://www.linuxquestions.org/questions/susenovell-60/boot-linux-suse-using-boot.ini-from-windows-xp-244728/)

Well worth the effort :)

---

