---
title: "ext4 partition to iSCSI"
date: 2017-08-14
forum: Hardware
---

### Post by andrea-c on 2017-08-14
Hello.

I've been ask to convert a ext4 RAID5 24TB volume to an iSCSI target. Is it something possible to do on ubuntu?
i'm not really familiar with this and looking for ideas.

Thanks
Andrea

---

### Post by TheFu on 2017-08-15
Considering that iSCSI is a block device, this would be really easy, provided you don't need to retain any data.  Just look up how to make an iSCSI target and follow that.

iSCSI is like /dev/md0.  No file system. It is a network block device and storing data after creating a file system is the role of the iSCSI initiator (client).  The iSCSI server doesn't have a clue about file systems.  iSCSI isn't like NFS.

If you need to keep the data, well, that means backing it up, doing the iSCSI magic, then having a client copy the data back after the LUN is accessible and a file system has been added from the initiator-side (client).

There isn't any way to open a GUI and click 5 buttons and have everything changed.

Are you certain that the boss understands the request?

---

### Post by andrea-c on 2017-08-16
Hi TheFU
Thanks for your reply.

Actually we're receiving a new unit that is a ProMax server and their technical support told me to look into how to convert ext4 to iSCSI because the unit work with iSCSI and that would be the best way to mount it if samba doesn't work. I'm a bit confused now.
Is there a way to have an iSCSI partition mounted on ubuntu then? I might do the other way around as I have to keep our server data intact

---

### Post by TheFu on 2017-08-16
I looked up what ProMax server means ... ah ... you need to do this perfectly or you could be stuck with terrible performance for the next 4 yrs.

There are probably ways to do what you want, but it would mean adding an extra layer to provide a block device where one is not needed.  Performance would be impacted with the hdd, lvm, raid, file system, block device, iscsi-server, network, iscsi-client, file system .... overhead.  It would have at least 2 extra layers that aren't needed.  OTOH, if you used ZFS, then the lvm, raid, file system, would all be condensed into ZFS. ZFS provides an iSCSI server.

If you've ever used a hypervisor with virtual machines, the virtual storage devices created and used by each VM is sorta like what you'd be doing.  I have never done this, but it should work thanks to the flexibility of Unix systems.  Making a single, huge, block device would be ill-advised. There are complexities that I cannot predict in doing this.

But I would be very clear to my boss that doing this the correct way is necessary. Rebuilding the array is needed to support iSCSI. Anything less will likely end with not-so-great performance.

---

### Post by andrea-c on 2017-08-17
Wow I got lost.

I'm not entirely sure of what you're talking about in your last post.
You mean condense the ext4, lvm into a single unit to be readable from the ProMax?

---

### Post by TheFu on 2017-08-17
The short version is read the last paragraph and tell your boss that you cannot "convert" from ext4 to iSCSI.  Changing the nature of storage to a lower level requires wiping.

I've re-read the other things I wrote. It is a complex thing. If you think those paragraphs are complicated, wait until you try to manage storage doing it.  Re-re-re-re-read it until you understand.  Look up everything mentioned until you understand it. 
Or just ignore it and wipe the disks and build the iSCSI from the ground up.

---

### Post by andrea-c on 2017-08-17
Thanks, TheFu

will do that.

A.

---

