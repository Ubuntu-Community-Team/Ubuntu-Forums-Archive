---
title: "ata2.00: status: { DRDY ERR }"
date: 2009-10-09
forum: Hardware
---

### Post by z987k on 2009-10-09
I'm thinking this is my Hard disk crapping out, but want to make sure first.  This happens whenever I start up a guest OS(the only guest OS) in Virtual box.

Here is the error I get.  It repeats itself endlessly until I kill the virtual os(which never completes booting up.)

```

ata2.00: status: { DRDY ERR }
ata2.00: error: { UNC }
ata2.00: configured for UDMA/133
sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Descriptor sense data with sense descriptors (in hex):
        72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
        0d 56 63 af 
sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
end_request: I/O error, dev sda, sector 223765423
ata2: EH complete
sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
sd 1:0:0:0: [sda] Write Protect is off
sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```
That's the last bit of my syslog.

I googled a bit of that, and that is what leads me to believe that the drive is failing.  Something about not being able to move data off bad blocks?

I ran e2fsck -f -p and didn't get any errors back.

Is this something to do with virtualbox or the hard drive?

---

### Post by jarekl on 2009-10-12
I wouldn't be tio sure about the disk "crapping out". Installed 9.10 x86_64 on my second disk to test it and found lots of these errors, quite frequently. However, when I boot back into 9.04 i386 and make a backup of /home into the same disk I see not a single error message although I backed >33G of data. There is something fishy going on with recent kernels. 

Normally I have two identical systems which I switch between when I do something stupid on one of them and until I upgraded to 9.10 x86_64 on one of these disks I didn't see a single error message.

Have you by any chance upgrade to a recent kernel > 2.6.28? I've been looking for a solution to this and it seems this problem is of a recent date.

---

### Post by dabl on 2009-10-12
I vote for a VBox problem.  I don't actually know for sure, but my thinking is that a guest OS does not communicate directly with the real hard drive, only with the virtual disk, so the errors must therefore be all about the virtual disk, not the real one.

---

### Post by z987k on 2009-11-03
Just to update back on what fixed this.  I ended up running e2fsck -c -c on the problem partition, that found the disk problems... and well more or less fixed them.

---

