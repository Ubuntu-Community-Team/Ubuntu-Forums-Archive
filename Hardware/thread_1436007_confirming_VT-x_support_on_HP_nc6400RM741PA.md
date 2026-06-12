---
title: "confirming VT-x support on HP nc6400/RM741PA"
date: 2010-03-22
forum: Hardware
---

### Post by bob.blanchett on 2010-03-22
jumping through hoops trying to install win2008 x64 under virtualbox on this machine.
Ubuntu 9.04 Host
64 bit w2008 server guest.

trying to install x64 Win2008 server
I get a STOP 0xc000035a
from winload.exe
about 64-bit apps and the CPU ot being compatible with 64-bit mode.
--
I've run both the 3.08 OSE and the 3.1.4 from the ubuntu or virtualbox.org repositories.
"microsoft windows/windows 2008" VM.
same problem,
all the packages used have been installed via Synaptic, I havent resorted to homebrew stuff at all

the vbox.log for the VM has the error no extensions found.
Intel network adapter and IO APIC are selected and the gui details panel "says" VT-X/AMD-V: enabled!!
C"hecked a few forums and tried suggested config/biossetting check workarounds.

my config is:
HP nc 6400 model RM741PA =T5500 Core 2 Duo processor F0.B BIOS. (from lshw)
motherbaord rev:
product: 30AD
vendor: Hewlett-Packard
version: KBC Version 56.34

I haven't been able to determine the Chipset precisely beyone 945GM family
and is the controller hubs are either of 82801GHM or 82801GBM and what impact this has on effective VT support.
intel website reports that the T5500 is a VT supported 64-bit chip.

confirmed "Virtualization Technology" is set to "enable" in the Bios
the option is available, not greyed and can be enabled and disabled.
cold started system after setting enable on VT setting in bios after laptop battery removal etc.

only thing i've not done is set bios defaults and tried that.

Kernel:
bob@grytpype:~$ uname -a
Linux grytpype 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

/proc/cpuinfo does NOT however show the vmx kernel flag.

Questions:
1. I need to run 64-bit guests.. have I bought a pup?
(and I thought I did my homework about this nc6400/RM741PA giving VT support, too! bugger!)

2. Am I missing something re kernel configuration?

3. anything vbox config wise I've missed?

4. Is there a problem with BIOS support? should/can/how do I fallback if I have to?

advice/suggestions to this forum and also via email to (anonomice at gmail).. I'm crossposting at virtualbox.org linux host and windows guests forums as well as HP ITRC and ubuntu forums.

ta
Bob

---

