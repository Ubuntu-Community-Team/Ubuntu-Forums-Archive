---
title: "AHCI or SATA mode in BIOS?"
date: 2011-01-02
forum: Hardware
---

### Post by ozzman2 on 2011-01-02
Just wondering what the general consensus is on AHCI?
Does anybody use this, or just stick with SATA mode in BIOS?

Does it matter if this option is turned on after Ubuntu (10.04) is already installed?  Any opinions if whether or not it will make things better or worse?

=)

---

### Post by llawwehttam on 2011-01-02
If you turn it on after install chances are it won't boot. You need to have it turned on before you install or enable it after parsing the AHCI hook in the kernel.

I wouldn't bother TBH. Unless you are planning on hotswapping drives there is no real point.

---

### Post by ozzman2 on 2011-01-02
I just picked up a Solid State Drive and went through all the tweaks for it (manually installed kernel 2.6.33 to enable TRIM, noatime and discard in fstab, etc.)

Just finished reading on another forum that Windows 7 does not support TRIM for SSD's unless it's in AHCI mode.  Not having much luck finding Ubuntu/Linux information on this option.  Really would like to have TRIM enabled for the longevity of the drive.

Any thoughts?

---

### Post by cascade9 on 2011-01-02
Unless you've got comptability problems, its always best to run in AHCI mode, not legacy PATA emulation. 

> **llawwehttam said:**
> If you turn it on after install chances are it won't boot. You need to have it turned on before you install or enable it after parsing the AHCI hook in the kernel.

I wouldn't bother TBH. Unless you are planning on hotswapping drives there is no real point.

I think it should boot. I havent tested this though. 

BTW, AHCI mode does more than just hotswapping. If you are running in legacy PATA emulation mode, NCQ (native command queing) is disabled as well.

---

### Post by ozzman2 on 2011-01-02
My 3 options in BIOS are SATA, AHCI or RAID.  Am I correct to assume that SATA = legacy PATA emulation?

The machine does boot when I put it in AHCI mode.  Is that a pretty good indicator that it's running in AHCI?  Or is there something else that needs to be enabled?

Your comment on Native Command Queing brings me to my next question:  If I have a standard 2TB HDD (which was previously loaded up with files while the BIOS was set to SATA), do I risk anything by now enabling NCQ?

---

### Post by cascade9 on 2011-01-02
> **ozzman2 said:**
> My 3 options in BIOS are SATA, AHCI or RAID.  Am I correct to assume that SATA = legacy PATA emulation?

The machine does boot when I put it in AHCI mode.  Is that a pretty good indicator that it's running in AHCI?  Or is there something else that needs to be enabled?

Your comment on Native Command Queing brings me to my next question:  If I have a standard 2TB HDD (which was previously loaded up with files while the BIOS was set to SATA), do I risk anything by now enabling NCQ?

I can t be sure that SATA mode = legacy PATA emulation without knowing the motherboard model. If you dont know what model it is, 'sudo lshw' (in terminal) should tell you. 

If it boots in AHCI, then you are running in AHCI. 

There is no risk with NCQ. ;)

---

