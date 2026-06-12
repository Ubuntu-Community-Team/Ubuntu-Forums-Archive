---
title: "[SOLVED] Keeping /home"
date: 2008-10-13
forum: General Help
---

### Post by Ms_Angel_D on 2008-10-13
Hi guys,

Can someone give me a run down of how you keep your /home partition during an install, I would like to be prepared when 8.10 is released.

thanks in advance,
Angel

---

### Post by Idefix82 on 2008-10-13
If you upgrade, then you will keep everything anyway. It's only an issue if you do a clean install. In that case, put your /home folder on a separate partition if it isn't there already and when you install Intrepid, choose that partition to mount as /home but uncheck the "format partition" box - very simple.

---

### Post by Ms_Angel_D on 2008-10-13
Opps yeah I forgot to mention, that /home is already on it's own partition. I just hadn't re-installed yet with it being there, so I was unsure as to the process.

---

### Post by Joeb454 on 2008-10-13
Moved to GH :)

---

### Post by dirtylobster on 2008-10-13
Is that method foolproof? I'm thinking about doing a clean install and I wouldn't want to make a ******** of backups. My /home is on its own partition.

---

### Post by -Zeus- on 2008-10-13
foolproof?  I guess so...

---

### Post by Sam on 2008-10-13
> **dirtylobster said:**
> Is that method foolproof? I'm thinking about doing a clean install and I wouldn't want to make a ******** of backups. My /home is on its own partition.

Yep as long as you don't choose the "format partition" option for /home everything will go smoothly.

---

### Post by howefield on 2008-10-13
Nothing is absolutely foolproof, just a question of acceptable risk or not.

If you have data on your machine you do not want to lose, it should be backed up to a seperate disk, dvd, whatever. Hard disks die.

---

### Post by ssam on 2008-10-13
even if you home is on your root partition (the default), then you can do a clean install without wiping it.

in the installer choose manual partitioning.

select you root partition, set it to be mounted at '\' and make sure 'format' is not ticked. when you click ok you will be wanted that the system folders (/usr, /bin etc) will be wiped. continue. your /home directory will be left intact.

of course you should never do an install with out a back up.

---

