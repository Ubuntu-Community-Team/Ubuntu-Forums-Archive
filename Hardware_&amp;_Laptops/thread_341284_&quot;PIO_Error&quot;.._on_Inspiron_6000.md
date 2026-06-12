---
title: "&quot;PIO Error&quot;..? on Inspiron 6000"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by antar on 2007-01-18
I've posted about this before (with no response), but now I have more information.

I've had this problem for a while that, never more than once a session, in Ubuntu, my Inspiron 6000 will start "skipping" for about a minute--it'll freeze up for a couple seconds, then be all right for a few more, then freeze up again.

Looking at the System Monitor, I'm not seeing any spikes in CPU usage, but just recently I had the brilliant idea of looking at the system log.

Here's what I see:

```
Jan 18 12:33:51 localhost kernel: [17185700.572000] ata2: PIO error
Jan 18 12:34:25 localhost kernel: [17185730.668000] ipw2200: Firmware error detected.  Restarting.
Jan 18 12:34:25 localhost kernel: [17185730.668000] ata2: PIO error
Jan 18 12:34:25 localhost kernel: [17185730.692000] ata2: PIO error
Jan 18 12:34:25 localhost kernel: [17185730.692000] ata2: no sense translation for error 0x20
Jan 18 12:34:25 localhost kernel: [17185730.692000] ata2: no sense translation for status: 0x51
Jan 18 12:34:25 localhost kernel: [17185730.820000] sr: Current [descriptor]: sense key: Aborted Command
Jan 18 12:34:25 localhost kernel: [17185730.820000]     Additional sense: Scsi parity error
```

Since the PIO error comes first, I'm thinking that's the culprit.

What does this mean?

Thanks for the help.

---

