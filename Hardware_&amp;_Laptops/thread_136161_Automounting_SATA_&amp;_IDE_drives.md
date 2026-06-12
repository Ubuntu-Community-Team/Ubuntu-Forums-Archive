---
title: "Automounting SATA &amp; IDE drives?"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by Amon_Re on 2006-02-25
Is it possible to have ubuntu automount internal HD's, or is the only option available to me editing /etc/fstab ?

I have 6 hd's inside my machine & i'd rather have ubuntu mount them as if they were USB or FireWire drives

---

### Post by localzuk on 2006-02-25
I don't quite understand your query? Do you not want your internal drives to be always mounted? You cannot plug and play internal drives with the machine turned on IIRC. So this doesn't seem to make sense.

---

### Post by Amon_Re on 2006-02-25
I regularely add/remove drives, and i wonder if i could have it work like the USB & FireWire external drives work.

It's not really a problem, more of a convieniance

---

### Post by aysiu on 2006-02-25
[QUOTE=Amon_Re]Is it possible to have ubuntu automount internal HD's, or is the only option available to me editing /etc/fstab ?

I have 6 hd's inside my machine & i'd rather have ubuntu mount them as if they were USB or FireWire drives[/QUOTE] If you edit the /etc/fstab *once* and specify all your internal hard drives, they *will* be mounted every time you boot the computer. You don't have to edit the /etc/fstab file every time you want them to mount.

---

### Post by RaptorRaider on 2006-02-25
I believe you're misinterprenting localzuk's post.
IDE drivers are **not** hot-swappable; you can't just make them "work like the USB & FireWire external drives work".

---

### Post by localzuk on 2006-02-25
Ah, so the simple answer to this is no.

The confusion is caused by 'automounting' as this stage cannot even be reached.

IDE hard disks are not plug and play/hotswappable.

---

### Post by Amon_Re on 2006-02-25
Guess i'll have to restate the goal in clearer words ;) 

When i turn off my machine, hook up another SATA, IDE (or even SCSI) disk & boot, it won't mount the disk unless it's in fstab.

Is there a way to skip the editing of fstab in such a situation?

---

### Post by RaptorRaider on 2006-02-25
So **I** was misinterprenting someone's words... :-# 

If their ID's are irrelevant, I think you could try what aysiu posted.

---

### Post by Amon_Re on 2006-02-25
That's a possible route, but i'd rather have them mounted automaticly & have them appear on the desktop.

Plus, that doesn't strike me as a very "clean" approuch.

---

### Post by localzuk on 2006-02-26
Ah, that makes more sense :)

If the disk is always the same /dev/ device and always the same number of partitions + filesystem type you should just be able to have a line in your fstab which corresponds to that.

There is no way of mounting internal disks without /etc/fstab from what I have seen. I don't think internal drives are often used in such a way so it is a slightly obscure way of doing things. Have you thought about installing a firewire card and buying some external enclosures or buying extra ide/sata controllers and just having the disks hooked up permanently?

The problem with swapping hard disks like this is that they will likely become damaged over time. Little jolts involved when constantly removing and re-adding disks, IME, can damage them.

---

### Post by Amon_Re on 2006-02-26
[QUOTE=localzuk]Ah, that makes more sense :)

If the disk is always the same /dev/ device and always the same number of partitions + filesystem type you should just be able to have a line in your fstab which corresponds to that.[/QUOTE]

Nah, somehow i think that would clutter up my logs when one of them is removed. I'm slowly in the process of replacing all my old IDE drives with SATA, so i do expect things to change alot.

> There is no way of mounting internal disks without /etc/fstab from what I have seen.

Bummer :cry: 
So there is **ONE[B]**[/B] that windows does better \\:D/ 

> I don't think internal drives are often used in such a way so it is a slightly obscure way of doing things. Have you thought about installing a firewire card and buying some external enclosures or buying extra ide/sata controllers and just having the disks hooked up permanently?

I have 4 of these already :D 

> The problem with swapping hard disks like this is that they will likely become damaged over time. Little jolts involved when constantly removing and re-adding disks, IME, can damage them.

True, however, the disk controller is more prone to damage then the drives, and it's not like i swap drives internally every week, it's not that often.

Guess i'll have to live with editing /etc/fstab

---

### Post by localzuk on 2006-02-26
The other option would be to get yourself some sort of file server which can house all these drives and connect via a network to them. This way you can have them set up however you want permanently.

A cheap setup would be just to grab a fullsize atx case, a high power suppply (550W) and a relatively cheap mobo+cpu+ram, put a few sata and ide controllers in and bob's your uncle.

This is what I do to have access to 10 250Gb hdd's in one giant array. It works like a charm.

---

### Post by Amon_Re on 2006-02-26
True, been thinking of doing it, but i don't really have the space to put yet another monstrocity of a tower ;) 

I'll just have to live with it i guess

---

