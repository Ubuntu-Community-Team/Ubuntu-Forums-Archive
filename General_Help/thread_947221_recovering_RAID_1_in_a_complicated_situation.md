---
title: "recovering RAID 1 in a complicated situation"
date: 2008-10-14
forum: General Help
---

### Post by edge@freerderz.lv on 2008-10-14
I had raid1 on my edgy eft server instalation,mounted at /var. the system disk (which was not raid) broke down, so i`m now reinstaling server with hardy.

I`m not sure exactly when, but ONE of the raid disks, which were mounted in /var , had been deleted or something during several problems at reinstaling. Now this disk seems to be even not formatted, in partitioner it shows only free space. 
So now i have a half of raid left with wery important data inside. what would be the right way to recover the raid? first I would like to backup the contents of the ex-raid disk, that`s not deleted, if everything goes completely wrong. The thing is, that system is not allowing me to mount it, saying "unknow filesystem type `linux_raid_member`".

i installed raid following this: [http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server]("http://http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server").

help please!?

---

### Post by edge@freerderz.lv on 2008-10-14
> **edge@freerderz.lv said:**
> I had raid1 on my edgy eft server instalation,mounted at /var. the system disk (which was not raid) broke down, so i`m now reinstaling server with hardy.

I`m not sure exactly when, but ONE of the raid disks, which were mounted in /var , had been deleted or something during several problems at reinstaling. Now this disk seems to be even not formatted, in partitioner it shows only free space. 
So now i have a half of raid left with wery important data inside. what would be the right way to recover the raid? first I would like to backup the contents of the ex-raid disk, that`s not deleted, if everything goes completely wrong. The thing is, that system is not allowing me to mount it, saying "unknow filesystem type `linux_raid_member`".

i installed raid following this: [http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server]("http://http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server").

help please!?

ok, now i`m creating image of the good disk using ddrescue. I`m not sure, what will I do with it in case if it will be necessary, but it`s another question.

now, what would be the solution to rebuild the Raid? what info and outputs are needed?

---

### Post by fjgaude on 2008-10-14
Maybe this link will help:

[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

And this other stuff:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz

Always have backups of important data, it's the first law when using raid or any other scheme of computing. I use three, one online, near-line, off-line.

---

