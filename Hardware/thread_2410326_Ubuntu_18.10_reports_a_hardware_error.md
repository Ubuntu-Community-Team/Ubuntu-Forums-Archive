---
title: "Ubuntu 18.10 reports a hardware error"
date: 2019-01-14
forum: Hardware
---

### Post by tommi-hoynalanmaa on 2019-01-14
Hello

I got the following errors in kern.log when I booted Ubuntu 18.10 Live:

> Jan 14 10:10:33 ubuntu kernel: [    0.044731] mce: [Hardware Error]: Machine check events logged
Jan 14 10:10:33 ubuntu kernel: [    0.044733] mce: [Hardware Error]: CPU 0: Machine Check: 0 Bank 6: ae0000000040110a
Jan 14 10:10:33 ubuntu kernel: [    0.044738] mce: [Hardware Error]: TSC 0 ADDR ff887480 MISC 78a0000086 
Jan 14 10:10:33 ubuntu kernel: [    0.044743] mce: [Hardware Error]: PROCESSOR 0:306c3 TIME 1547460536 SOCKET 0 APIC 0 microcode 25


Is this something serious?

---

### Post by Autodave on 2019-01-14
What happens if you reboot it again?  If no error message, I wouldn't worry about it.

If you get it again, some info on your machine may help.

---

### Post by tommi-hoynalanmaa on 2019-01-16
The message appeared again.

Machine information:
Lenovo G510
BIOS: 79CN44WW(V3.03)
CPU: Intel Core i5-4200M

biosdecode output:
> # biosdecode 3.0
ACPI 2.0 present.
    OEM Identifier: LENOVO
    RSD Table 32-bit Address: 0x9CFFE124
    XSD Table 64-bit Address: 0x000000009CFFE210
SMBIOS 2.7 present.
    Structure Table Length: 2805 bytes
    Structure Table Address: 0x000FD000
    Number Of Structures: 67
    Maximum Structure Size: 226 bytes


---

