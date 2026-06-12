---
title: "Partion problem no root file system defined?"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by telmore007 on 2009-02-26
Ok, I used my recovery disk and but Vista back on my computer but when I did I split it up into two drives. Drive D is what I want to put Ubuntu and have Vista for programs I can't run in ubunutu. I get this error when I select manual install. And when I highlight over the partition I want. Which is dev/sda5 size 168316 mb. What am I doing wrong? Lady_Tiffany_2002@yahoo to find me on messenger. 

Thanks

---

### Post by taurus on 2009-02-26
Make sure you tell the installer to mount /dev/sda5 to / and format it.

---

### Post by Therion on 2009-02-26
Well if you want to set up that partitions manually you're going to have to partition and format / (root), /swap and /home (if you want a separate "home" partition (optional)).

The easier solution would be to use the option for installing Ubuntu on the largest contiguous free-space and let the installer create the partitions.

---

### Post by phani450 on 2009-03-12
i am also having the same problem....
my laptop is HP dv6701us with 2GB ram and 160 GB HDD...
the laptop came with recovery partition and C drive with Vista OS

i made two more partitions....and i want to place ubuntu in one of these partition....
i installed ubuntu from vista using "Wubi installer"....
when i entered in to ubuntu after reboot it is giving me the error as "no root file system defined" and giving something like "correct it from partition table".....

When i am installing ubuntu from CD it is taking total 160GB for ubuntu without showing actual partions...but whn i tried in my frnd laptop(same model dv6701) it works well...

I want both vista and ubuntu in my laptop...

plz help meeeeeee
:(:(:(:(

---

