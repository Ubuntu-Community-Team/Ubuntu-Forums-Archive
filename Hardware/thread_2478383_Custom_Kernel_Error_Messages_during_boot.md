---
title: "Custom Kernel: Error Messages during boot"
date: 2022-08-25
forum: Hardware
---

### Post by manmath on 2022-08-25
I'm running the latest Lubuntu with a heavily modified zen kernel. I've stripped everything of the kernel that's not necessary for a home desktop. The system is running blazing fast. Boots in 1.5 sec. Applications also start and run fast. However I do see lots of error messages during booting. The typical error message is like "Failed to check xyz." I know it can't find "xyz" cos I've disabled or stripped that off during kernel compilation. I want to makes some changes in some systemd config files so that it won't try to find "xyz". Well, here're the error messages:
```

root@manmath:~# dmesg | grep -i error
[    1.575297] [drm:fw_domains_get_normal [i915]] *ERROR* render: timed out waiting for forcewake ack to clear.
root@manmath:~# dmesg | grep -i fail
[    1.017717] systemd[1]: Failed to find module 'autofs4'
[    1.137616] systemd[1]: Journal Audit Socket was skipped because of a failed condition check (ConditionSecurity=audit).
[    1.138310] systemd[1]: Huge Pages File System was skipped because of a failed condition check (ConditionPathExists=/sys/kernel/mm/hugepages).
[    1.138373] systemd[1]: POSIX Message Queue File System was skipped because of a failed condition check (ConditionPathExists=/proc/sys/fs/mqueue).
[    1.138439] systemd[1]: Kernel Debug File System was skipped because of a failed condition check (ConditionPathExists=/sys/kernel/debug).
[    1.138495] systemd[1]: Kernel Trace File System was skipped because of a failed condition check (ConditionPathExists=/sys/kernel/tracing).
[    1.141728] systemd[1]: File System Check on Root Device was skipped because of a failed condition check (ConditionPathExists=!/run/initramfs/fsck-root).
[    1.144638] systemd[1]: Repartition Root Disk was skipped because all trigger condition checks failed.
[    1.165511] systemd[1]: Platform Persistent Storage Archival was skipped because of a failed condition check (ConditionDirectoryNotEmpty=/sys/fs/pstore).
root@manmath:~# dmesg | grep -i disable
[    0.000000] NX (Execute Disable) protection: active
[    0.001440] Kernel/User page tables isolation: disabled on command line.                                                                                                                                      
[    0.001711] ACPI: Early table checksum verification disabled                                                                                                                                                  
[    0.082543] core: PMU erratum BJ122, BV98, HSD29 workaround disabled, HT off                                                                                                                                  
[    0.092068] ACPI: PCI: Interrupt link LNKB disabled                                                                                                                                                           
[    0.092163] ACPI: PCI: Interrupt link LNKE disabled                                                                                                                                                           
[    0.092195] ACPI: PCI: Interrupt link LNKF disabled                                                                                                                                                           
[    0.139697] Serial: 8250/16550 driver, 4 ports, IRQ sharing disabled                                                                                                                                          
[    0.183629] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp                                                                                             
[    0.909920] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Quota mode: disabled.                                                                                                                  
[    1.163923] EXT4-fs (sdb1): re-mounted. Quota mode: disabled.                                                    

```

---

