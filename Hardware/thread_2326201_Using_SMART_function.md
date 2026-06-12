---
title: "Using SMART function"
date: 2016-05-29
forum: Hardware
---

### Post by fund_raiser on 2016-05-29
Hello
SMART option is disabled by default in BIOS on my machine. As far as I know SMART relocates, or can relocate bad sectors to spare ones. My question is:

_If the SMART option is disabled in BIOS, will SMART still relocate bad sectors (if any occur) to other areas of the drive?_


PS
Strangely enough 'HD tune' on Win OS (I have two systems win and linux) shows data in *SMART section*, and says that the disk is OK. How is this possible if the SMART is disabled in BIOS?

---

### Post by DuckHook on 2016-05-30
As far as I know, SMART is a function of your HDD, not your MOBO. Therefore, I'm not sure that BIOS can actually stop a SMART query from the OS. Perhaps the BIOS setting just disables SMART data from showing in your BIOS. I freely admit that I'm skating on thin ice here. Not a HDD or MOBO expert. You can query SMART in *buntu as well by using the *Disks* app > the Settings button at top right > SMART Data & Self-Tests

---

### Post by weatherman2 on 2016-05-30
The BIOS can't disable S.M.A.R.T. - it can only disable the connection to the hard drive's S.M.A.R.T. controller.  In theory disabling it could speed up communications with the drive, but in practice, as I understand it, not really (in the old days, maybe).  The hard drive's firmware (which is what is reallocating sectors, etc.) functions the same whether or not the BIOS has enabled talking to it.

---

