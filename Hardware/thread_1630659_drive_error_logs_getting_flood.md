---
title: "drive error? logs getting flood"
date: 2010-11-25
forum: Hardware
---

### Post by Brzhk on 2010-11-25
Hello,

I started my computer today to see my log file getting flood with theses messages:

[QUOTE="messages"]Nov 25 19:28:36 gauss kernel: [  131.191036] sr 0:0:0:0: ioctl_internal_command return code = 8000002
Nov 25 19:28:36 gauss kernel: [  131.191039]    : Sense Key : Aborted Command [current] [descriptor]
Nov 25 19:28:36 gauss kernel: [  131.191044]    : Add. Sense: No additional sense information
Nov 25 19:28:38 gauss kernel: [  133.066604] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov 25 19:28:38 gauss kernel: [  133.106531] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov 25 19:28:38 gauss kernel: [  133.147036] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov 25 19:28:38 gauss kernel: [  133.188188] sr 0:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Nov 25 19:28:38 gauss kernel: [  133.188285] sr 0:0:0:0: ioctl_internal_command return code = 8000002
Nov 25 19:28:38 gauss kernel: [  133.188288]    : Sense Key : Aborted Command [current] [descriptor]
Nov 25 19:28:38 gauss kernel: [  133.188293]    : Add. Sense: No additional sense information
Nov 25 19:28:40 gauss kernel: [  135.061989] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov 25 19:28:40 gauss kernel: [  135.101896] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov 25 19:28:40 gauss kernel: [  135.141806] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov 25 19:28:40 gauss kernel: [  135.183576] sr 0:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00[/QUOTE]


and

[QUOTE="kern"]Nov 25 19:29:14 gauss kernel: [  169.023459] ata1.00: status: { DRDY ERR }
Nov 25 19:29:14 gauss kernel: [  169.063349] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 25 19:29:14 gauss kernel: [  169.063352] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Nov 25 19:29:14 gauss kernel: [  169.063361] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov 25 19:29:14 gauss kernel: [  169.063362]          res 51/04:00:00:89:00/00:00:00:00:00/00 Emask 0x1 (device error)
Nov 25 19:29:14 gauss kernel: [  169.063365] ata1.00: status: { DRDY ERR }
Nov 25 19:29:14 gauss kernel: [  169.103256] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 25 19:29:14 gauss kernel: [  169.103259] sr 0:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
Nov 25 19:29:14 gauss kernel: [  169.103268] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Nov 25 19:29:14 gauss kernel: [  169.103269]          res 51/04:00:00:89:00/00:00:00:00:00/00 Emask 0x1 (device error)[/QUOTE]

I sense it is drive related, but all my drives seems to work fine.

What should i do ?

---

### Post by Brzhk on 2010-11-26
the problem seems to be only a glitch... i'll close the thread then.

---

