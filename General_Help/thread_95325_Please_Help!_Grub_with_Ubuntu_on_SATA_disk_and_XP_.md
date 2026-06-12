---
title: "Please Help! Grub with Ubuntu on SATA disk and XP on IDE??"
date: 2005-11-26
forum: General Help
---

### Post by naomi on 2005-11-26
Hi!

I just installed Win XP on my computer (on an IDE harddisk). I already had Ubuntu installed on a SATA harddisk. I could choose in the bios wether to boot from the IDE or SATA harddisk. Since I chose the SATA, I still have my grub bootloader working. Now I wanted to add XP to grub.

I first did a fdisk -l which gave this result:

```

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       10199    81923436    7  HPFS/NTFS

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2            4864       17021    97659135   83  Linux
/dev/sda3           17022       30515   108390555    5  Extended
/dev/sda5           17022       17386     2931831   82  Linux swap / Solaris
/dev/sda6           17387       30515   105458661   83  Linux
```

So /dev/hdc1 is my Windows disk.
I then added the following to /boot/grub/menu.lst as I saw it in some other threads:

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry manually added for a non-linux OS
# on /dev/hdc1
title Microsoft Windows XP
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1inux swap / Solaris
/dev/sda6           17387       30515   105458661   83  Linux
```

When I now boot my computer, the Windows entry is found in the grub menu, but when I select Windows, I get an error message, which says, that there's no such device.

Any idea on what I did wrong?
Many thanks,
Naomi

---

### Post by Alpha_toxic on 2005-11-26
I might be mistaking, but it should be [COLOR="Red"](hd1,0)[/COLOR]. I suppose that the first ubuntu entry is [COLOR="#ff0000"](hd0,0)[/COLOR]? If the ubuntu entry is [COLOR="#ff0000"](sd0,0)[/COLOR] (I've never used SATA, so I don't know how it looks in GRUB's menu), then windows would be [COLOR="Red"](hd0,0)[/COLOR], as it's your first IDE drive.
I also find suspecious the chainloader line. 
[COLOR="#ff0000"]chainloader +1inux swap / Solaris[/COLOR]
is it [COLOR="#ff0000"]+1inux[/COLOR] or [COLOR="#ff0000"]+1 linux[/COLOR] or [COLOR="#ff0000"]+linux[/COLOR]?? I haven't done external win swap on a dual boot machine (I just put a static page file and that usually does the trick), but the first one doesn't seem right at all...

---

### Post by naomi on 2005-11-26
Ooops, I appologize... messed up the code here.  menu.lst says:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry manually added for a non-linux OS
# on /dev/hdc1
title Microsoft Windows XP
rootnoverify (hd2,0)
savedefault
makeactive
chainloader +1
```

My ubuntu partition is listed as (hd0,0).
I read in some other thread that if the partition is hda1 this equals hd0,0 in the menu.lst. I.e. a equals 0, b equals 1, etc. - so I thought it should be hd2 then.

---

### Post by msr7x57 on 2005-11-26
**BEWARE**, I don't own a SATA disk, but it might be worth while trying "(hd1,0)", because it's the disk that GRUB sees "second".

And the best way to do it would be to 

$sudo grub
root (                      <===== PRESS TAB key and it will show a list of disks


eg on my machine:
# grub
   GNU GRUB  version 0.96  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub> root (hd                   <=========pressed TAB
 Possible disks are:  hd0 hd1

grub> root (hd               <===========backspace and type "quit"

---

### Post by Alpha_toxic on 2005-11-26
That looks better. When I saw "chainloader +1.... swap", I thought that you are trying to tell windows to use linux' swap as paging file, and I really doubt that it's possible at all.
Back to the question:
What I understand is that Win is the first partition on the second drive (which happens to be the first/only IDE)?
If so, then Win is either [COLOR="Red"](hd1,0)[/COLOR] or [COLOR="#ff0000"](hd0,0)[/COLOR]. The first one is if the SATA's are not counted separately, the second if they are. I don't know if GRUB counts them separately or not, so you'll have to try both.
P.S. in [COLOR="#ff0000"](hd[COLOR="YellowGreen"]x[/COLOR],[COLOR="RoyalBlue"]y[/COLOR])[/COLOR] , [COLOR="YellowGreen"]x[/COLOR] is the number of the hard drive (physicaly) and [COLOR="RoyalBlue"]y[/COLOR] s the number of the partition on it, both coundet from zero. 
Example: your [COLOR="#ff0000"]third[/COLOR] partition on your [COLOR="#ff0000"]second[/COLOR] hard drive is [COLOR="Red"](hd1,2)[/COLOR]
P.P.S. My second drive is SCSI and it is [COLOR="#ff0000"]hd1[/COLOR], so it's counted as an usual hard disk, so there is no reason for SATA's to be counted separately. This gives you [COLOR="#ff0000"](hd1,0)[/COLOR] as the only option.

---

### Post by paddyg on 2005-11-26
Alpha_toxic, don't call me smartass, you're right, but it's just hd in grub, not hda or hdb ;)

---

### Post by Alpha_toxic on 2005-11-26
Please all of you excuse me for my mistake (mainly naomi). No idea why I wrote that, I'll edit the post wright away...
Anyway that also removes the possibility of sth called (sd0,0), this just doesn't sound right. I think I've seen "sda" somewhere else and it got me totally confused...

---

### Post by soulestream on 2005-11-26
take a look at 

[http://www.linuxquestions.org/questions/answers/479](http://www.linuxquestions.org/questions/answers/479)

the problem is you have to lie to windows, because its not on the first drive.

also there is a file in /boot/grub call device.list(i think) that will tell you which drives are which like /dev/sda = (hd0,1)


soule

---

### Post by naomi on 2005-11-28
Hi! Many thanks for all your help. Unfortunately it still doesn't work :(

@msr7x57: I did what you suggested and I also have hd0 and hd1.

But...
@soulestream: I checked my device.map in /boot/grub and there is only one entry, which lists the SATA disk as: (hd0)   /dev/sda
The IDE disk isn't mentioned here.
I followed the link you posted and it is said there that I have to change the windows entry to the following:
4) Look for the part of the document which regards Windows and replace it with the following:

```
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

```

So I changed that and commented
```
#rootnoverify (hd1,0)
#savedefault
#makeactive

```
which I think is a bit weird...

But when I rebooted my computer and selected the Windows option in grub, nothing happened. Any ideas?

---

