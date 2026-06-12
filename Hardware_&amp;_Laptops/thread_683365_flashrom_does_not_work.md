---
title: "flashrom does not work"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by karunadheera on 2008-01-30
i tried the command "sudo flashrom -V -w P5GC-MX-ASUS-1333-0310.ROM"

but it does not work for my mainboard.

configuration:
[LIST]
[*]MB : P5GC-MX-ASUS-1333 - ASUS (Running 800 FSB).
[*]PROC : INTEL Pentium D 3000 (4MB L2) 800 FSB.
[*]Graphics : NVidia GeForce 6600 GT / 256MB (SLI) - Single PCI Express.
[*]HD : 160GB SAMSUNG SATA (3GB/s)
[/LIST].

Following is the output i get when i try to update my BIOS. Please help me! :(:confused:

Thanks!
Prageeth Karunadheera.

[INDENT]
[COLOR="DarkRed"]prageeth@prageeth-desktop:~/Desktop$ sudo flashrom -V -w P5GC-MX-ASUS-1333-0310.ROM
Calibrating delay loop... 430M loops per second. ok
No LinuxBIOS table found.
Found chipset "ICH7/ICH7R": Enabling flash write... OK.
Probing for Am29F040B, 512 KB
probe_29f040b: id1 0xff, id2 0xff
Probing for Am29F016D, 2048 KB
probe_29f040b: id1 0xff, id2 0xff
Probing for AE49F2008, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for At29C040A, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for At29C020, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for Mx29f002, 256 KB
probe_29f002: id1 0x2e, id2 0x26
Probing for SST29EE020A, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for SST28SF040A, 512 KB
probe_28sf040: id1 0xff, id2 0xff
Probing for SST39SF010A, 128 KB
probe_jedec: id1 0x47, id2 0x90
Probing for SST39SF020A, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for SST39SF040, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for SST39VF020, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for SST49LF040B, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for SST49LF040, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for SST49LF020A, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for SST49LF080A, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for SST49LF002A/B, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for SST49LF003A/B, 384 KB
probe_jedec: id1 0x66, id2 0xc1
Probing for SST49LF004A/B, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for SST49LF008A, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for Pm49FL002, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for SST49LF004C, 512 KB
probe_49lfxxxc: id1 0xff, id2 0xff
Probing for SST49LF008C, 1024 KB
probe_49lfxxxc: id1 0xff, id2 0xff
Probing for SST49LF016C, 2048 KB
probe_49lfxxxc: id1 0xff, id2 0xff
Probing for SST49LF160C, 2048 KB
probe_49lfxxxc: id1 0xff, id2 0xff
Probing for Pm49FL004, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for W29C011, 128 KB
probe_jedec: id1 0x47, id2 0x90
Probing for W29C020C, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for W49F002U, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for W49V002A, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for W49V002FA, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for W39V040FA, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for W39V040A, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for W39V040B, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for W39V080A, 1024 KB
probe_jedec: id1 0xff, id2 0xff
Probing for M29F002B, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for M29F002T/NT, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for M29F400BT, 512 KB
probe_m29f400bt: id1 0xff, id2 0xff
Probing for M29F040B, 512 KB
probe_29f040b: id1 0xff, id2 0xff
Probing for 82802ab, 512 KB
probe_82802ab: id1 0xff, id2 0xff
Probing for 82802ac, 1024 KB
probe_82802ab: id1 0xff, id2 0xff
Probing for F49B002UA, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for LHF00L04, 1024 KB
probe_lhf00l04: id1 0xff, id2 0xff
Probing for S29C51001T, 128 KB
probe_jedec: id1 0x47, id2 0x90
Probing for S29C51002T, 256 KB
probe_jedec: id1 0x2e, id2 0x26
Probing for S29C51004T, 512 KB
probe_jedec: id1 0xff, id2 0xff
Probing for S29C31004T, 512 KB
probe_jedec: id1 0xff, id2 0xff
No EEPROM/flash device found.[/COLOR]
[/INDENT]

---

