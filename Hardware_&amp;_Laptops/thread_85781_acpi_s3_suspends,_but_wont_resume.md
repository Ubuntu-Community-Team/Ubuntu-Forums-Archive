---
title: "acpi s3 suspends, but wont resume"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by Kirk Wolf on 2005-11-03
I've built a desktop system for my father and I would really really like to get suspend to ram (acpi s3) working.  (He's fanatical about not leaving it "turned on", "wasting electricity", but he won't use it nearly as much if it takes too long to turn on.....  :-)

I've just installed Breezy, updated it, etc.  All seems to work fine.

Anyway, I have a Biostar BIOSTAR GEFORCE 6100-M7 (CRU51-M7) motherboard, which has a Nforce C51 northbridge and MCP51 southbridge.  I'm using the VESA x-driver for now, which seems to work fine.

I've edited /etc/default/acpi-support as documented elsewhere to enable suspend to ram.  (I uncommented "ACPI_SLEEP_MODE=mem" ).

Suspend works fine.  If I press a key on the keyboard it powers back up, but thats the end of it.

- the display remains off
- the keyboard caps light turns on/of when I press caps lock, but its connected to a KVM, so that might be a false positive.
- it doesn't respond to pings, so networking doesn't seem to be up.
- my usb mouse doesn't get power

its not clear that anything has resumed.
Is there a log anywhere that would tell me what happened when it tried to resume?  Any help for diagnosing the problem would be appreciated.

---

