---
title: "Bios update lead to ACPI boot error"
date: 2009-05-26
forum: Hardware
---

### Post by iKevin on 2009-05-26
Hi All,

I updated my BIOS today in hopes to fix an issue that I was experiencing with Vista.  The update went fine and it didn't fix the issue.  I then rebooted into to linux, which is the default for me.  While booting, I noticed the message:
```
[    0.553978] pnp 00:0b: can't evaluate _CRS: 12298<6>pnp: PnP ACPI: found 12 devices

```

The system seems to be running fine but I am unsure what, if anything, to do about the error.  Is there something that I should be looking at in the BIOS settings?  I couldn't find anything in the BIOS regarding ACPI.  Below is a snippet of the messages around the error as reported by dmesg.  Any ideas?

```
[    0.552058] pnp: PnP ACPI init
[    0.552071] ACPI: bus type pnp registered
[    0.553932] ACPI Error (dsopcode-0595): Field [ASSM] at 524320 exceeds Buffer [BUF0] size 688 (bits) [20080926]
[    0.553938] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.MEM_._CRS] (Node f6c17990), AE_AML_BUFFER_LIMIT
[    0.553970] ACPI Error (uteval-0232): Method execution failed [\_SB_.MEM_._CRS] (Node f6c17990), AE_AML_BUFFER_LIMIT
[    0.553978] pnp 00:0b: can't evaluate _CRS: 12298<6>pnp: PnP ACPI: found 12 devices
[    0.554112] ACPI: ACPI bus type pnp unregistered
[    0.554116] PnPBIOS: Disabled by ACPI PNP

```

---

### Post by iKevin on 2009-05-30
Just a minor update.  I still have this issue.  The odd thing is that I have tested power management under Vista and it all seems to be working fine.  It seems there is no answer but is anybody else experiencing such an error when booting?

---

### Post by blyfoten on 2009-07-26
I've the exact same issue, (on my HP Pavilion dv9607eo) 

It's an annoying message during boot and I would very much like to know if it's something serious and if it easily fixed

edit:
Taking a closer look I do not have the exact same problem... but very similar
```

[    0.536052] pnp: PnP ACPI init
[    0.536064] ACPI: bus type pnp registered
[    0.539023] ACPI Error (dsopcode-0595): Field [I9MN] at 544 exceeds Buffer [IORT] size 464 (bits) [20080926]
[    0.539030] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f6c15900), AE_AML_BUFFER_LIMIT
[    0.539073] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f6c15900), AE_AML_BUFFER_LIMIT
[    0.539082] pnp 00:03: can't evaluate _CRS: 12298<6>pnp: PnP ACPI: found 12 devices
[    0.541188] ACPI: ACPI bus type pnp unregistered
[    0.541192] PnPBIOS: Disabled by ACPI PNP

```

---

### Post by jymbolia on 2009-10-02
similar problem
> 
[    0.448051] pnp: PnP ACPI init
[    0.448058] ACPI: bus type pnp registered
[    0.450057] ACPI Error (dsopcode-0595): Field [I9MN] at 544 exceeds Buffer [IORT] size 464 (bits) [20080926]
[    0.450062] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f6c16900), AE_AML_BUFFER_LIMIT
[    0.450094] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f6c16900), AE_AML_BUFFER_LIMIT
[    0.450101] pnp 00:03: can't evaluate _CRS: 12298<6>pnp: PnP ACPI: found 12 devices
[    0.451747] ACPI: ACPI bus type pnp unregistered
[    0.451750] PnPBIOS: Disabled by ACPI PNP


---

### Post by llbowen on 2010-02-10
Same here:

[    0.496053] pnp: PnP ACPI init
[    0.496061] ACPI: bus type pnp registered
[    0.497944] ACPI Error (dsopcode-0595): Field [I9MN] at 544 exceeds Buffer [IORT] size 464 (bits) [20080926]
[    0.497950] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f6c16900), AE_AML_BUFFER_LIMIT
[    0.497988] ACPI Error (uteval-0232): Method execution failed [\_SB_.PCI0.LPC0.PMIO._CRS] (Node f6c16900), AE_AML_BUFFER_LIMIT
[    0.497996] pnp 00:03: can't evaluate _CRS: 12298<6>pnp: PnP ACPI: found 12 devices
[    0.499866] ACPI: ACPI bus type pnp unregistered
[    0.499870] PnPBIOS: Disabled by ACPI PNP

Any solution known?

---

