---
title: "[Errno 5] Input/output error"
date: 2008-08-14
forum: General Help
---

### Post by Rooker on 2008-08-14
Thank you whoever it was that created wubi. Awesome program.

I had quite a bit of trouble getting it to install Kubuntu last night. Tried Ubuntu, Kubuntu and Kubuntu 64bit and it kept failing on the install with this error:

> The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

At some random point in the "copying files" part of the install it would spit out that error message, then load into the LiveCD.

I ran a chkdsk /f and defragged ahead of time and obviously wasn't even using a CD. The same .ISOs installed fine into a virtual machine and I have it running now, so the images were fine. 

What seems to have fixed it finally was choosing the "No ACPI" option in the Grub boot menu before installing and it completed fine. I haven't had any problems booting up after it installed.

Not sure if this is a wubi issue or an Ubuntu issue. I found quite a few people with the same problem while Googling. 

My Hard drive is a 300GB SATA Maxtor on an NVIDIA MCP55 Chipset mobo (you'll have to help me out if you need more specific details).

---

