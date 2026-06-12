---
title: "recovering linux partition"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by HosBosCos on 2006-01-05
i installed ubuntu on my second partition but then i wanted to uninstall and i opened with xp cd. i fixed mbr, now grub does not load but i can't see my linux partition form windows. how can i use that partition again without formatting windows? i really need space immediately.
thanks.

---

### Post by az on 2006-01-05
Good question.  You need to delete the second partition from your partition table and extend the first one.  You should try to use a windows tool for that.

I know the installer can shrink an ntfs partition, but I have never had the need to extend one.

---

### Post by hillbilly on 2006-01-05
Well you can use partition magic 7.0 (i use this). Partition magic can "see" the ext filesystem and you can remove it or reformat it or merge it with another partition. I have done this.

And i believe you can do it with the partitioning option in ubuntu too. I am postulating here, so dont do this unless you get some confirmation from someone who has done this. 
You can pop in the boot cd and get to the partitioning step and manually remove the linux partition, write these changes on to the hard drive and then abort the installation. This should ideally free up the space and you can see it with windows. ***NOTE: I HAVE NOT DONE THIS ***

---

