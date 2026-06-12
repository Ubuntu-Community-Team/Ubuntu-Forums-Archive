---
title: "confused : RAID array SATA card, PCI Express, linux kernel modules..."
date: 2019-01-22
forum: Hardware
---

### Post by crackers_altitude on 2019-01-22
I need to narrow down a thicket of questions I have. here goes:

I'm trying to get Ubuntu installed using the DVD drive on an Acer Aspire X1300 desktop on which the SATA controller has failed. A SATA PCIe card  - IOcrest brand, Marvell chipset 88SE9120 - is being used as a workaround to connect the DVD and SSD. This seems reasonable. The installation goes ok until a few error messages (which I can write in detail if needed - this is very time consuming) appear, which point to a few problems with the drive setup.

I have tried a number of Linux distributions, and they all give similar errors - indicating some problem with the drive setup - during installation. There does not appear to be Linux support for Marvell chipset 88SE9120, however, a number of other Marvell chipsets are, and further, Ubuntu has a long list of RAID controllers that - AFAIK - will just work, for instance some Intel, LSI, or Intel cards. I have not done anything about the BIOS messages such as "update data to DMI", and further tinkering in the BIOS configurations is not productive (for instance, changing the AHCI settings). One tiny pecularity is an inability to change the drive priority from the SSD to the DVD drive.

My hope and dream is that a new Ubuntu-approved RAID controller card will just work.

Apologies for the confused questions.

---

### Post by TheFu on 2019-01-22
I know nothing, but error messages are critical in Linux to solve problems.  Take a photo and attach it to the message as a link. This is one of the few times when a clear photo is useful. 

The install log should have those messages too, if you can get that as a file onto other media, like a flash drive, then pull the relevant parts out and copy/paste the text here. I know it exists, but haven't looked for it myself.  Perhaps in /var/log/installer/ ?

---

### Post by crackers_altitude on 2019-01-23
I transcribed most of the errors from some pictures I took of the boot process - that is, installing the lastest Ubuntu Desktop via the DVD.:

Asmedia    106X SATA Controller Ver 0.950 AHCI Mode
Copyright (C) Asmedia Technologies, Inc. All Right Reserved.
S.M.A.R.T. Supported
Using PCIE Gen 2
SATA PM    0 Port 0 Samsung 860 SSD EVO 500GB     SATA 3
SATA PM    1 Port 0 ATAPI DVD A DH16A6S           SATA 1
Press any key to exit

AHCI Option ROM    BIOS Revision: 01.07.10    Date: 12-05-2008
Copyright (c) 2006-2008    Phoenix    Technologies, LTD

device listing:
device class: ACPI controller
IRQ : 09
(no other information, such as no. device no. func. no.    vendor/device class

AMD Data Change    ... Update New Data to DMI!

[  0.000000] do_IRQ: 0.55 No irq handler for vector
[  0.038766] ACPI Exception: Could not find/resolve named package element : \_PR_.CPU0 (20170831/dspkginit-381)

[ 40.067987] ata10.00: exception Emask 0x52SACt    0x0 SErr 0xffffffff action 0xe frozen
[ 40.068007] ata10: SError: { RecovData    RecovComm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Disper BadCRC Handshk LinkS\
eq TrStaTrns UnrecFIS DevExch }
[ 40.068023] ata10.00: failed command: IDENTIFY    PACKET DEVICE
[ 40.068034] ata10.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[ 40.068034]                    res    40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x56 (ATA bus error)
[ 40.068048] ata10.00: status: { DRDY }


.....

---

### Post by TheFu on 2019-01-23
Simplify and test.  That's the normal method. Isolate each component until the exact 1 with the issue is known.
The problem is with ata10. You can trace that device under the /dev/disk/by-path/ links.

A bus error can be caused by anything in the chain.
I put the error into google: [https://askubuntu.com/questions/695557/ata8-00-exception-emask-0x52-sact-0x0-serr-0xffffffff-action-0xe-frozen](https://askubuntu.com/questions/695557/ata8-00-exception-emask-0x52-sact-0x0-serr-0xffffffff-action-0xe-frozen)  seems to say that only HDDs can be connected to some SATA controllers, so connecting optical devices isn't supported.

BTW, the Samsung storage device requires specific settings in the BIOS to be supported, doesn't it?  I know my m.2 slots have some BIOS settings that I've never seen before (I'm new to desktop m.2 storage).  My motherboard has a table attempting to explain which m.2 slot works in which way and how that impacts other SATA ports or bus speeds.

Some more googling: [https://forums.tweaktown.com/asrock/51478-asmedia-106x-sata-controller-0-90-ahci-mode-pcie-error.html](https://forums.tweaktown.com/asrock/51478-asmedia-106x-sata-controller-0-90-ahci-mode-pcie-error.html)  I found lots and lots of complaints against the Asmedia 106X SATA Controller.

---

### Post by crackers_altitude on 2019-01-24
it worked! Ubuntu 16.04.5 is up and running!

I apologize for the delay - it worked almost as soon as I saw the suggestion that the PCI card isn't working with this optical drive. I was delighted after simply unplugging the SATA cable from the PCI card, plugging it into a SATA-to-USB converter cable (low cost, in-hand), and in total plugging the optical drive into the exterior USB port. It was absolutely clear after Ubuntu started installing. I'm particularly excited to experience the SSD performance.

I'd like to add some after-the-fact details, if it isn't bad form, to help anyone who might come across this problem. It might take a while because I don't have a KVM switch.

Thank you TheFu! I learned a lot from this!

---

### Post by TheFu on 2019-01-24
Thanks for reporting back!  Helpful.

Most people do installs using flash media.  I haven't used optical since 2010, as an example.

Also, please mark the thread as "solved" using the thread tools button near the top. That helps the wider community.

---

### Post by crackers_altitude on 2019-01-24
my last question, if I may - it appears I have a 64 bit processor, so how do I know I have the 64-bit distribution? I've tried this before, and was confused, and now it appears I have 32-bit.

details FWIW : there's no real order to this, I'm just poking through - also can't be bothered to reformat with different fonts or anything. I just started noticing the OS can query BIOS information - there was a question about BIOS settings - so I haven't gotten into that yet...

inxi -Fxz:

System:    Host: (redacted by crackers_altitude) Kernel: 4.15.0-43-generic i686 (32 bit gcc: 5.4.0)
           Desktop: Unity 7.4.5 (Gtk 3.18.9-1ubuntu3.3) Distro: Ubuntu 16.04 xenial
Machine:   System: Acer product: Aspire X1300
           Mobo: Acer model: WMCP78M Bios: Phoenix v: R01-C0 date: 06/09/2010
CPU:       Dual core AMD Athlon 7450 (-MCP-) cache: 1024 KB
           flags: (lm nx pae sse sse2 sse3 sse4a svm) bmips: 9599
           clock speeds: max: 2400 MHz 1: 1200 MHz 2: 2400 MHz
Drives:    HDD Total Size: 500.1GB (1.2% used) ID-1: /dev/sda model: Samsung_SSD_860 size: 500.1GB
Partition: ID-1: / size: 457G used: 4.8G (2%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 720M used: 133M (20%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 1.02GB used: 0.00GB (0%) fs: swap dev: /dev/dm-3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present

selected lshw output:

        *-storage
             description: SATA controller
             product: ASM1062 Serial ATA Controller
             vendor: ASMedia Technology Inc.
             physical id: 0
             bus info: pci@0000:03:00.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: storage msi pm pciexpress ahci_1.0 bus_master cap_list rom
             configuration: driver=ahci latency=0
             resources: irq:25 ioport:ac00(size=8) ioport:a800(size=4) ioport:a400(size=8) ioport:a000(size=4) ioport:9c00(size=32) memory:fdcff000-fdcff1ff memory:fdc00000-fdc0ffff


lsmod | grep ahci
ahci                   36864  2
libahci                32768  1 ahci

---

### Post by #&amp;thj^% on 2019-01-24
> **crackers_altitude said:**
> my last question, if I may - it appears I have a 64 bit processor, so how do I know I have the 64-bit distribution?i

You can use:
```
getconf LONG_BIT
64  ## This is mine

```
Also beside the code yetimon_64 offers below my post, you can also use:
```
file /lib/systemd/systemd

```
Although it is a bit harder to read from a newer user's eye.
```
/lib/systemd/systemd: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=**_I removed this output,_** stripped
```

---

### Post by yetimon_64 on 2019-01-24
> **crackers_altitude said:**
> my last question, if I may - it appears I have a 64 bit processor, so how do I know I have the 64-bit distribution?....

Try the terminal command ...
```
dpkg --print-architecture
```

eg. from this install...
> ```
yetiman:~ $ dpkg --print-architecture
amd64
```
This shows I have the 64 bit OS installed.

**Edit**: ninja'd by 1fallen :-)

---

### Post by slickymaster on 2019-01-24
*Thread moved to **Hardware**.*

---

### Post by TheFu on 2019-01-24
```
System: Host: (redacted by crackers_altitude) Kernel: 4.15.0-43-generic i686 (32 bit gcc: 5.4.0)
```
That doesn't say amd64.  It says i686, a 32-bit kernel.

```
$ uname -m
x86_64
```
and
```
$ uname -m
i686
```

The **file** command shown above, should work for any binary program. There's nothing special about systemd is my point. So 
```
$ file /bin/b*
bunzip2:            ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=0875d3c6ee88e90ad268333441551baee6b17aa8, stripped
busybox:            ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), statically linked, for GNU/Linux 2.6.32, BuildID[sha1]=5ce436575b628a8f54c2a346cc6e758d494c33fe, stripped
bzcat:              ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=0875d3c6ee88e90ad268333441551baee6b17aa8, stripped
...
```

BTW, the **-z **option strips any machine specific output from inxi.

Glad you got what you needed. I'm out.

---

### Post by crackers_altitude on 2019-01-24
just one last word of thanks : thanks!

---

