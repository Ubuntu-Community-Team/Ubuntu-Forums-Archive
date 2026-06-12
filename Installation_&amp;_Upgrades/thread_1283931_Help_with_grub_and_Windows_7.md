---
title: "Help with grub and Windows 7"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by lecasri on 2009-10-06
Hi... recently I upgrade my windows vista to windows 7, but I lost the grub, now my computer only start with windows.

I found in the forum many options to restore the grub but doesn't work. I don't know if I'm doing something wrong. for example, I follow the steps in  [http://ubuntuforums.org/showthread.ph?t=1282785&highlight=reinstall+grub+windows](http://ubuntuforums.org/showthread.ph?t=1282785&highlight=reinstall+grub+windows)


this is the information of my disk

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x517182bf

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       10444    83886080    7  HPFS/NTFS
/dev/sda2           10444       38914   228681728    7  HPFS/NTFS

Disco /dev/sdb: 60.0 GB, 60022480896 bytes
255 cabezas, 63 sectores/pista, 7297 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x02830282

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1        7298    58612736    7  HPFS/NTFS

Disco /dev/sdc: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x4b4b4b4b

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extendida
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris


I have 
1 SATA disk (320Gb) with 2 partiotion (one windows 7 system and other for programs)
1 IDE Disk with 60gb for documents
1 IDE Disk  with 81Gb for Linux..

Could somebody help me to reinstall grub? Thanks

---

### Post by bilalakhtar on 2009-10-06
When you install a version of windoze (any one), it always rewrites the MBR. If you had GRUB earlier, there is Windows bootloader in its place now. You can do two things to solve the problem:-
1)Re-install grub using the grub-install command from a liveCD. More info on that:- [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
2)Modify the Windows bootloader to show an option for ubuntu (risky, may not work in Win7, mainly works in Vista)
To get the steps for each option, simply google it. Have some popcorn.:popcorn: :lolflag: :guitar:

---

