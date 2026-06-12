---
title: "Proper configuration of lm-sensors for IT8718?"
date: 2016-12-07
forum: Hardware
---

### Post by bcschmerker on 2016-12-07
On the Hot Rod gPC™, the lm-sensors indicator applet in Unity 7 constantly reads it8718-isa-0228 Fan 3 as zero where Fans 1, 2, and 4 (4 is a need-to-find, as it is not displayable as of 7 December 2016) for the same chip are nonzero and apparently correspond to SYS_FAN, NB_FAN, and CPU_FAN on the Gigabyte® GA-MA78GM-S2HP v2.0 with BIOS Revision F6D.  The figures temp1 through temp3 for the same chip correctly track sensors on different parts of the 'board  In which subdirectory of /etc would I locate the correct conf or rc file?  (The feeds from k8temp-pci-00c3 are not at issue.)

---

