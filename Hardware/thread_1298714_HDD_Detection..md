---
title: "HDD Detection."
date: 2009-10-23
forum: Hardware
---

### Post by KaiXXV on 2009-10-23
Hey there.  I'm currently having some "interesting" troubles with my laptop.  Ubuntu both detects and is willing to interact with my HDD.  Windows XP is not.  Is there anything that would 'cause this?  I'll give a read out asap.  I'm currently busy installing Ubuntu.  *Crosses fingers*  I hope it works.

---

### Post by prshah on 2009-10-23
> **KaiXXV said:**
> Hey there.  I'm currently having some "interesting" troubles with my laptop.  Ubuntu both detects and is willing to interact with my HDD.  Windows XP is not.  Is there anything that would 'cause this?  I'll give a read out asap.  I'm currently busy installing Ubuntu.  *Crosses fingers*  I hope it works.

If your laptop is a recent one, with SATA HDD, and Windows XP is pre SP3, then Windows XP will not detect your SATA HDD.

To get Windows XP setup to detect your SATA HDD, you will need to load custom drivers for SATA (usually available on the motherboard CD) by pressing F6 during inital setup when prompted.

Or you can check if you have a BIOS option similar to "Native" or "Compatibility" or "IDE Mode"; the exact option varies from BIOS to BIOS and essentially means that the SATA HDD is presented to XP as a IDE HDD. Note that in some cases, you cannot go back to SATA mode once XP is installed and updated.

---

### Post by earthpigg on 2009-10-23
hi,

if the HDD has linux partitions, Windows will refuse to talk to or recognize those partitions.

obviously, Microsoft wants to discourage you from using non-Windows operating systems.

---

