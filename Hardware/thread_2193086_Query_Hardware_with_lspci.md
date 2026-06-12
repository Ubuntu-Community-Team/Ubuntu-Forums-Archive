---
title: "Query Hardware with lspci"
date: 2013-12-11
forum: Hardware
---

### Post by damienthogan on 2013-12-11
Hi,

I've been having problems with my wireless card (I don't need to go into that now though).

the lspci -v command on my laptop tells me I have: "Intel Corporation Centrino Advanced-M 6235" but the manufacturer of my system are telling me I have an "Atheros Killer e220 Wireless-N 1202" card and that I must just have an Intel driver installed.

Edit: I have reinstalled the OS (formatting the drive) twice, trying 12.04 and 13.10 and both tell me I have an Intel card.

From my basic understanding the lspci command queries the actual hardware and not just the driver so in this case I do actually have an Intel card.

Can someone confirm, or advise me here, as to whether I am correct or if it is possible I just have an Intel driver and an Atheros card?

Thanks,

---

### Post by steeldriver on 2013-12-11
The way I think it works is that lspci probes the PCI vendor ID and device ID values reported by the device itself, and then looks these up in a database in order to provide the human readable description of the device. It's unlikely that the device is reporting the wrong PCI IDs (although it is sometimes possible to modify these values, if they are in EEPROM and the device firmware supports writing - don't ask me how I know...), and it's unlikely that the database is wrong (especially since the Intel and Atheros vendor IDs are probably the 2 best known ones).

You can see the actual PCI ID numbers themselves by running lspci with the -nn ("numbers and names") switch for example

```

$ lspci -vnn | grep '\[0280\]'
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [[COLOR=#0000ff]**8086**[/COLOR]:[COLOR=#ff8c00]**4230**[/COLOR]] (rev 61)

```

Here [COLOR=#0000ff]**8086 **[/COLOR]is an Intel vendor ID - for Atheros it would be **168C** I think

---

### Post by damienthogan on 2013-12-11
Thank you.

---

