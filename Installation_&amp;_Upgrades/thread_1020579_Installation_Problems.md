---
title: "Installation Problems"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by bimmer jake on 2008-12-24
Here's all the facts as i know them. 

i'm trying to install 8.10 on my laptop (toshiba satellite a215-s7422).
amd turion dual core 1 gig ram 160 gig hard drive.

i've had 8.04 on the same laptop in the past.

i initially tried to install the 64 bit got an error then, thinking the error was a problem with the 64 bit version, i tried the 32 bit and got the same error.

this is what my screen currently says...

[     0.412025] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait...


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   70.732367] end_request: I/O error, dev sr0, sector 1431184
[   70.732407] Buffer I/O error on device sr0, logical block 178898



Is this telling me that my hard drive took a dive? :confused:

i did the disk check and all was ok.  i also ran the memory test and it checked out.

thanks for any thoughts that might help.

---

### Post by taurus on 2008-12-24
How fast did you burn the ISO image?  If you set it as a default, try burning it again except at a slower speed like 4x if you can.

---

### Post by bimmer jake on 2008-12-24
Same exact error. 

I'm specifically concerned about the i/o error.  Should i not be worried about this?

---

### Post by Pumalite on 2008-12-24
Do md5sum on the iso. Do not use CD-RW. Clean the lens in your burner. Burn a new CD

---

