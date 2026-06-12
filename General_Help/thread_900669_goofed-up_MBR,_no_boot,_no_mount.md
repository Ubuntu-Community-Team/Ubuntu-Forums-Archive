---
title: "goofed-up MBR, no boot, no mount"
date: 2008-08-25
forum: General Help
---

### Post by diogenes_3 on 2008-08-25
This isn't really a Linux problem in the first place, but I made it one by trying to use Ubuntu to resolve it.

I have a Toshiba Satellite M70-187 notebook, Windows XP on the first partition, Ubuntu 8.04 on the second, GRUB on the MBR.

I seriously goofed: I played with the Toshiba recovery disc, I merely wanted to see what exactly was on it, so I booted from it. I expected it to show me some dialogue options, instead it just ran off without any user intervention, immediately starting to "recover" my PC, where recover obviously means overwrite my data with an image of a new Windows. 

When I realized that I panicked: my backup, as is always the case with those, was neither complete nor current. So I hard-powered-off the computer. On reboot it wouldn't boot to an OS, nor say "insert a disc", only a blinking cursor stared at me menacingly. An Ubuntu live CD sees a harddisk, but no partitions, and says it couldn't mount it (*$MFTMirr error: Invalid mft record*). I tried *ntfsfix*, but to no avail, it ends with the same error.

Apparently the tool has eaten my MBR and/or MFT, hopefully without finding the time to actually overwrite my data. 

I read about a Windows recommendation, *chckdisk /f* from a Windows CD, or about [BartPE]("http://www.nu2.nu/pebuilder/"), but only now realize I don't acutally *have* a Windows CD, the recovery disc obviously being anything but that. I understand I can always run the recovery disc again, getting my PC back, but I would very much like to please get my data back first. Any chances?

---

### Post by dannyboy79 on 2008-08-25
good luck, here's the only way I know how to recover partition tables etc etc.

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

---

