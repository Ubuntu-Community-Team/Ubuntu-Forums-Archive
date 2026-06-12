---
title: "cupsdAuthorize: Local authentication certificate not found"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by lduperval on 2006-07-02
Hi,

I am having trouble printing from a CUPS 1.1.x client to Dapper. Printing worked correctly before I upgraded, but now that I have, I keep getting:

cupsdAuthorize: Local authentication certificate not found
cupsdAuthorize: Local authentication certificate not found

in my CUPS error log. I don't understand what it means. I searched around on the forums and tried removing authentication, restart CUPS, creating a new printer, setting my printer as default, I tried changing the Listen directive to 

*:631

nothing works.

There is something in my configuration that is preventing me from accessing my printer remotely, and I can't figure out what.

Can anyone help?

L

---

### Post by lduperval on 2006-07-02
I can print locally without a problem. The problem only appears when I try to print from another machine.

L

---

### Post by SeanKaneFLA on 2007-07-15
Dear L,

Did you find a solution to this?  I'm seeing this same issue with my Macs trying to print to a Konica printer over the network.

Thanks,
Sean

---

### Post by lduperval on 2007-07-15
Oh man, that was so long ago  I don't remember. I think that I added a line to the Location with Allow for the machines that access the print server.

L

---

### Post by SeanKaneFLA on 2007-07-15
Thanks! 

Actually, I am trying to print directly to the printer via the network, I'm not using anything to "share" the printer.

Still stumped...
Sean

> **lduperval said:**
> Oh man, that was so long ago  I don't remember. I think that I added a line to the Location with Allow for the machines that access the print server.

L

---

