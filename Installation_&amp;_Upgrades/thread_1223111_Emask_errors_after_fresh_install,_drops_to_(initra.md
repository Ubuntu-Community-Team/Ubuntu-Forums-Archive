---
title: "Emask errors after fresh install, drops to (initramfs) prompt"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by Rippy on 2009-07-25
I have an Acer Aspire Timeline (AS3810TZ) laptop, nice and new. The pre-installed Vista runs without problems, and Spinriting the drive showed no defects, so I'm assuming the Hitachi 320GB drive is working fine. However, I can't get Ubuntu 9.04 to successfully install.

The live cd and install work fine. But when I try to boot it for the first time, I slowly get dozens of errors like this: (where XX.XXXXXX is a number which increases after each error, presumably to do with the hard disk)

```
[   XX.XXXXXX] ata2.00: STATUS: { DRDY }
[   XX.XXXXXX] ata2.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x6 frozen
[   XX.XXXXXX] ata2.00: cmd 60/08:00:95:58:0c/00:00:08:00:00/40 tag 0 ncq 4096 in
[   XX.XXXXXX] ata2.00: res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
```

It then gives up and drops to an "(initramfs)" prompt which I do not know how to deal with.

I tried installing 9.10 Alpha 2 before, and it still gets all these same errors but somehow manages to boot nonetheless, after many minutes. Updating it ruins it however. Trying the latest daily build of 9.10 did not work at all either.

Does anyone know how to fix this? Ubuntu's just been getting easier and easier for me over the years, but now it's suddenly broken because of some random hard drive compatibility issue? My searches have found that Hitachi drives have produced Emask errors for people, but those threads are years old...

Well, any help is appreciated! Thanks!

-Rippy

---

### Post by Rippy on 2009-07-26
Bump? Still looking for help...

Can someone at least help me create a GRUB loader for my Vista partition so that my laptop isn't bricked anymore? I don't know how to do that without booting into Ubuntu...

---

### Post by ionospheric on 2009-08-29
get supergrub, install windows MBR

---

### Post by Acer3810T on 2009-09-06
I get the same error when I try to run Ubuntu 9.04 and 9.10 Alpha 5 (both x64) on my Acer 3810T, so there might be some general incompatibility here.

---

### Post by ionospheric on 2009-09-08
I just went to Fry's and booted Ubuntu NBR 9.04 from a USB stick on the Acer timeline 3810TZ (they actually let me!)
I saw the same error message during the boot process. However after a while, the boot process continued, and everything worked!
- Intel 4500 graphics adapter at full resolution, fast
- wireless
- sound
- webcam

The partition editor saw the hard disk.

I could probably live with that error message, as long as it boots at some point, and hope that a future Ubuntu will do away with the problem.

Have you tried changing SATA mode from AHCI to IDE in the BIOS?

---

