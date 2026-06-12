---
title: "Screen error - Software or Graphic Card issue??"
date: 2015-05-19
forum: Hardware
---

### Post by maravingian on 2015-05-19
Hi All,

I`ve recently noticed an error message when booting up my computer before it reaches the Ubuntu password screen;

[       1.652390]  ACPI PCC probe failed.
starting version 219

Does anyone know what this means?

AMD FX(tm)-6300 Six-Core Processor × 6 
GeForce GT 520/PCIe/SSE2, running Nvidia binary driver - version 346.59 from nvidia-346 (proprietary, tested)
64 bit Ubuntu 15.04
7.8GiB Memory
306.5GB

BUSH TV LED 22982FHD.  I`ve tried changing monitors but it still comes up with the same message..

Cheers for any help :)

---

### Post by Bashing-om on 2015-05-19
maravingian; Hello;

Yeah, known issue, of no import if your system boots with no problems:
> 
The kernel is probing ACPI, looking for the "Platforms communication channel" interface. This is a new ACPI interface and not much hardware currently supports it.
(matt_symes)

[http://ubuntuforums.org/showthread.php?t=2275310](http://ubuntuforums.org/showthread.php?t=2275310)

PCC (Platform Communication Channel) is a recent ACPI 5.0 addition. The driver does not find a PCC communications mailbox and just exits with that error message. It is not something to worry about, most machines don't have an ACPI PCCT table and they don't use this mechanism.
References:
ACPI specification Chapter 14.0 "Platform Communications Channel"
Linux source: drivers/mailbox/pcc.c


If you do have the hardware, one might do :
```

sudo systemctl enable sddm.service -f
sudo reboot

```

After this your computer should be able to boot up normally.

[INDENT][INDENT]as we evolve
[INDENT][INDENT][INDENT]merrily along
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by maravingian on 2015-05-20
Cheers for the update :) 

Hopefully when i upgrade my computer next the system will be able to use ACPI!!

---

### Post by grahammechanical on 2015-05-20
I believe that the comment "starting version 219" is referring to the version of systemd that is being used. Ubuntu switched from Upstart to SystemD part way through the 26 week development period of 15.04. I have been seeing those two messages ever since. I am still seeing them now that I have moved on to the development version of 15.10 (Wily Werewolf).

Wily Werewolf is running great!

Regards.

---

