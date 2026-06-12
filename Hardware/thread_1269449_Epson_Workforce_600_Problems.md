---
title: "Epson Workforce 600 Problems"
date: 2009-09-18
forum: Hardware
---

### Post by gradysghost on 2009-09-18
Hello, everyone.  I picked up an Epson Workforce 600 a while back, and it prints great from Ubuntu Jaunty, but there are two other primary problems.

[LIST=1]
[*]Even when plugged in via USB cable, XSane refuses to see the scanning device which is part of the printer.
[*]I can access the memory card's file share over the network in Windows with the standard \\IP.ADD.RE.SS format, but trying to get to it via SMB in Nautilus doesn't work.
[/LIST]

Regarding the first one, the specific error I receive is the "no devices available" dialog.  There doesn't appear to be any further information.

As for the second, I have not tried mounting it at the CLI using CIFS, but Nautilus has always managed to map things accessible with \\wi.nd.ow.s if I only do smb://the.same.ip.addy in its toolbar.  Anyone know if it's using some special kind of file sharing protocol?

I have workarounds for both of these things, but they're sloppy and ugly.  I'd really like this to work natively.

---

### Post by frilock on 2009-10-06
bump for you i cant get the card reader to work ether im using it via wifi

---

