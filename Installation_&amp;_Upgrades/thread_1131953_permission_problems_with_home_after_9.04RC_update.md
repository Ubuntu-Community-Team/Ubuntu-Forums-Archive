---
title: "permission problems with /home after 9.04RC update"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by rusyear04 on 2009-04-21
**[COLOR="Red"]UPDATE: Problem SOLVED!![/COLOR]**

i don't know how & why but i (apparently) managed to fix the situation. it seems that -although it gave errors- the chmod did work out. for the first, things are running smooth.

thanx to this forum for the usually great help anyhow!


=====================
hi everybody!

i experience some problems with my /home directory premissions... situation:

i deleted my old root & swap partitions and left /home as it was. i installed 9.04RC into the empty space and used the exiting /home again as home. now most of the things work all right, but apperently there are some permission problems i can not change by simple chmod or chown.

maily this is .ICEauthority which gives me an error at every log-in (even if i change it to 777 before).
the .gvfs is "dr-x--------- user user" and cannot be changed at all.

do you have any ideas?
can this be related to the fact that i'm accessing the /home from winXP with an ext2-plugin?

for debugging...

fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=bf268ab5-313b-47b6-a1cf-9f1966691f1f /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=db79bc61-9750-4d6f-9fac-f1e53d79398d /home           ext3    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=e8edf8d7-9180-45db-9744-626299c37a8b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0     
```

in my /home/user i have
```

dr-x------  2 user user     0 2009-04-21 16:33 .gvfs

```
which i cannot change by any means to 777.

thanks in advance!

---

