---
title: "[SOLVED] help usb device will wount as read only in flux and mounts fine in kde"
date: 2008-05-22
forum: Hardware
---

### Post by jza873 on 2008-05-22
ok so lately i been using the fluxbox wm.  kde got to sluggish.  here is the issue, i have a 300gb maxtor external hd (vfat).  on kubuntu 8.04 when in the kde desktop it auto mounts my external hd in /media/disk (which it creates automatically).  it works great i can read write and execute all files.  no once i log into flux since its so minimalistic it doesn't auto mount it.  so  i type in

sudo mkdir /media/disk-1/ 
sudo mount /dev/sdb1/ /media/disk-1/

it mounts fine except its read only.  so i cant save any files to it which kind of defeats the purpose of the large hd.  but if i'm in a terminal and i use su or sudo its mine to own (it works like it does in kde).  so i was wondering if any one knew the command that ubuntu runs when it auto mounts file systems.  i was thinking about trying a different wm but i put so much work into fulx yesterday and its just so so damn fast.  
hay thanks in advance for any one that can help me out.

---

### Post by jza873 on 2008-05-22
SOLVED  i been battling this since i used slackware 2 years ago.  and i just figured it out.

might be a little excessive but i dont have to be root any mroe to get this to work

sudo mount -t vfat -o rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=1000,utf8,shortname=lower /dev/sdb1 /media/disk

ther is the command if any one else needs it

---

