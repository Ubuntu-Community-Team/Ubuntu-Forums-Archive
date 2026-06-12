---
title: "Dead USB stick - can you help me?"
date: 2015-02-04
forum: Hardware
---

### Post by fondatommaso2 on 2015-02-04
Good morrow,
I've got a 1GB USB stick that I had never used for awhile. I plugged it into my mother's MacBook with OS X and it was neither mounted nor detected. Then I plugged it into my Ubutntu 14.10 pc which did not detect it too. I'm almost sure it is irreparably dead, but I'd like you to give me your opinion.
The USB stick:
- does not show up in Nautilus;
- does not show up in gparted
- is not detected by dd
- *does* show up in Gnome Disks, but it cannot be formatted. Also, Gnome Disks can't give any information about it (see screenshots).
My system is in Italian so ask me if you don't understand something!
Thank you in advance.

[ATTACH=CONFIG]259713[/ATTACH]

---

### Post by sudodus on 2015-02-04
The pendrive is recognized as the mass storage device ***/dev/sdc*** which is promising. But there is no information about the size (as for the other 'generic flash disk 2 GB').

You could try to wipe the first megabyte. If it works you can use ***gparted*** and create a new partition table. If wiping the first megabyte does not work there is probably no hope, that you can revive it.


See this link: [http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by fondatommaso2 on 2015-02-04
> **sudodus said:**
> The pendrive is recognized as the mass storage device ***/dev/sdc*** which is promising. But there is no information about the size (as for the other 'generic flash disk 2 GB').

You could try to wipe the first megabyte. If it works you can use ***gparted*** and create a new partition table. If wiping the first megabyte does not work there is probably no hope, that you can revive it.


See this link: [http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

Unfortunately mkusb doesn't recognize the stick - I guess it's really dead.

---

### Post by sudodus on 2015-02-04
I'm sorry, but I think so too.

---

