---
title: "fat32 partition not showing in ubuntu"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by mike2005 on 2005-04-26
Hi.
    I reinstalled ubuntu (a clean install) after i did some changing to my partitions to allow ubuntu more space.

Now I have a fat32 partition named "windows" which showed up in ubuntu the first time i installed it. Now that i have reinstalled it, the partition is not there. I can not find it anywhere either.

Yet from windows xp its entirely visible so that i can copy files onto it (in the hope i may access them from ununtu as my main windows partition is ntfs)

Also if anyone can help with the threat i posted LOL typo, i mean thread: swansmart ii pci modem (i can't get this modem working under ubuntu)

Please dont assume i know much about linux. I am only familiar with windows (and obsolete os's like amiga os's, old mac os's, apple ii's, dos, commodoore 64, sys 64738, poke 53280,0, lda #0, sta 53280, inc 53281, rts, ahh those days  :) :) :)

Thanks if you can help

Mike

---

### Post by bored2k on 2005-04-26
Type this into a terminal and tell us the results:
sudo fdisk -l
df -h

This would show your partitions and their current state. So we know what commands to give you.

[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat) can be of great help. Any asistance, we are here.

---

### Post by indianajones123 on 2007-09-04
Hey all, I jumped the gun posting.  I initially had the same problem.  I had a FAT32 partition that I created as "osshare" during install.  It never showed on the desktop or in Computer, but was a 100gb folder in my File System as /osshare.  I modified /etc/fstab to this:

UUID=7028-183E  **/media/osshare **       vfat    defaults,utf8,umask=007,gid=46 0 

Now it loads fine as a separate drive for 100ish gigs.  However, that /osshare folder is still there with 37.5 gigs free which I don't get.  Can I safely delete this?  Still new to linux so I don't want to screw anything up.  Thanks, and did I do this correctly by changing fstab?

---

### Post by strabes on 2007-09-04
So what exactly is the problem??

---

### Post by indianajones123 on 2007-09-04
sorry, jumped the gun on my post, see my edits, thanks.

---

