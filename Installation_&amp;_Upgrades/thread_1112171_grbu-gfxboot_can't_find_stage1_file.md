---
title: "grbu-gfxboot can't find stage1 file"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by silentbuteo2 on 2009-03-31
Hi,

I'm trying to install the gfxboot loader. I followed the tutorials on the net, but i'm stuck when i want to intall it in the hdx.

so things i dit:
- remove old grub
- installed the new gfxboot grub
      (tried both grub-gfxboot_0.97-40_i386 and grub-gfxboot_0.97-5_i386)
-copied a messeg.xxx file into /boot/grub/
-adjusted the menu.lst file with the 'gfxmenu'

Now i have to do the grub> root (hdx,y) and setup (hdx)
But that fails.I get the next error:

[COLOR="RoyalBlue"][I]grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 2: Bad file or directory type[/I][/COLOR] 

I'm sure the current linux partition is hd0,1.
Here I post my fdisk info

[COLOR="RoyalBlue"][I]sudo fdisk -lu

Schijf /dev/sda: 640.1 GB, 640135028736 bytes
255 koppen, 63 sectoren/spoor, 77825 cilinders, totaal 1250263728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x0001df92

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *          63   629426699   314713318+   7  HPFS/NTFS
/dev/sda2       629426700  1246354829   308464065   83  Linux
/dev/sda3      1246354830  1250258624     1951897+  83  Linux

Schijf /dev/sdb: 163.9 GB, 163928604672 bytes
255 koppen, 63 sectoren/spoor, 19929 cilinders, totaal 320173056 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x3b9eb835

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *          63     8385929     4192933+  82  Linux wisselgeheugen
/dev/sdb2         8385930   320159384   155886727+   7  HPFS/NTFS

Schijf /dev/sdc: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cilinders, totaal 240121728 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0xe90be90b

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1           16065   102398309    51191122+   f  W95 Uitgeb. (LBA)
/dev/sdc2       102398310   204796619    51199155   83  Linux
/dev/sdc3   *   204796620   235914524    15558952+   c  W95 FAT32 (LBA)
/dev/sdc4       235914525   240107489     2096482+  83  Linux
/dev/sdc5           16128   102398309    51191091    7  HPFS/NTFS

Schijf /dev/sdd: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0xcb02ea17

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdd1              63   976768064   488384001    7  HPFS/NTFS

Schijf /dev/sde: 2055 MB, 2055021056 bytes
16 koppen, 63 sectoren/spoor, 3981 cilinders, totaal 4013713 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0xa0dc43e6

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sde1   *          63     4013712     2006825    b  W95 FAT32[/I][/COLOR]

When i search for the stage1 file, i find one, but on my old harddisk. I had gfxboot installed on my older hd, but that has to be removed one of these days.

[COLOR="RoyalBlue"][I]grub> find /boot/grub/stage1
 (hd2,1)[/I][/COLOR]

When i run this find without hd2 attacthed to my computer is get:
[COLOR="RoyalBlue"][I]grub> find /boot/grub/stage1
Error 15: File not found[/I][/COLOR]

Can someone help me with this strange problem.

note: when i install the old grub again, all things work fine again. So he finds the stage1 file.

---

### Post by tollboy on 2009-04-09
i was having having the same problem..............
i experimented without any logic . and finally got solved the problem

first wat u have to is install the grub on ur partition not on ur mbr.

so do it as follow.
```
sudo grub-install sdaX
sudo grub
find /boot/grub/stage1
root (hdX,X)
setup (hdX)

```
this will install grub on ur root partition 
for example it was on sda5

now unistall grub and install the grub-gfxboot
```
sudo apt-get remove grub
cd /directory/were/.deb/is /kept
sudo dpkg -i grub-gfxboot*****
sudo grub
find /boot/grub/stage1
```


and u will see it is finding the stage 1

hope this will help u.

---

### Post by silentbuteo2 on 2009-04-12
No, no luck on this one.
I can't find that stage1 file once i installed the gfx-boot grub.

I think I'll give up. I tried different solutions from other forums, but no luck. Maybe i tried one to many.


I will check this post regular, if someone has other ideas

Thanks tollboy for the suggestion.

---

