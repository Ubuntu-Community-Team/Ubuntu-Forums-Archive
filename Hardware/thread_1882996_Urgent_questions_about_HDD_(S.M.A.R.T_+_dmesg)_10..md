---
title: "Urgent questions about HDD (S.M.A.R.T + dmesg) 10.04LTS"
date: 2011-11-18
forum: Hardware
---

### Post by Sneux on 2011-11-18
Alright ladies and gentlemen here is the issue. Lately I have been having some weird system hangs, an inquiry into dmesg lead me to believe that they were Hard Drive related so I watched dmesg and messages log as well as checked the S.M.A.R.T what I saw worried me as I don't know what it means but it doesn't look good. I need someone to interpret to tell me if I should be worried as well as if so how soon should I be looking for a replacement (plan to just replace the entire laptop if the hard drive ends up failing, yes I do have the cash for it but I really don't want to spend it unless it is absolutely necessary).

```

[19838.906827] ata2.00: status: { DRDY ERR }
[19838.906829] ata2.00: error: { UNC }
[19838.910991] ata2.00: configured for UDMA/133
[19838.910999] ata2: EH complete
[19841.163490] ata2.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[19841.163494] ata2.00: irq_stat 0x40000001
[19841.163497] ata2.00: failed command: READ FPDMA QUEUED
[19841.163502] ata2.00: cmd 60/28:00:b0:8d:49/00:00:18:00:00/40 tag 0 ncq 20480 in
[19841.163503]          res 41/40:28:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19841.163506] ata2.00: status: { DRDY ERR }
[19841.163508] ata2.00: error: { UNC }
[19841.163510] ata2.00: failed command: READ FPDMA QUEUED
[19841.163515] ata2.00: cmd 60/08:08:08:08:40/00:00:1b:00:00/40 tag 1 ncq 4096 in
[19841.163516]          res 41/04:28:ca:8d:49/00:00:18:00:00/00 Emask 0x1 (device error)
[19841.163518] ata2.00: status: { DRDY ERR }
[19841.163520] ata2.00: error: { ABRT }
[19841.163522] ata2.00: failed command: READ FPDMA QUEUED
[19841.163526] ata2.00: cmd 60/08:10:f0:10:81/00:00:17:00:00/40 tag 2 ncq 4096 in
[19841.163527]          res 41/04:28:ca:8d:49/00:00:18:00:00/00 Emask 0x1 (device error)
[19841.163530] ata2.00: status: { DRDY ERR }
[19841.163531] ata2.00: error: { ABRT }
[19841.167673] ata2.00: configured for UDMA/133
[19841.167683] ata2: EH complete
[19843.682952] ata2.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x0
[19843.682957] ata2.00: irq_stat 0x40000008
[19843.682960] ata2.00: failed command: READ FPDMA QUEUED
[19843.682966] ata2.00: cmd 60/28:10:b0:8d:49/00:00:18:00:00/40 tag 2 ncq 20480 in
[19843.682967]          res 41/40:28:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19843.682969] ata2.00: status: { DRDY ERR }
[19843.682971] ata2.00: error: { UNC }
[19843.687170] ata2.00: configured for UDMA/133
[19843.687190] sd 1:0:0:0: [sda] Unhandled sense code
[19843.687192] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[19843.687195] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[19843.687199] Descriptor sense data with sense descriptors (in hex):
[19843.687201]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[19843.687207]         18 49 8d ca 
[19843.687210] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[19843.687215] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 18 49 8d b0 00 00 28 00
[19843.687222] end_request: I/O error, dev sda, sector 407473610
[19843.687237] ata2: EH complete
[19846.698961] ata2.00: exception Emask 0x0 SAct 0x8 SErr 0x0 action 0x0
[19846.699005] ata2.00: irq_stat 0x40000008
[19846.699033] ata2.00: failed command: READ FPDMA QUEUED
[19846.699070] ata2.00: cmd 60/08:18:c8:8d:49/00:00:18:00:00/40 tag 3 ncq 4096 in
[19846.699071]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19846.699160] ata2.00: status: { DRDY ERR }
[19846.699185] ata2.00: error: { UNC }
[19846.778814] ata2.00: configured for UDMA/133
[19846.778824] ata2: EH complete
[19849.141384] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19849.141432] ata2.00: irq_stat 0x40000008
[19849.141462] ata2.00: failed command: READ FPDMA QUEUED
[19849.141497] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19849.141498]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19849.141591] ata2.00: status: { DRDY ERR }
[19849.141618] ata2.00: error: { UNC }
[19849.178546] ata2.00: configured for UDMA/133
[19849.178558] ata2: EH complete
[19851.540457] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19851.540503] ata2.00: irq_stat 0x40000008
[19851.540532] ata2.00: failed command: READ FPDMA QUEUED
[19851.540568] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19851.540570]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19851.540663] ata2.00: status: { DRDY ERR }
[19851.540690] ata2.00: error: { UNC }
[19851.577605] ata2.00: configured for UDMA/133
[19851.577620] ata2: EH complete
[19853.884553] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19853.884598] ata2.00: irq_stat 0x40000008
[19853.884628] ata2.00: failed command: READ FPDMA QUEUED
[19853.884665] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19853.884666]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19853.884760] ata2.00: status: { DRDY ERR }
[19853.884785] ata2.00: error: { UNC }
[19853.921651] ata2.00: configured for UDMA/133
[19853.921663] ata2: EH complete
[19856.305590] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19856.305634] ata2.00: irq_stat 0x40000008
[19856.305661] ata2.00: failed command: READ FPDMA QUEUED
[19856.305698] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19856.305699]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19856.305790] ata2.00: status: { DRDY ERR }
[19856.305816] ata2.00: error: { UNC }
[19856.342736] ata2.00: configured for UDMA/133
[19856.342754] ata2: EH complete
[19858.682649] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19858.682695] ata2.00: irq_stat 0x40000008
[19858.682723] ata2.00: failed command: READ FPDMA QUEUED
[19858.682760] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19858.682763]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19858.682857] ata2.00: status: { DRDY ERR }
[19858.684412] ata2.00: error: { UNC }
[19858.719799] ata2.00: configured for UDMA/133
[19858.719814] sd 1:0:0:0: [sda] Unhandled sense code
[19858.719816] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[19858.719820] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[19858.719823] Descriptor sense data with sense descriptors (in hex):
[19858.719825]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[19858.719832]         18 49 8d ca 
[19858.719834] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[19858.719839] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 18 49 8d c8 00 00 08 00
[19858.719846] end_request: I/O error, dev sda, sector 407473610
[19858.721399] ata2: EH complete
[19861.971251] ata2.00: exception Emask 0x0 SAct 0x5 SErr 0x0 action 0x0
[19861.972789] ata2.00: irq_stat 0x40000001
[19861.974301] ata2.00: failed command: READ FPDMA QUEUED
[19861.975828] ata2.00: cmd 60/08:00:d0:88:07/00:00:18:00:00/40 tag 0 ncq 4096 in
[19861.975829]          res 41/04:08:ca:8d:49/00:00:18:00:00/00 Emask 0x1 (device error)
[19861.978887] ata2.00: status: { DRDY ERR }
[19861.980349] ata2.00: error: { ABRT }
[19861.981825] ata2.00: failed command: READ FPDMA QUEUED
[19861.983321] ata2.00: cmd 60/08:10:c8:8d:49/00:00:18:00:00/40 tag 2 ncq 4096 in
[19861.983323]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19861.986349] ata2.00: status: { DRDY ERR }
[19861.987852] ata2.00: error: { UNC }
[19862.021322] ata2.00: configured for UDMA/133
[19862.021331] ata2: EH complete
[19864.339182] ata2.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[19864.340697] ata2.00: irq_stat 0x40000008
[19864.342188] ata2.00: failed command: READ FPDMA QUEUED
[19864.343686] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19864.343687]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19864.346671] ata2.00: status: { DRDY ERR }
[19864.348124] ata2.00: error: { UNC }
[19864.376333] ata2.00: configured for UDMA/133
[19864.376342] ata2: EH complete
[19866.903323] ata2.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[19866.904854] ata2.00: irq_stat 0x40000008
[19866.906343] ata2.00: failed command: READ FPDMA QUEUED
[19866.907848] ata2.00: cmd 60/08:08:c8:8d:49/00:00:18:00:00/40 tag 1 ncq 4096 in
[19866.907849]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19866.910858] ata2.00: status: { DRDY ERR }
[19866.912363] ata2.00: error: { UNC }
[19866.940472] ata2.00: configured for UDMA/133
[19866.940479] ata2: EH complete
[19869.258390] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19869.259897] ata2.00: irq_stat 0x40000008
[19869.261410] ata2.00: failed command: READ FPDMA QUEUED
[19869.262918] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19869.262919]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19869.265957] ata2.00: status: { DRDY ERR }
[19869.267467] ata2.00: error: { UNC }
[19869.295522] ata2.00: configured for UDMA/133
[19869.295531] ata2: EH complete
[19871.613430] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19871.614961] ata2.00: irq_stat 0x40000008
[19871.616488] ata2.00: failed command: READ FPDMA QUEUED
[19871.617996] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19871.617998]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19871.621028] ata2.00: status: { DRDY ERR }
[19871.622489] ata2.00: error: { UNC }
[19871.650579] ata2.00: configured for UDMA/133
[19871.650586] ata2: EH complete
[19874.100540] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[19874.102126] ata2.00: irq_stat 0x40000008
[19874.103638] ata2.00: failed command: READ FPDMA QUEUED
[19874.105168] ata2.00: cmd 60/08:00:c8:8d:49/00:00:18:00:00/40 tag 0 ncq 4096 in
[19874.105169]          res 41/40:08:ca:8d:49/00:00:18:00:00/00 Emask 0x409 (media error) <F>
[19874.108156] ata2.00: status: { DRDY ERR }
[19874.109626] ata2.00: error: { UNC }
[19874.137692] ata2.00: configured for UDMA/133
[19874.137707] sd 1:0:0:0: [sda] Unhandled sense code
[19874.137709] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[19874.137712] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[19874.137716] Descriptor sense data with sense descriptors (in hex):
[19874.137718]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[19874.137725]         18 49 8d ca 
[19874.137728] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[19874.137733] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 18 49 8d c8 00 00 08 00
[19874.137740] end_request: I/O error, dev sda, sector 407473610
[19874.139273] ata2: EH complete

```

I would REALLY appreciate feedback on what this means in detail if you can as well as 'how' you know that is what it means, such as what to watch out for, what the big flashing neon arrows are that I need to look out for as well as where I can learn more about this sort of stuff not only on the Ubuntu/Linux Troubleshooting side but as well as the Hardware side. Thank you so much!

---

### Post by WasMeHere on 2011-11-18
Hi Sneux,

When SMART blows the whistle, then you should watch out, but don't panic! I think your hard drive is failing now. If possible do the necessary research from another computer until you know what to do and then do it as efficiently as possible to rescue your personal files as well as system settings.

There is a good tool to rescue failing disks, ***ddrescue***. You should run it from another drive, for example a live CD or USB drive and save the data by cloning the failing drive to another one of at least the same size. Browse the internet for ddrescue tutorial or something like that to learn about it.

Good luck
Olle

---

### Post by Sneux on 2011-11-18
Thank you very much Olle I shall do so now, still curious as to what exactly is going wrong though, especially what the dmesg output means.

---

### Post by alarme on 2011-11-18
Hi,

Modern HDD have some hidden spare sectors. If during operation the HDD hardware detects that a sector starts to fail, copy the contents to a spare sector, and then marks it as "bad"
As can be seen in the SMART report, this disk has 99 spare sectors, and detected 100 defective ones, therefore there is no possibility of substitution of the latter.

In this situation, if the OS requests to read a bad sector, the drive returns an error code reading.

At dmesg:
[19874.137740] end_request: I/O error, dev sda, sector 407473610

You must replace that disk as soon as possible.  More time you wait, more errors you get (and more data you lose).

Good luck

---

### Post by Sneux on 2011-11-18
> **alarme said:**
> Hi,

As can be seen in the SMART report, this disk has 99 spare sectors, and detected 100 defective ones, therefore there is no possibility of substitution of the latter.

In this situation, if the OS requests to read a bad sector, the drive returns an error code reading.

At dmesg:
[19874.137740] end_request: I/O error, dev sda, sector 407473610

You must replace that disk as soon as possible.  More time you wait, more errors you get (and more data you lose).

Good luck

Where exactly does it say it has 100 defective onse, I thought it said 35?

---

