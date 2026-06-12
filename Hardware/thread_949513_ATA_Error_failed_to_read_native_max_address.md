---
title: "ATA Error: failed to read native max address"
date: 2008-10-16
forum: Hardware
---

### Post by Eremit on 2008-10-16
```
Oct 11 21:45:53 skynet kernel: [  291.719681] ata5.01: failed to read native max address (err_mask=0x4)
Oct 11 21:45:53 skynet kernel: [  291.719687] ata5: failed to recover some devices, retrying in 5 secs
Oct 11 21:45:58 skynet kernel: [  296.719661] ata5: soft resetting link
Oct 11 21:45:58 skynet kernel: [  297.047898] ata5.00: configured for UDMA/33
Oct 11 21:45:58 skynet kernel: [  297.047902] ata5.01: configured for UDMA/100
Oct 11 21:45:58 skynet kernel: [  297.047917] ata5: EH complete
Oct 11 21:45:58 skynet kernel: [  297.067478] sd 4:0:1:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Oct 11 21:45:58 skynet kernel: [  297.080580] sd 4:0:1:0: [sda] Write Protect is off
Oct 11 21:45:58 skynet kernel: [  297.094858] sd 4:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 11 21:45:58 skynet kernel: [  297.101153] sd 4:0:1:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Oct 11 21:45:58 skynet kernel: [  297.104581] sd 4:0:1:0: [sda] Write Protect is off
Oct 11 21:45:58 skynet kernel: [  297.109191] sd 4:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

I get these errors pretty frequently but **only when I use the AMD Catalyst Driver** for my HD4850. When using vesa for example I don't get any errors, so I think my harddrive should be ok.
Because of that bug I switched to Intrepid but it's still the same.

Did a short test too:
```
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      7860         -

```

Any Ideas? Please :(

---

