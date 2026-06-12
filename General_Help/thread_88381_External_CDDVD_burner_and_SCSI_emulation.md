---
title: "External CD/DVD burner and SCSI emulation"
date: 2005-11-10
forum: General Help
---

### Post by Douglas Royds on 2005-11-10
I have an NEC CD/DVD burner in an external USB 2.0 box. I succeeded in burning a data CD using Gnomebaker, but failed to burn an audio CD with the following message:

[INDENT]cdrecord: No such file or directory. Cannot open '/dev/sg*'. Cannot open SCSI driver. [/INDENT]

I understand that kernel 2.6 does not need SCSI emulation for IDE drives. Things get complicated when using an IDE drive via USB, as USB drives appear to be SCSI. My burner appears as /dev/sg0. I fixed the problem with the following addition to Grub:

[INDENT]kopt=sg0=ide-scsi ...[/INDENT]

So burning audio CDs now works, but is this an appropriate fix, or am I missing something here?

What's the best fix, and how can this be fed back into Ubuntu?

For the record, I had been able to burn audio CDs using this burner under Hoary, but it failed after the upgrade to Breezy. Any ideas why?

---

