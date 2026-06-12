---
title: "Won't install on old hardware"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Tony Goodwin on 2005-09-26
So I just bought an old laptop. It is a Compaq LTE 5300

I don't know how to install Ubuntu onto it. I have Ubuntu 5.04 on a bootable CD. It will not boot from the CD (or any CD for that matter). It can boot from a floppy. I have successfully booted both a Win98 boot disk, and Hal91 (Linux on a floppy). Unfortunately, the floppy and cd-rom share a bay, and you can't use both at the same time. They may be warm-swappable, but I have been unable to verify that.

It is not networkable. It does have a pcmcia 56k modem card. However it goes to a regular phone line, not an ethernet port. Any ideas?

-Tony

---

### Post by karuptdata on 2005-09-26
This may sound retarded but in your machiines bios is it set to boot from cd first??It sounds like your machine is set to boot from floppy....

---

### Post by Tony Goodwin on 2005-09-26
[QUOTE=karuptdata]This may sound retarded but in your machiines bios is it set to boot from cd first??It sounds like your machine is set to boot from floppy....[/QUOTE]


Yeah, its too old to boot from cd.

---

### Post by lompolo on 2005-09-27
Don't know if this helps. I have not tried. But check link.
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

---

### Post by mr_mop on 2005-09-27
I've installed on a Toshiba 3410CT with only a floppy disc and a PCMCIA ethernet card.  It is  possible :)
Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

As I had DOS on floppy I installed that rather than a Windows install. I then installed GRUB in the DOS partion and put the GRUB launch in config.sys and not boot.ini as described there.

Oh and you only have a modem, which is a bit bad.  Any way you can get a PCMCIA ethernet?

---

### Post by Tony Goodwin on 2005-10-03
[QUOTE=mr_mop]I've installed on a Toshiba 3410CT with only a floppy disc and a PCMCIA ethernet card.  It is  possible :)
Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

As I had DOS on floppy I installed that rather than a Windows install. I then installed GRUB in the DOS partion and put the GRUB launch in config.sys and not boot.ini as described there.

Oh and you only have a modem, which is a bit bad.  Any way you can get a PCMCIA ethernet?[/QUOTE]

Just bought one today.

---

### Post by mr_mop on 2005-10-04
Thats great.  I hope all goes well! :)

---

