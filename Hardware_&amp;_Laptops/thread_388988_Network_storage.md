---
title: "Network storage"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by graabein on 2007-03-20
Hi, I need more disk space. 500 GB on the ethernet would be great. Has anyone had any experience with this sort of storage? 

I already have three internal disks and one external on my main box. Poor thing can't handle much more I think ;-)

Suggestions are welcome!!

---

### Post by foo Utu on 2007-03-20
network attached storage works well in Ubuntu, using Places -> Connect to Server allows you to mount many types of network filesystems.

most ethernet based external hard disks will offer SMB aka Windows file-sharing support, which can be accessed by choosing the service type Windows Share in the Connect to Server dialog box.

---

### Post by kidders on 2007-03-20
Hi there,

> **graabein said:**
> 500 GB on the ethernet would be great.Are you referring to ATA over Ethernet, or to filesharing protocols like NFS?

Since you mentioned such a large number (500GB), I'm guessing you're looking for an AoE solution. If you would like some pointers, I may be able to help you out. I use vblade and aoetools to expose and mount Ethernet-based block devices.

---

### Post by graabein on 2007-03-20
> **foo Utu said:**
> network attached storage works well in Ubuntu, using Places -> Connect to Server allows you to mount many types of network filesystems.

most ethernet based external hard disks will offer SMB aka Windows file-sharing support, which can be accessed by choosing the service type Windows Share in the Connect to Server dialog box.

So I have to look for a solution that works with Samba? 

> **kidders said:**
> Hi there,

Are you referring to ATA over Ethernet, or to filesharing protocols like NFS?

Since you mentioned such a large number (500GB), I'm guessing you're looking for an AoE solution. If you would like some pointers, I may be able to help you out. I use vblade and aoetools to expose and mount Ethernet-based block devices.

I really don't know the difference between AoE (ATA over Ethernet) and NFS. I'll look them up on wikipedia and read up on it. 

I would like an extendible solution where I can add more disks later if that is possible. Something that can just sit on the LAN and be a file server. I obviously want to use GNU/Linux with it so I don't want no Windows-only stuff. So yeah, I guess AoE is what I want.

---

### Post by kidders on 2007-03-20
> **graabein said:**
> I would like an extendible solution where I can add more disks later if that is possible. Something that can just sit on the LAN and be a file server.You can't use AoE devices as file _servers_ ... there's nothing more to them than the ATA protocol (hence the name). Often, ATA over Ethernet is used to make ginormous RAID arrays, using hard disks from multiple locations, rather than having them all in the same box.

Perhaps what you're after is file *sharing* (ie NFS, Samba, AFP, etc.). If you don't require Windoze compatibility, NFS is the usual choice.

> **graabein said:**
> I really don't know the difference between AoE (ATA over Ethernet) and NFS.

They have nothing at all in common, really. In basic terms, the difference is that if you opt for file sharing, your 500GB will be a separate, self-contained space for storing things, that will be accessible over a network. With AoE, you can, for example, extend a pre-existing RAID array by 500GB, and *then* optionally expose it using NFS/etc. to make it remotely accessible. I (perhaps wrongly) assumed this was what you were referring to, since you said "Has anyone had any experience with this sort of storage?", which is an odd thing to ask about file sharing! Chances are though, if you don't know what AoE is, you _don't_ want it.

I hope that helps... sorry for confusing the issue.

---

### Post by graabein on 2007-03-20
I think I want some kind of [NAS]("http://en.wikipedia.org/wiki/Network-attached_storage"). Any suggestions on that? Manufacturer and features etc?

And yeah, my fault also on the unlucky choice of words. I don't know too much about the subject and English is not my first language so mistakes are made :-)

---

### Post by casaschi on 2007-03-20
I have a buffalo linkstation. See buffalotech.com for details. It's basically an hard drive, with a cheap cpu and an ethernet port. Runs linux and samba with a custom webinterface.

Funny thing is that for some models, it is possible to gain root access and have access to the the linux shell. From there you can install your sw of choice, like a bittorrent client, an ssh server, a personal webserver and so on... even a full debian.
See here for more into [http://linkstationwiki.net/](http://linkstationwiki.net/)

---

