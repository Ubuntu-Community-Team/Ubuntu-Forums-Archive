---
title: "Blank Partition list..."
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Midnitewolf on 2009-02-26
Ok, first off i'll give a few details about my installation. I'm trying to install ubuntu 8.10, most recent one. I downloaded and burned the .iso image onto a bootable cd. I have over 100 gigs free space on my hdd, and about 3 gigs of ram, and my normal OS is windows vista 64 (quad core phenom proc)

Im trying to install ubuntu, but when i reach step 4, the partitions list is totally blank, and its impossible to proceed beyond this point. I googled around for some help but the only answers i found were totally chinese to me, something about going to a shell and entering a slash command, which i couldnt understand for the life of me.

I just want to install ubuntu as a secondary OS for when im running certain programs.

Any help out there? (and please explain in detail, im not much of a pc whiz with linux)

---

### Post by taurus on 2009-02-26
I think you mean something like open a terminal and run this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be a lower case letter L, not number 1.

---

### Post by Midnitewolf on 2009-02-26
> **taurus said:**
> I think you mean something like open a terminal and run this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That would be a lower case letter L, not number 1.

what would that do though? Thats not deleting or messing up my original windows is it? I want to have 2 OS', and one time a long time ago, i accidentally used some command like that that destroyed one of the OS i had on my system

---

### Post by pw_f100_220 on 2009-02-26
fdisk -l will just list your partitions.  no actual action takes place.  very helpful in many cases

---

### Post by Mark Phelps on 2009-02-27
Sorry for a basic question ... but is it "free" space (as inside a partition), or "unpartitioned" space (as in not partitioned).  Folks here have used the same term for both situations.

If it's unpartitioned space, you could download a GParted LiveCD, burn it, boot from it, and partition the empty space as Ext3. The Ubuntu installer should then see it just fine.

Since you're using Vista, I trust you have a Vista DVD to boot from in case there are problems?  If not, suggest you visit the NeoSoft forums to download a Recovery CD. They have both 32-bit and 64-bit available.  If anything happens to your Vista OS partition, you will need this to boot and do Startup Repair to get Vista working again.

---

### Post by Midnitewolf on 2009-03-01
i ran this sudo command, absolutely nothing happened. It just gave me a new line to enter text in

anything else i could do?

---

