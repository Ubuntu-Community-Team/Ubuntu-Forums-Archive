---
title: "[SOLVED] Ubuntu 8.04 and ECS D6VAA v1.1 motherboard"
date: 2008-09-09
forum: Hardware
---

### Post by GiveLove on 2008-09-09
Hello people,

Just passing along some information that I figured out.
I have a secondary computer that is using an old ECS D6VAA v1.1 motherboard with BIOS version 1.2e. I am only using one of the two CPU sockets. In it sits a socket 370 1Ghz Intel Celeron. This motherboard uses the VIA 82C694X northbridge and VT82C686B southbridge. (no chuckling, this was a freebie) :D

Anyways I was only able to get a stable install of Ubuntu 8.04 by specifying the "noapic" command on the first screen that comes up when the install CD boots up. So far it has run for 12 hours straight with absolutely no problems. Before having tried that, after successfully installing Ubuntu 8.04, it would consistently, and completely freeze randomly in anywhere from 5 to 30 minutes of usage, requiring a hard reset.

I recognize this is really old and probably not very popular hardware. But perhaps it will help someone else out there.

Take care :)

---

