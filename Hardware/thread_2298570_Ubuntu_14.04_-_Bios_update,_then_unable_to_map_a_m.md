---
title: "Ubuntu 14.04 - Bios update, then unable to map a mount point on raid card - NEED HELP"
date: 2015-10-12
forum: Hardware
---

### Post by nick_b3 on 2015-10-12
Hello,

I did a BIOS upgrade on a SuperMicro X10DRG-HT from bios 1.0b to version 1.0c.  After completing the BIOS update correctly the Raid card doesnt seem to be able to access the drives because it keeps rebooting itself.  When it boots up it should map /data to /dev/sdd1 however it cannot on boot with some output like:

Scsi 0:0:0:0: WARNING: (0x06:0x002C): Command (0x12) timed out, resetting card
3w-sas: shutting fown host 0.
3w-sas: Shutdown Complete
Scsi 0:0:0:0: Device offlined - not ready after error recovery
ata9.00: exception Emask 0x0 SAct 0x40000000 SErr 0x0 action 0x6 frozen
ata9.00: failed command: READ FPDMA QUEUED
ata9.00 status DRDY
ata9: hard resetting link
ata9: SATA link up 6.0 GBPS (SStatus 113 SControl 300)
scsi 0:0:1:0 WARNING (0x06:0x002C): Command (0x12) timed out, resetting card

How can i test the drives behind the raid card to see if the drives are bad or if the raid card is bad?  Also, i suppose the port could be bad as well?  Like i said, it worked fine before i did the BIOS update tho so i was thinking it could be a BIOS setting however everything looks correct.  I had no knowledge of how this was setup before i was asked to complete the BIOS update so any help will be appreciated.

---

### Post by nick_b3 on 2015-10-12
Sorry guys first post ever. I realize i may have incorrectly categorized my thread.  Please let me know if you need any additional information.  All help would be appreciated.

---

### Post by nick_b3 on 2015-10-13
Reverted BIOS back to original version and the card is working again.  I guess the Raid card needs to be updated before i can run a BIOS update?

---

### Post by weatherman2 on 2015-10-13
What problems were you trying to fix with the BIOS update?  If you can't list any, don't update it.

---

