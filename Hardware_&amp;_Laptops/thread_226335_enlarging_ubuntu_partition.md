---
title: "enlarging ubuntu partition"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by xinelo on 2006-07-31
Hello, 

I would like to know what I can do to enlarge the partition where my ubuntu installation resides. I tried using gparted. I could reduce /hda1 and /hda2 to create free space. 

Then I had to delete the boot (/hda5) and the swap (/hda6) partitions to allow the ubuntu partition to move and recreated them at the beginning of the free space. 

So, from this (/ = free): 

```
[FONT="Courier New"]+------+-------+-------+------+------+--------+
| hda1 | hda2  |///////| hda5 | hda6 | hda7   |
| NTFS | FAT32 |///////| boot | swap | ubuntu |
+------+-------+-------+------+------+--------+[/FONT]
```

I got to this: 

```
[FONT="Courier New"]+------+-------+------+------+-------+--------+
| hda1 | hda2  | hda5 | hda6 |///////| hda7   |
| NTFS | FAT32 | boot | swap |///////| ubuntu |
+------+-------+------+------+-------+--------+[/FONT]
```

What I wanted to do at that point is resize hda7 using the free space next to it. However I found that I can't do that. 

I didn't apply the changes and logged off. 

hda1, hda2 and hda3 are normal partitions and all linux partitions (hda5, hda6 and hda7) are logical partitions inside hda3. In case it helps there is fdisk output:

```
[FONT="Courier New"]xinelo@micho:~$ sudo fdisk -lu /dev/hda
Password:

Disco /dev/hda: 40.0 GB, 40007761920 bytes
255 cabeças, 63 setores/trilha, 4864 cilindros, total de 78140160 setores
Unidades = setores de 1 * 512 = 512 bytes

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/hda1   *          63    24579449    12289693+   7  HPFS ou NTFS
/dev/hda2        24579450    59729669    17575110    b  W95 FAT32
/dev/hda3        59729670    78140159     9205245    5  Estendida
/dev/hda5   *    59729733    59874254       72261   83  Linux
/dev/hda6        59874318    61046999      586341   82  Linux swap / Solaris
/dev/hda7        61047063    78140159     8546548+  83  Linux[/FONT]
```

Any ideas? Thanks a lot! 

xinelo

---

### Post by swamytk on 2006-07-31
I too faced this problem. GParted does not resize with the free space available before the resizing partition. There is a  workaround for this.
1. If the freespace is enough to store the entire files of ubuntu / partition => 
(a)move the ubuntu / partition to freespace (if GParted does not work properly, go for "parted", it is fast and very simple).
(b)ensure that your ubuntu / partition available at newly moved place.
(c)delete the old ubuntu / partition
(d)now, you have ubuntu / partition followed by free space.
(e)resize the ubuntu / partition.

---

### Post by cyberdude on 2006-07-31
have you tried the gparted livecd??

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by xinelo on 2006-07-31
thank you guys for your prompt replies. 

cyberdude: yes, sorry if I didn't mention it explicitly, I did everything that I explained from the gparted live CD. 

swamytk: let me see if I understand: you suggest to create a new ext3 partition in the free space (from the gparted live cd), then log back in and mv /* into that partition? (otherwise phrased: when you say "move" do you mean "mv"?)

wouldn't moving stuff in that way from one partition to another risk destroying all the directory structure or make something fail when reloging in into linux? 

cautiously yours, xinelo

ps: swamytk: does parted have support for ntfsresize?

---

### Post by swamytk on 2006-08-01
> **xinelo said:**
> 
wouldn't moving stuff in that way from one partition to another risk destroying all the directory structure or make something fail when reloging in into linux? 


GParted cannot resize partition in backward. Reference: [http://en.wikipedia.org/wiki/GParted](http://en.wikipedia.org/wiki/GParted)

Option1: Less risky => There is a option in Gparted called "copy" when you right-click a partition. Using that option you can copy one partition to another. (Caution: After copying, you have to preserve the partition number, so that grub/lilo can boot it properly OR do necessary changes in grub/lilo)
Option12: What I did : Bit risky : I used "parted" command, and moved the partition to freespace.

> **xinelo said:**
> 
ps: swamytk: does parted have support for ntfsresize?
Yes, It can.

---

### Post by xinelo on 2006-08-01
Thanks. I think I'll try to do it the safe way. 

Just one more question: how do I preserve the partition number? I would assume that if the number of partitions is the same and the order is the same, ubuntu's partition's number shouldn't change.

Thanks again. Cheers! xinelo

---

### Post by xinelo on 2006-08-09
Hello, 

Here's some feedback. 

I did it the first way. I used gparted live cd. I had to copy the / partition  and the /boot partition and recrete the /swap partition. 

The only problem that I had is that I couldn't apply all changes at once, so I had to go one by one. 

One weird thing with this issue is that, assuming partitions cannot be moved backwards (which seems to be the problem I had with hda7), I wonder how come I could do precisely that with hda2. 

Let me explain this: I resized hda1 from 12Gb to 10Gb and then moved hda2 2Gb backwards so that no free space remained between those two partitions. Maybe fat32 partitions can be moved backwards and ext3 cannot, who knows. 

Anyway, thanks a lot for your advice, swamitk. Cheers!

xinelo

---

