---
title: "Can't print on a LPT printer shared by a Ubuntu system"
date: 2008-07-24
forum: Hardware
---

### Post by N-t-F on 2008-07-24
Hi all,

not sure it is the right place to post about printing problems, but I guessed it could fit the "hardware" tag :???:

So, I do have a printer (HP 4250 dtn) plugged on the parallel port of a PC running Ubuntu Hardy Heron. Printing from this PC works pretty well.

Now I try to print from another PC also running Ubuntu Hardy Heron but any attempt fails (except the test page, which prints nicely, oddly enough :shock: ) Oh, and when I try to print using lpr from the remote computer, I get a weird message saying:

```
lpr: Unauthorized
```

Unauthorized ? :shock: Before you ask: I've checked the rights and the lpr program is executable. Not to mention that I get the very same error when logged as root.

Here is the /etc/cups/printers.conf from the server:
```
# Printer configuration file for CUPS v1.3.7
# Written by cupsd on 2008-07-24 14:51
<DefaultPrinter hp_243>
Info hp_243
Location pg22
DeviceURI parallel:/dev/lp0
State Idle
StateTime 1216823192
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option orientation-requested 3
</Printer>

```

And the one from the client:

```
# Printer configuration file for CUPS v1.3.7
# Written by cupsd on 2008-07-24 14:42
<DefaultPrinter hp_243>
AuthInfoRequired negotiate
Info hp_243
Location pg22
DeviceURI ipp://pg22:631/printers/hp_243
State Idle
StateTime 1216903364
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option orientation-requested 3
</Printer>
```

Any hint would be welcome... :)

---

### Post by prshah on 2008-07-24
Just a suggestion: On both computers, configure cups by opening the below address in a browser:```
http://localhost:631
```

I find it easier to use than printconf

If you've already configured using this, or if this doesn't show up any obvious problems, I don't know what's up, sorry.

---

### Post by N-t-F on 2008-09-24
Oops, forgot to answer. I'm sorry. The problem has been solved in a very unrefined way : I had to reinstall the system because of other issues and this solved the lpr problem as well...

---

