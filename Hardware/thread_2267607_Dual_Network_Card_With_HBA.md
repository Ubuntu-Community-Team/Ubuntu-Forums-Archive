---
title: "Dual Network Card With HBA?"
date: 2015-03-02
forum: Hardware
---

### Post by cackles on 2015-03-02
I'm going to buy a dual network card for my Ubuntu Server (under VMware). I've came across a few that have HBA, are there any advantages to getting an HBA one or is it a waste of time/money?

[SIZE=5]Thanks for the help.[/SIZE]
Re: Dual Network Card With HBA? 








Quote Originally Posted by houstonbofh View Post 

An HBA offloads iSCSI processing from the CPU. With no iSCSI, you can not use and HBA.
You've been a massive help. I found two pages straight away and understand perfectly now, thanks.


Quote Originally Posted by cackles

You've been a massive help. I found two pages straight away and understand perfectly now, thanks.

 This explained it me:
[http://www.sysprobs.com/nas-vmware-w...n-iscsi-target](http://www.sysprobs.com/nas-vmware-w...n-iscsi-target)

 This told me what I needed to do to make it work in Ubuntu Server:
[https://help.ubuntu.com/lts/servergu...initiator.html](https://help.ubuntu.com/lts/servergu...initiator.html)

 I paid £20/$30 for an HP NC380-T. I am going to go for an Dual Port + RAID HBA card once I get the money together.

 But thanks, just saying iSCSI gave me a keyword to play with. 

Someday something constructive will go here.

---

### Post by houstonbofh on 2015-03-03
How much iSCSI do you plan to do, and how CPU constrained are you?  (assuming there are even HBA drivers available)  I would just go for a good Intel nic and not worry about HBA.

---

### Post by cackles on 2015-03-04
> **houstonbofh said:**
> How much iSCSI do you plan to do, and how CPU constrained are you?  (assuming there are even HBA drivers available)  I would just go for a good Intel nic and not worry about HBA.

iSCSI I'm not sure about. I have given the server 3 virtual SCSI disks on 3 hard drives. Two of the drives are Samba and mapped. I'm also running PLEX
I have given it 4 x 3.2GHz cores (2 CPU x 2 cores each). Guess I'm ok then.

Thanks for the input.

---

### Post by houstonbofh on 2015-03-04
An HBA offloads iSCSI processing from the CPU.  With no iSCSI, you can not use and HBA.

---

### Post by cackles on 2015-03-04
> **houstonbofh said:**
> An HBA offloads iSCSI processing from the CPU.  With no iSCSI, you can not use and HBA.

You've been a massive help. I found two pages straight away and understand perfectly now, thanks.

This explained it me:
[http://www.sysprobs.com/nas-vmware-workstation-iscsi-target](http://www.sysprobs.com/nas-vmware-workstation-iscsi-target)

This told me what I needed to do to make it work in Ubuntu Server:
[https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

I paid £20/$30 for an HP NC380-T. I am going to go for an Dual Port + RAID HBA card once I get the money together.

But thanks, just saying iSCSI gave me a keyword to play with.

---

