---
title: "reinstall without touch /home?"
date: 2008-09-26
forum: General Help
---

### Post by b4nsh33 on 2008-09-26
Hi, im a happy ubuntu user from several months ago, im really impresed with the distribution, i kissed windows good bye, ok, now im ready to use it exclusively, the "problem" is that from the pasts months i have been busy installing/deinstalling/evaluating packages, upgading packages, kde, kde4, fluxbox, etc, so i have a clear idea what is my favorite choice, my home dir is too big to make a backup.
i installed it in a separate partition, i was wondering if it should be posible that i reinstall from scratch leaving my current home partition intact and dont check the format option when manually create the partitions.
will the new ubuntu instalation work as spected with my old /home? , my username will be the same, will this create some kind of conflict?

---

### Post by jualin on 2008-09-26
> **b4nsh33 said:**
> Hi, im a happy ubuntu user from several months ago, im really impresed with the distribution, i kissed windows good bye, ok, now im ready to use it exclusively, the "problem" is that from the pasts months i have been busy installing/deinstalling/evaluating packages, upgading packages, kde, kde4, fluxbox, etc, so i have a clear idea what is my favorite choice, my home dir is too big to make a backup.
i installed it in a separate partition, i was wondering if it should be posible that i reinstall from scratch leaving my current home partition intact and dont check the format option when manually create the partitions.
will the new ubuntu instalation work as spected with my old /home? , my username will be the same, will this create some kind of conflict?

You got it right. I did that type of installation yesterday to try out Intrepid. No conflicts whatsoever. Just make sure during the installation you set the home partition to the "/home" mount point. Also make sure you don't check the "format" box since it will delete the home partition. Good luck!

---

