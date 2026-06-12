---
title: "ubuntu and windows disk war???"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by carniolus on 2006-12-01
Hi!
i'm having a strange problem.
once (100 years) i was very excited about win xp. i installed it on my
first disk. and then, i installed ubuntu edgy on my second disk.
they worked togehter for about an month.
but now, every time i start computer in xp, it crashes at login time with one
of the famous blue screens.
BUT, my ubuntu works great!
when an fsck is runed on my windows partition, everthing works fine (even wins!) for a couple of boots. after that, everthing goes back.

can anybody help me?

ps: fsck is runned because i mounted windows partition over 30 times

---

### Post by an.echte.trilingue on 2006-12-01
What filesystem is your windows partition? (FAT or NTFS)

---

### Post by m.aicardi on 2006-12-01
> **carniolus said:**
> Hi!
but now, every time i start computer in xp, it crashes at login time with one
of the famous blue screens.
BUT, my ubuntu works great!


Nothing strange...

XP has always had (and always will have) its BSOD (Blue Screen Of Death).

There is NO correlation with your great Ubuntu.

Crashing is just the normal way of XP works. You have now to reinstall Windows XP.

Please keep in mind that when you will reinstall Windows, XP will DELETE your MBR (Master Boot Record), where the Ubuntu loader is stored. This way you will become unable to boot Ubuntu again as long as you will not restore the Ubuntu MBR.

To backup and restore you will need a Ubuntu LiveCD, too.

To backup your MBR you have to open Bash and give this command:

```
sudo dd if=/dev/sda of=~/ubuntu_mbr.img bs=512 count=2
# [replace sda with your Ubuntu installation harddisk]
```

Then you can reinstall Windows and then you boot your Ubuntu LiveCD, open up a terminal and give this commands

```
mkdir /tmp/ubuntu
sudo mount /dev/sda1 /tmp/ubuntu
# [replace sda1 with your Ubuntu partition; you can get a clue with command mount]
sudo dd of=/dev/sda1/home/<yourname>/ubuntu_mbr.img of=/dev/sda bs=512 count=2
# [replace sda with your Ubuntu installation harddisk]
```

Then you can restart your system and your Ubuntu will be alive again.

Please note that these commands are NOT guaranteed to work with your system, therefore ask a Linux expert friend before.

Please use command dd with EXTREME CARE; it can erase EVERYTHING from your HDs if used with wrong parameters.

Cheers.

Marco

---

