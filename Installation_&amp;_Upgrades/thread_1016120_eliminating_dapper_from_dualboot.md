---
title: "eliminating dapper from dualboot"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by karrank% on 2008-12-19
Sorry if this has been posted elsewhere, couldn't find it.

I've given away this computer and need to eliminate the ubuntu partition, sorry to say, and extend the XP partition to reoccupy the entire HDD. Any advice? This n00b thanks you in advance.

---

### Post by oilchangeguy on 2008-12-19
> **karrank% said:**
> Sorry if this has been posted elsewhere, couldn't find it.

I've given away this computer and need to eliminate the ubuntu partition, sorry to say, and extend the XP partition to reoccupy the entire HDD. Any advice? This n00b thanks you in advance.

i hope you got the xp cd with the computer because you're going to need it. and you're going to need a ubuntu cd to resize the partitions. do you have these cd's available?

---

### Post by karrank% on 2008-12-19
> **oilchangeguy said:**
> i hope you got the xp cd with the computer because you're going to need it. and you're going to need a ubuntu cd to resize the partitions. do you have these cd's available?

Have the ubuntu cd but not XP it's an Emachines w/ the recovery stuff on the D: drive /dev/hda/2

---

### Post by oilchangeguy on 2008-12-19
> **karrank% said:**
> Have the ubuntu cd but not XP it's an Emachines w/ the recovery stuff on the D: drive /dev/hda/2

search google for how to create a windows boot disc. because if you remove ubuntu, you'll have to restore windows master boot record (mbr). i'd suggest just leaving it alone.

---

### Post by karrank% on 2008-12-19
> **oilchangeguy said:**
> search google for how to create a windows boot disc. because if you remove ubuntu, you'll have to restore windows master boot record (mbr). i'd suggest just leaving it alone.

Thanks for the assistance, I misspoke earlier, there is an emachines recovery disk available. But I am confused (can ya tell?). Are you suggesting I'll need to reformat the HDD to accomplish this?

---

### Post by oilchangeguy on 2008-12-19
> **karrank% said:**
> Thanks for the assistance, I misspoke earlier, there is an emachines recovery disk available. But I am confused (can ya tell?). Are you suggesting I'll need to reformat the HDD to accomplish this?

a restore cd may not work for this. and no, i'm not saying to reformat. if you uninstall ubuntu, it's boot loader goes with it. so you'll need to restore windows boot loader in order to start it.

---

### Post by cariboo on 2008-12-19
If you use the emachne restore disk, it should reformat the hard drive and install XP like the day it was first installed. You probably have to spent several hours updating it, and installing all the programs you don't need when running Ubuntu (anti-virus, anti-spyware and a firewall):).

I use the update dvd from [here]("http://www.projectdakota.net/") to speed up installing updates. I usually figure on about 6 hours to bring XP up to date.

Jim

---

### Post by karrank% on 2008-12-19
> **cariboo907 said:**
> If you use the emachne restore disk, it should reformat the hard drive and install XP like the day it was first installed. You probably have to spent several hours updating it, and installing all the programs you don't need when running Ubuntu (anti-virus, anti-spyware and a firewall):).

I use the update dvd from [here]("http://www.projectdakota.net/") to speed up installing updates. I usually figure on about 6 hours to bring XP up to date.

Jim
thanks for the reply gents and I apologize for causing this confusion, but I forgot to say I'm trying to avoid reformatting the XP side and just leave it alone if possible.

---

### Post by oilchangeguy on 2008-12-19
> **karrank% said:**
> thanks for the reply gents and I apologize for causing this confusion, but I forgot to say I'm trying to avoid reformatting the XP side and just leave it alone if possible.

please read post #6 again.

---

### Post by karrank% on 2008-12-19
Aahh, restore windows boot loader, got it, sorry, thanks.

---

### Post by karrank% on 2008-12-19
> **oilchangeguy said:**
> please read post #6 again.

I've got a spare supergrub disk laying around, can I use that?

---

### Post by oilchangeguy on 2008-12-19
> **karrank% said:**
> I've got a spare supergrub disk laying around, can I use that?

no, you'll need to use a windows xp cd, not a factory restore cd, to restore the windows boot record.

---

