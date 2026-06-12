---
title: "acpi errors can't turn off acpi because nvidia driver requires it."
date: 2018-02-13
forum: Hardware
---

### Post by richard378 on 2018-02-13
Any suggestions please.  This error goes away with the grub option acpi=off but that crashes the NVIDIA driver and only can be used with the nouveau driver.  How can I turn off this error and still use the NVIDIA driver?
Ubuntu 17.10.1 fresh install multiple installs all have same error. the Motherboard Z97-HD3 has no direct linux drivers that I can install.  I don't know what to do about this warning so far I am ignoring it, but would like a better solution.

journalctl -b shows every boot.

Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI Warning: SystemIO range 0x0000000000001828-0x000000000000182F conflicts with OpRegion 0x0000000000001800-0x000000000000187F (\PMIO) (20170531/utaddress-247)
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI Warning: SystemIO range 0x0000000000001C40-0x0000000000001C4F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170531/utaddress-247)
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20170531/utaddress-247)
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI Warning: SystemIO range 0x0000000000001C30-0x0000000000001C3F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170531/utaddress-247)
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001C3F (\GPRL) (20170531/utaddress-247)
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI Warning: SystemIO range 0x0000000000001C00-0x0000000000001C2F conflicts with OpRegion 0x0000000000001C00-0x0000000000001FFF (\GPR) (20170531/utaddress-247)
Feb 13 15:38:31 richard-Z97-HD3 kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb 13 15:38:31 richard-Z97-HD3 kernel: lpc_ich: Resource conflict(s) found affecting gpio_ich

---

### Post by #&amp;thj^% on 2018-02-13
I was told by a kernel developer that a user should have never seen those "ACPI Error" 
And was more meant to be used for developer's for their needs.
EG you see:```
richard-Z97-HD3 kernel: ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
```
As long as things are working Ok I wouldn't worry about them.
Here's Mine:
```
[    6.984975] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170831/dsopcode-235)
[    6.985246] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.985466] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.985746] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170831/dsopcode-235)
[    6.986097] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.986302] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.986578] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170831/dsopcode-235)
[    6.986833] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.987105] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.987389] input: HP WMI hotkeys as /devices/virtual/input/input10
[    6.987512] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20170831/dsopcode-235)
[    6.987766] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.987973] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20170831/psparse-550)
[    6.988312] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bi
```
And my system performs nicely.

---

### Post by richard378 on 2018-02-13
I have been trying this page: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)
When I try "pnpacpi=off"it becomes a acpi error with nvidia-uvm package. specificity and assume it is causing my graphics problems 
Like i said I'm ignoring it, for now.  since you say nothing can be done I will continue to ignore it.

As it is I am getting gnome errors regardless of the above settings acpi on or off,  and have posted on the desktop forum regarding that.

---

### Post by richard378 on 2018-02-17
Found a fix:

[https://bbs.archlinux.org/viewtopic.php?id=163556](https://bbs.archlinux.org/viewtopic.php?id=163556)
the easy way to fix this **** is to
blacklist pcspkr
blacklist lpc_ich
blacklist gpio-ich

This is a known bug that is Triaged to upstream and has not update since 2015.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1280467](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1280467)
[https://bugzilla.kernel.org/show_bug.cgi?id=44991](https://bugzilla.kernel.org/show_bug.cgi?id=44991)

---

### Post by jontis on 2018-09-18
-

---

