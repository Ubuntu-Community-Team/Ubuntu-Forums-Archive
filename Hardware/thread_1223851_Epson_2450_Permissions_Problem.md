---
title: "Epson 2450 Permissions Problem"
date: 2009-07-26
forum: Hardware
---

### Post by technoholic on 2009-07-26
Another newbie with scanner problems here. I have two scanners attached, both are IEEE1394 interfaces. The Nikon Coolscan works fine and is seen by xsane and vuescan.
The problem is with an Epson Perfection 2450 Photo which is not seen by either app.

Executing "gksudo xsane" works with the both 2450 and Coolscan scanners.

Executing xsane from the menu under my userid does not work with the 2450.
Executing xsane from the menu under my userid works OK with the Coolscan

Executing "sudo sane-find-scanner" returns:
found SCSI processor "EPSON GT-9700 1.05" at /dev/sg5
found SCSI scanner "Nikon LS-4000 ED 1.10" at /dev/sg6

Executing "sane-find-scanner" returns:
found SCSI scanner "Nikon LS-4000 ED 1.10" at /dev/sg6

After 2 days working on this, it seems (to me) to be a permissions issue causing the problem but I haven't had enough experience to know how to correct it. Am I on the right track? Can anyone help?

I should add that I am running 9.04, Jaunty.   Thanks.

---

