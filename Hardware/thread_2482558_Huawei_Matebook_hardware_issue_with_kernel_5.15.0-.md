---
title: "Huawei Matebook hardware issue with kernel 5.15.0-1025-oracle"
date: 2023-01-03
forum: Hardware
---

### Post by BJC_001 on 2023-01-03
I have a Huawei Matebook that has a hardware problem with kernel *5.15.0-1025-oracle* but isn't evident with *5.15.0-56-lowlatency*. When booting into the *1025-oracle* kernel, the touchpad and wireless wi-fi don't work and the screen resolution is 1280x1024 rather than the expected 2160x1440. Booting into the *56-lowlatency* kernel, everything works as expected. I believe the problem has been evident since the *1025-oracle* version update was installed. Since then, every restart has required the selection of the special boot options and manually selecting the *56-lowlatency* version.

As some background, I've many years experience of Windows as a user and developer and also do hard embedded firmware development too. However, my Ubuntu (Linux) experience is only as a user. Consequently, I'm struggling to debug the issue. I'm looking for some help to fault find or resolve the issue.

I've tried booting from each kernel version and doing some things.

I ran the *lsusb -t* command, with the following results in the working *56-lowlatency* kernel:
```

/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 10000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 4: Dev 2, If 1, Class=Video, Driver=uvcvideo, 480M
    |__ Port 4: Dev 2, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 10: Dev 3, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 10: Dev 3, If 1, Class=Wireless, Driver=btusb, 12M

```

The same command in the non-working 1025-oracle kernel has the following output:
```

/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 10000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 4: Dev 2, If 1, Class=Video, Driver=, 480M
    |__ Port 4: Dev 2, If 0, Class=Video, Driver=, 480M
    |__ Port 10: Dev 3, If 0, Class=Wireless, Driver=, 12M
    |__ Port 10: Dev 3, If 1, Class=Wireless, Driver=, 12M

```

I note that the driver isn't listed for some of those devices. That doesn't seem right.

I also captured the *dmesg* output for each kernel version. Obviously, there's much that's the same, or similar. I dare not post it all here but I suspect the issues are around the point that the xHCI Controller is detected.

This is the extract from the working *56-lowlatency* version.
```

...
[    0.982208] Run /init as init process
[    0.982209]   with arguments:
[    0.982209]     /init
[    0.982210]     splash
[    0.982211]   with environment:
[    0.982211]     HOME=/
[    0.982211]     TERM=linux
[    0.982212]     BOOT_IMAGE=/boot/vmlinuz-5.15.0-56-lowlatency
[    1.055454] hid: raw HID events driver (C) Jiri Kosina
[    1.055747] wmi_bus wmi_bus-PNP0C14:01: WQ data block query control method not found
[    1.055764] wmi_bus wmi_bus-PNP0C14:01: WQ data block query control method not found
[    1.055773] wmi_bus wmi_bus-PNP0C14:01: WQ data block query control method not found
[    1.055781] wmi_bus wmi_bus-PNP0C14:01: WQ data block query control method not found
[    1.056316] acpi PNP0C14:04: duplicate WMI GUID 05901221-D566-11D1-B2F0-00A0C9062910 (first instance was on PNP0C14:03)
[    1.056371] acpi PNP0C14:05: duplicate WMI GUID 05901221-D566-11D1-B2F0-00A0C9062910 (first instance was on PNP0C14:03)
[    1.063972] ahci 0000:00:17.0: version 3.0
[    1.064355] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 1 ports 6 Gbps 0x4 impl SATA mode
[    1.064359] ahci 0000:00:17.0: flags: 64bit ncq sntf pm clo only pio slum part deso sadm sds apst 
[    1.064547] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.064554] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.066085] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x110 quirks 0x0000000000009810
[    1.067785] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.067789] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.067793] xhci_hcd 0000:00:14.0: Host supports USB 3.1 Enhanced SuperSpeed
[    1.067825] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[    1.067827] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.067829] usb usb1: Product: xHCI Host Controller
[    1.067830] usb usb1: Manufacturer: Linux 5.15.0-56-lowlatency xhci-hcd
[    1.067831] usb usb1: SerialNumber: 0000:00:14.0
[    1.068007] hub 1-0:1.0: USB hub found
[    1.068025] hub 1-0:1.0: 12 ports detected
[    1.068032] scsi host0: ahci
[    1.068190] scsi host1: ahci
[    1.068330] scsi host2: ahci
[    1.068423] ata1: DUMMY
[    1.068425] ata2: DUMMY
[    1.068431] ata3: SATA max UDMA/133 abar m2048@0xb42af000 port 0xb42af200 irq 124
[    1.069534] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15
[    1.069539] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.069541] usb usb2: Product: xHCI Host Controller
[    1.069543] usb usb2: Manufacturer: Linux 5.15.0-56-lowlatency xhci-hcd
[    1.069544] usb usb2: SerialNumber: 0000:00:14.0
[    1.069693] hub 2-0:1.0: USB hub found
[    1.069705] hub 2-0:1.0: 6 ports detected
[    1.089028] intel-lpss 0000:00:15.0: enabling device (0004 -> 0006)
[    1.089483] idma64 idma64.0: Found Intel integrated DMA 64-bit
[    1.109244] intel-lpss 0000:00:15.1: enabling device (0004 -> 0006)
[    1.109479] idma64 idma64.1: Found Intel integrated DMA 64-bit
[    1.125049] intel-lpss 0000:00:19.0: enabling device (0004 -> 0006)
[    1.142047] intel-lpss 0000:00:1e.0: enabling device (0004 -> 0006)
[    1.142457] idma64 idma64.3: Found Intel integrated DMA 64-bit
[    1.155324] intel-lpss 0000:00:1e.3: enabling device (0004 -> 0006)
[    1.155850] idma64 idma64.4: Found Intel integrated DMA 64-bit
[    1.376440] ata3: SATA link down (SStatus 4 SControl 300)
[    1.382123] nvme 0000:02:00.0: platform quirk: setting simple suspend
[    1.382246] nvme nvme0: pci function 0000:02:00.0
[    1.383304] i801_smbus 0000:00:1f.4: SPD Write Disable is set
[    1.383383] i801_smbus 0000:00:1f.4: SMBus using PCI interrupt
[    1.387694] i2c i2c-3: 2/2 memory slots populated (from DMI)
[    1.388032] usb 1-4: new high-speed USB device number 2 using xhci_hcd
[    1.388685] input: ELAN962C:00 04F3:3109 Mouse as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN962C:00/0018:04F3:3109.0001/input/input4
[    1.388866] input: ELAN962C:00 04F3:3109 Touchpad as /devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-ELAN962C:00/0018:04F3:3109.0001/input/input6
[    1.389026] hid-generic 0018:04F3:3109.0001: input,hidraw0: I2C HID v1.00 Mouse [ELAN962C:00 04F3:3109] on i2c-ELAN962C:00
[    1.390003] input: ELAN224A:00 04F3:2841 Touchscreen as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-ELAN224A:00/0018:04F3:2841.0002/input/input7
[    1.390272] input: ELAN224A:00 04F3:2841 as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-ELAN224A:00/0018:04F3:2841.0002/input/input8
[    1.390372] input: ELAN224A:00 04F3:2841 as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-ELAN224A:00/0018:04F3:2841.0002/input/input9
[    1.390463] input: ELAN224A:00 04F3:2841 as /devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-1/i2c-ELAN224A:00/0018:04F3:2841.0002/input/input10
[    1.390603] hid-generic 0018:04F3:2841.0002: input,hidraw1: I2C HID v1.00 Device [ELAN224A:00 04F3:2841] on i2c-ELAN224A:00
[    1.391854] nvme nvme0: 8/0/0 default/read/poll queues
[    1.395646]  nvme0n1: p1 p2 p3 p4 p5 p6 p7
[    1.544073] usb 1-4: New USB device found, idVendor=13d3, idProduct=56c6, bcdDevice=18.07
[    1.544083] usb 1-4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.544086] usb 1-4: Product: HD Camera
[    1.544089] usb 1-4: Manufacturer: Azurewave
[    1.544092] usb 1-4: SerialNumber: 0x0001
[    1.594114] i801_smbus 0000:00:1f.4: Transaction timeout
[    1.594127] fbcon: Taking over console
[    1.594284] Console: switching to colour frame buffer device 160x64
[    1.596136] i801_smbus 0000:00:1f.4: Failed terminating the transaction
[    1.596227] i801_smbus 0000:00:1f.4: SMBus is busy, can't use it!
[    1.660125] usb 1-10: new full-speed USB device number 3 using xhci_hcd
[    1.698130] tsc: Refined TSC clocksource calibration: 2304.001 MHz
[    1.698144] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2135f8984a8, max_idle_ns: 440795232764 ns
[    1.698213] clocksource: Switched to clocksource tsc
[    1.787877] usb 1-10: New USB device found, idVendor=8087, idProduct=0aaa, bcdDevice= 0.02
[    1.787886] usb 1-10: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.873273] EXT4-fs (nvme0n1p4): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
[    1.961094] systemd[1]: Inserted module 'autofs4'
[    2.033809] systemd[1]: systemd 249.11-0ubuntu3.6 running in system mode (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)
[    2.045315] systemd[1]: Detected architecture x86-64.
...

```

This is the extract from the non-working *1025-oracle* version.
```

...
[    0.881792] Run /init as init process
[    0.881794]   with arguments:
[    0.881796]     /init
[    0.881797]     splash
[    0.881799]   with environment:
[    0.881800]     HOME=/
[    0.881801]     TERM=linux
[    0.881802]     BOOT_IMAGE=/boot/vmlinuz-5.15.0-1025-oracle
[    0.888184] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.996321] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.996329] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.997035] ahci 0000:00:17.0: version 3.0
[    0.997319] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 1 ports 6 Gbps 0x4 impl SATA mode
[    0.997323] ahci 0000:00:17.0: flags: 64bit ncq sntf pm clo only pio slum part deso sadm sds apst 
[    0.997411] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x110 quirks 0x0000000000009810
[    0.997485] nvme 0000:02:00.0: platform quirk: setting simple suspend
[    0.997565] nvme nvme0: pci function 0000:02:00.0
[    0.997845] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.997850] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.997853] xhci_hcd 0000:00:14.0: Host supports USB 3.1 Enhanced SuperSpeed
[    0.997899] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.15
[    0.997902] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.997904] usb usb1: Product: xHCI Host Controller
[    0.997906] usb usb1: Manufacturer: Linux 5.15.0-1025-oracle xhci-hcd
[    0.997907] usb usb1: SerialNumber: 0000:00:14.0
[    0.998146] hub 1-0:1.0: USB hub found
[    0.998168] hub 1-0:1.0: 12 ports detected
[    0.998174] scsi host0: ahci
[    0.998360] scsi host1: ahci
[    0.999294] scsi host2: ahci
[    0.999364] ata1: DUMMY
[    0.999367] ata2: DUMMY
[    0.999372] ata3: SATA max UDMA/133 abar m2048@0xb42af000 port 0xb42af200 irq 124
[    1.000176] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.15
[    1.000181] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.000182] usb usb2: Product: xHCI Host Controller
[    1.000184] usb usb2: Manufacturer: Linux 5.15.0-1025-oracle xhci-hcd
[    1.000186] usb usb2: SerialNumber: 0000:00:14.0
[    1.000311] hub 2-0:1.0: USB hub found
[    1.000329] hub 2-0:1.0: 6 ports detected
[    1.006378] nvme nvme0: 8/0/0 default/read/poll queues
[    1.009017]  nvme0n1: p1 p2 p3 p4 p5 p6 p7
[    1.316190] ata3: SATA link down (SStatus 4 SControl 300)
[    1.336581] usb 1-4: new high-speed USB device number 2 using xhci_hcd
[    1.513065] usb 1-4: New USB device found, idVendor=13d3, idProduct=56c6, bcdDevice=18.07
[    1.513077] usb 1-4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.513082] usb 1-4: Product: HD Camera
[    1.513086] usb 1-4: Manufacturer: Azurewave
[    1.513090] usb 1-4: SerialNumber: 0x0001
[    1.644576] usb 1-10: new full-speed USB device number 3 using xhci_hcd
[    1.664584] tsc: Refined TSC clocksource calibration: 2304.003 MHz
[    1.664603] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2135fabfc56, max_idle_ns: 440795260950 ns
[    1.664705] clocksource: Switched to clocksource tsc
[    1.794718] usb 1-10: New USB device found, idVendor=8087, idProduct=0aaa, bcdDevice= 0.02
[    1.794731] usb 1-10: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.880311] fbcon: Taking over console
[    1.880446] Console: switching to colour frame buffer device 160x64
[    1.894015] EXT4-fs (nvme0n1p4): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
[    1.995374] systemd[1]: Inserted module 'autofs4'
[    2.112834] systemd[1]: systemd 249.11-0ubuntu3.6 running in system mode (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)
[    2.133021] systemd[1]: Detected architecture x86-64.
...

```

I've also attached the output from the system-info script, as run from each kernel version.

Any suggestions as to what might be wrong, how to fault find further, or ideally how to resolve the issue?

Thanks.

---

### Post by BJC_001 on 2023-01-08
Having just applied a software update, I can confirm that kernel *v5.15.0-57* is working as *5.15.0-56* had been. However, *5.15.0-1025-oracle* continues to fail, not supporting the touchpad or wireless adapter, and the screen resolution remains limited.

I'm open to any suggestions as to how I might investigate this further, or resolve the issue. Basically, I'm stuck trying to figure this out.

---

### Post by BJC_001 on 2023-01-16
OK, I've made a little progress on my own. Perhaps other might benefit from what I've found. However, any help would be appreciated.

Where the kernel version reports as "v5.15.0-1025-oracle, the "oracle" part denotes the kernel flavour. There are a list of kernel flavours ([https://wiki.ubuntu.com/Kernel/Dev/Flavours](https://wiki.ubuntu.com/Kernel/Dev/Flavours)) but oracle isn't in the list. The answer to another query ([https://askubuntu.com/questions/1170659/linux-kernel-flavours-in-modern-releases](https://askubuntu.com/questions/1170659/linux-kernel-flavours-in-modern-releases)) lists some other flavours and that does include oracle.

Based on that, it seems that oracle is a flavour that has been created for Oracle systems - it isn't some codename for something else. That's helpful because I don't believe that there's any reason that my system should be using that kernel.

My solution was to edit the */boot/grub/grub.cfg* file to replace the initial *menuentry* item from the oracle flavour to the generic flavour. That seemed to work but the change seemed to get overwritten at some point. I'd guess that was a software update for grub.

It'd be helpful if there were some way to determine the dependencies that required the oracle kernel flavour.

---

### Post by ajgreeny on 2023-01-16
If the default kernels 5.15.0-56 and -57 work why do you use the 5.15.0-1025-oracle version which is giving you the problem?

There must be a reason for you installing that version and persisting with its use but I'm not sure what that is. Why not simply boot into the 5.15.0-57 kernel and then delete the -1025-oracle version?

---

### Post by BJC_001 on 2023-01-17
Hi,

Thanks for posting.

Unfortunately, it seems that I haven't been as clear as I'd hoped. Sorry for that.

I didn't explicitly or intentionally install the *oracle* flavour of the kernel. I don't know what dependency brought it in. In fact, I didn't even know about the kernel flavours until I worked through some of the things described above.

I'm not really choosing to persist with the *oracle* kernel flavour either. I've tried to disable it as best I can, removing it from the grub menu. That only seems to have been partially successful, since I believe that it has come back at least once. I'd have tried to remove the *oracle* kernel completely, but I'm hesitant to do that with so little understanding of why it's there. I also have no knowledge of potential side-effects of removing it explicitly. However, I agree that removal of the undesired kernel flavour is beginning to look like the best solution. It's only during this process that I realised that the *generic* flavour is still being updated through the normal update mechanism, so that's encouraging that the system might be able to use that as normal, if I can configure things to make the generic kernel the default again.

Originally, this seemed, to me, to be a hardware support issue with the latest kernel. I don't think it was unreasonable to assume that a version with "1025" was more recent than one with "56", especially as my system was defaulting to the version with a higher number. I appreciate that it now feels more like a software configuration issue that's inadvertently pulled in a kernel flavour that's not required. I'm sorry if I mis-assessed the issue.

I've tried to post the correct information to get some help. I had hoped to get some advice on the best way forward, as I'm struggling. I don't believe that I'm incompetent. However, I am inexperienced in this area but I'm trying my best. I also hoped that sharing on this forum might not only help me but others too.

If anyone can suggest steps to identify how I might have pulled in the unexpected kernel flavour, or how it should best be removed from the system, that would be great.

Thanks.

---

### Post by #&amp;thj^% on 2023-01-17
> **BJC_001 said:**
> 

If anyone can suggest steps to identify how I might have pulled in the unexpected kernel flavour, or how it should best be removed from the system, that would be great.

Thanks.
I have no Idea how it arrived on your system, I'll try to help you remove it, but first I need to see this:
```
apt list --installed | grep linux-image

```

---

### Post by tea for one on 2023-01-17
> **1fallen said:**
> I have no Idea how it arrived on your system, I'll try to help you remove it, but first I need to see this:

I, also, have no idea how an unexpected kernel arrived but, as always with Ubuntu, there is more than one way to skin the furry feline.
Here is my method.
First , list my installed kernels
```
edited@edited:~$ ls /boot | grep vmlinuz-
vmlinuz-5.15.0-56-generic [COLOR="#0000FF"]to be removed[/COLOR]
vmlinuz-5.15.0-57-generic
vmlinuz-5.15.0-58-generic
edited@edited:~$
```
As long as I am not booted into an unwanted kernel, I can remove it with
```
sudo apt remove *5.15.0-56*
```
```
sudo apt remove *your oracle kernel*
```
Grub will be re-written automagically.

Before playing around with kernels, make sure that you have data backups.

---

### Post by ajgreeny on 2023-01-18
If that oracle kernel is a dependency of anything already installed,  the ***sudo apt remove*** command will tell you and ask for permission to continue so it should not cause any problems unless you ignore those removal.

---

### Post by #&amp;thj^% on 2023-01-18
> **ajgreeny said:**
> If that oracle kernel is a dependency of anything already installed,  the ***sudo apt remove*** command will tell you and ask for permission to continue so it should not cause any problems unless you ignore those removal.

+1 Good addition to ease any fears the OP has, IE:
```
sudo apt remove *linux-image-6.1.0-1-amd64*
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'linux-image-6.1.0-1-amd64-unsigned' for glob '*linux-image-6.1.0-1-amd64*'
Note, selecting 'linux-image-6.1.0-1-amd64' for glob '*linux-image-6.1.0-1-amd64*'
Note, selecting 'linux-image-6.1.0-1-amd64-dbg' for glob '*linux-image-6.1.0-1-amd64*'
Package 'linux-image-6.1.0-1-amd64-unsigned' is not installed, so not removed
Package 'linux-image-6.1.0-1-amd64' is not installed, so not removed
The following packages will be REMOVED:
  linux-image-6.1.0-1-amd64-dbg linux-image-amd64-dbg
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 5,764 MB disk space will be freed.
Do you want to continue? [Y/n] 

```
Now I just have:
```
ls /boot | grep vmlinuz-
vmlinuz-6.0.0-6-amd64
vmlinuz-6.2.0-060200rc4-generic


me on Wed Jan 18 at 11:06 AM in ~ branch: (HEAD) 
>> apt list --installed | grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-6.0.0-6-amd64/now 6.0.12-1 amd64 [installed,local]
linux-image-unsigned-6.2.0-060200rc4-generic/now 6.2.0-060200rc4.202301151633 amd64 [installed,local]

```
easy peasy :)

---

### Post by BJC_001 on 2023-01-18
Hi,

Thanks for the assistance. Most helpful.

Using the first suggested command ([FONT=courier new]apt list --installed | grep linux-image[/FONT]), the output is as follows:```
[FONT=courier new]WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-5.15.0-1025-oracle/jammy-updates,jammy-security,now 5.15.0-1025.31 amd64 [installed,automatic]
linux-image-5.15.0-58-generic/jammy-updates,jammy-security,now 5.15.0-58.64 amd64 [installed,automatic]
linux-image-generic/jammy-updates,jammy-security,now 5.15.0.58.56 amd64 [installed,automatic][/FONT]
```


Using the second suggested command ([FONT=courier new]ls /boot | grep vmlinuz-[/FONT]), the output is as follows:
```
vmlinuz-5.15.0-1025-oracle
vmlinuz-5.15.0-58-generic
```

So, the methods agree, as would be expected.

I've then gone on to revert the edits I made to the grub menu and then run the following command to remove the unwanted kernel flavour:
```
sudo apt remove linux-image-5.15.0-1025-oracle
```

Now, the output of that command was NOT what I was expecting, as follows:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  linux-image-unsigned-5.15.0-1025-oracle
Suggested packages:
  fdutils linux-oracle-doc-5.15.0 | linux-oracle-source-5.15.0
  linux-oracle-tools linux-headers-5.15.0-1025-oracle
The following packages will be REMOVED
  linux-image-5.15.0-1025-oracle linux-signatures-nvidia-5.15.0-1025-oracle
The following NEW packages will be installed
  linux-image-unsigned-5.15.0-1025-oracle
0 to upgrade, 1 to newly install, 2 to remove and 9 not to upgrade.
Need to get 11.7 MB of archives.
After this operation, 171 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
```

I opted to abort that operation because it seems to be suggesting that it's going to INSTALL and unsigned version instead. That doesn't sound like a good idea.

Have I managed to mess that up?

---

### Post by #&amp;thj^% on 2023-01-18
EDIT: I saw this   (linux-signatures-nvidia-5.15.0-1025-oracle) this has potential bad side effect.
First show me this:
```
apt policy linux-signatures-nvidia-5.15.0-1025
```
Please try this, copy and paste:
```
 sudo apt remove *linux-image-5.15.0-1025-oracle*
```
NOTE>>>"**" is needed, if you want us to look at first please feel free to do so.

---

### Post by BJC_001 on 2023-01-19
Hi,

OK, I see what I did wrong. I didn't appreciate that the wildcards were part of the command.

I ran the [slightly amended] command ([FONT=courier new]apt policy linux-signatures-nvidia-5.15.0-1025*[/FONT]), with the following results:
```
linux-signatures-nvidia-5.15.0-1025-oracle:
  Installed: 5.15.0-1025.31+1
  Candidate: 5.15.0-1025.31+1
  Version table:
 *** 5.15.0-1025.31+1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
        100 /var/lib/dpkg/status
linux-signatures-nvidia-5.15.0-1025-gcp:
  Installed: (none)
  Candidate: 5.15.0-1025.32+1
  Version table:
     5.15.0-1025.32+1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
```

The response to the second command ([FONT=courier new]sudo apt remove *linux-image-5.15.0-1025-oracle*[/FONT]) is as follows:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note: selecting 'linux-image-5.15.0-1025-oracle' for glob '*linux-image-5.15.0-1025-oracle*'
The following additional packages will be installed:
  linux-image-unsigned-5.15.0-1025-oracle
Suggested packages:
  fdutils linux-oracle-doc-5.15.0 | linux-oracle-source-5.15.0 linux-oracle-tools linux-headers-5.15.0-1025-oracle
The following packages will be REMOVED
  linux-image-5.15.0-1025-oracle linux-signatures-nvidia-5.15.0-1025-oracle
The following NEW packages will be installed
  linux-image-unsigned-5.15.0-1025-oracle
0 to upgrade, 1 to newly install, 2 to remove and 14 not to upgrade.
Need to get 11.7 MB of archives.
After this operation, 171 kB of additional disk space will be used.
Do you want to continue? [Y/n]
```

At this point, I opted for no, and did not proceed, because it's still intending to install another kernel.

---

### Post by tea for one on 2023-01-19
In post 2, you mentioned that you had two working kernels
> I can confirm that kernel v5.15.0-57 is working as 5.15.0-56 had been.

In post 10, you have two kernels, one of which is the troublesome oracle version
```
vmlinuz-5.15.0-1025-oracle
vmlinuz-5.15.0-58-generic
```

What happened to 5.15.0-57 and 5.15.0-56?

I'm going to guess now because it is a bit baffling.
Perhaps apt always wants to see two kernels, (i.e. only having one kernel is considered insecure)?

My latest kernel is the same as yours 5.15.0-58 so, if you are willing to experiment a little:-
Install a previous regular kernel
```
sudo apt install linux-headers-5.15.0-57 linux-headers-5.15.0-57-generic linux-image-5.15.0-57-generic linux-modules-5.15.0-57-generic linux-modules-extra-5.15.0-57-generic
```
Then, see if you can remove the oracle version?

Make sure that you have data backups before proceeding.

Lastly, I notice that you have Nvidia graphics and the oracle kernel package has nvidia in the package name.
I don't have Nvidia in my system so I really do not know if your graphics will be affected.

---

### Post by tea for one on 2023-01-19
This is a similar thread with particular reference to Nvidia.
[https://ubuntuforums.org/showthread.php?t=2473057](https://ubuntuforums.org/showthread.php?t=2473057)
Any help?

---

### Post by #&amp;thj^% on 2023-01-19
another thread is going on today, closley related to this thread....but not Identical.
lets see if any added new information, helps here first.
I also think the link tea for one points too #14 is worth a look.

---

### Post by ajgreeny on 2023-01-19
@ 1fallen

[https://ubuntuforums.org/showthread.php?t=2483064](https://ubuntuforums.org/showthread.php?t=2483064)
Is this the thread you mean which I have just seen and posted in, offering a link back to this thread.

Seems to be a growing problem!

---

### Post by ajgreeny on 2023-01-19
@ 1fallen

[https://ubuntuforums.org/showthread.php?t=2483064](https://ubuntuforums.org/showthread.php?t=2483064)
Is this the thread you mean which I have just seen and posted in, offering a link back to this thread.

Seems to be a growing problem!

---

### Post by BJC_001 on 2023-01-19
Hi,

The change to the generic kernel version is simply that some updates have been applied since this process started. After the first update - to 57 - I thought it might be helpful to confirm that the symptoms were unchanged. I didn't think it important to repeat that when it was updated again - to 58. I appreciate that I'd need to translate any instructions should anyone explicitly use one of the earlier versions. That much, I can handle. However, I appreciate that it might have been helpful to share. Sorry.

That link does seem to be exactly the same thing I've been experiencing. My original research hinted at a link to nVidia drivers but I didn't find anything so definite. Then again, I've learnt quite a bit more about kernel labelling since then. :-)

I appreciate the suggestion to explicitly reinstall the generic 57 kernel but I'm not sure that'll help. The only way I can have a functional system is to boot into the generic-58 kernel, so that line seems good. I'm also concerned that manual installations will mess up the normal update automation. As I understand it, the apt process makes different decisions when things are manually installed (and presumably removed too).

I think there's some mileage to be had with changing the nVidia drivers. I appreciate that's not somethiNg you can help with, if your system doesn't use them.

The system choice is currently "Using NVIDIA driver metapackage from nvidia-driver-515 (proprietary)". The Software & Updates application reports another option, listed as "Using NVIDIA driver metapackage from nvidia-driver-525 (proprietary, tested)". I thought I'd select that as a first step, and then perhaps an earlier version. I applied the change for the first option and it started well, with progress updating quickly. Unfortunately, it's now been running for a couple of hours and still hasn't completed. I'm patient but at some point soon it looks like I'll need to cancel.

Thanks for your help so far.

---

### Post by #&amp;thj^% on 2023-01-19
[s]@ BJC_001, Important question, do you have the nvidia driver installed.[/s]
I just saw your edit, i now think, I know why you keep getting the option to re-install the bad kernel.
Are you trying to un-install it while your booted to it?

---

### Post by #&amp;thj^% on 2023-01-19
> **ajgreeny said:**
> @ 1fallen

[https://ubuntuforums.org/showthread.php?t=2483064](https://ubuntuforums.org/showthread.php?t=2483064)
Is this the thread you mean which I have just seen and posted in, offering a link back to this thread.

Seems to be a growing problem!

The very one...
All looker's bare in mind I have high standards, this sometimes invokes a knee jerk reaction from me. (Apologies for my passion)

---

### Post by BJC_001 on 2023-01-19
OK, after 3 hours of waiting for the change of nVidia driver to complete, I activated the Cancel button. That didn't seem to do anything either. After a few minutes of nothing happening, I restarted. During the boot, I manually selected the 58-generic kernel. After the restart, the Software & Updates application reports reports that the active driver has changed to "Using NVIDIA driver metapackage from nvidia-driver-525 (proprietary, tested)".

I then ran the earlier suggest command to list the installed kernels ([FONT=courier new]apt list --installed | grep linux-image[/FONT]), and it reported the following:
```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-5.15.0-1025-oracle/jammy-updates,jammy-security,now 5.15.0-1025.31 amd64 [installed,automatic]
linux-image-5.15.0-58-generic/jammy-updates,jammy-security,now 5.15.0-58.64 amd64 [installed,automatic]
linux-image-generic/jammy-updates,jammy-security,now 5.15.0.58.56 amd64 [installed,automatic]
```

That's the same list as before, so the change of nVidia driver has changed the installed kernels.

I then restarted and allowed it to start normally (i.e. not manually selecting a different boot menu option for a different kernel). That exhibited the same symptoms that started this whole issue.

Perhaps the next thing to try os one of the earlier nVidia drivers (e.g. "NVIDIA driver metapackage from nvidia-driver-515 (proprietary" or "NVIDIA driver metapackage from nvidia-driver-470 (proprietary")? That'll need to wait for tomorrow.

---

### Post by #&amp;thj^% on 2023-01-19
Nothing you do from that kernel will work, it's just broken...
Boot with this kernel:
```
linux-image-5.15.0-58-generic
```
Now remove the oracle kernel.
we will work on the rest when you return.

---

### Post by BJC_001 on 2023-01-20
> **1fallen said:**
> [s]@ BJC_001, Important question, do you have the nvidia driver installed.[/s]
I just saw your edit, i now think, I know why you keep getting the option to re-install the bad kernel.
Are you trying to un-install it while your booted to it?
Sorry I missed this question.

No, I tried to delete the oracle kernel while booted into the generic kernel. The system operation is massively limited when booted into the oracle kernel - no wireless, no mouse, limited screen resolution. If I boot into it, about all I do is switch to a separate virtual TTY and use the command line to login and reboot, so that I can boot into a functional kernel.

---

### Post by #&amp;thj^% on 2023-01-20
Thanks for the update, we had a lot going on yesterday so post's were easily missed.
This is a dry run only again, I need to see what has the strangle hold on your system:
```
sudo apt remove --autoremove nvidia* -s

```
again no changes will be made, and if possible I would like to see the whole return from that command.

---

### Post by BJC_001 on 2023-01-20
OK, the response to requested command ([FONT=courier new]sudo apt remove --autoremove nvidia* -s[/FONT]) is as follows:
```
Reading package lists...
Building dependency tree...
Reading state information...
Package 'nvidia-egl-wayland-common' is not installed, so not removed
Package 'nvidia-390' is not installed, so not removed
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-driver-410' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-legacy-390xx-opencl-icd' is not installed, so not removed
Package 'nvidia-legacy-390xx-smi' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-compute-utils-418' is not installed, so not removed
Package 'nvidia-compute-utils-418-server' is not installed, so not removed
Package 'nvidia-compute-utils-430' is not installed, so not removed
Package 'nvidia-compute-utils-435' is not installed, so not removed
Package 'nvidia-compute-utils-440' is not installed, so not removed
Package 'nvidia-compute-utils-450' is not installed, so not removed
Package 'nvidia-compute-utils-455' is not installed, so not removed
Package 'nvidia-dkms-418' is not installed, so not removed
Package 'nvidia-dkms-418-server' is not installed, so not removed
Package 'nvidia-dkms-430' is not installed, so not removed
Package 'nvidia-dkms-435' is not installed, so not removed
Package 'nvidia-dkms-440' is not installed, so not removed
Package 'nvidia-dkms-450' is not installed, so not removed
Package 'nvidia-dkms-455' is not installed, so not removed
Package 'nvidia-driver-418' is not installed, so not removed
Package 'nvidia-driver-418-server' is not installed, so not removed
Package 'nvidia-driver-430' is not installed, so not removed
Package 'nvidia-driver-435' is not installed, so not removed
Package 'nvidia-driver-440' is not installed, so not removed
Package 'nvidia-driver-450' is not installed, so not removed
Package 'nvidia-driver-455' is not installed, so not removed
Package 'nvidia-headless-418' is not installed, so not removed
Package 'nvidia-headless-418-server' is not installed, so not removed
Package 'nvidia-headless-430' is not installed, so not removed
Package 'nvidia-headless-435' is not installed, so not removed
Package 'nvidia-headless-440' is not installed, so not removed
Package 'nvidia-headless-450' is not installed, so not removed
Package 'nvidia-headless-455' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418' is not installed, so not removed
Package 'nvidia-headless-no-dkms-418-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-430' is not installed, so not removed
Package 'nvidia-headless-no-dkms-435' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450' is not installed, so not removed
Package 'nvidia-headless-no-dkms-455' is not installed, so not removed
Package 'nvidia-kernel-common-418' is not installed, so not removed
Package 'nvidia-kernel-common-418-server' is not installed, so not removed
Package 'nvidia-kernel-common-430' is not installed, so not removed
Package 'nvidia-kernel-common-435' is not installed, so not removed
Package 'nvidia-kernel-common-440' is not installed, so not removed
Package 'nvidia-kernel-common-450' is not installed, so not removed
Package 'nvidia-kernel-common-455' is not installed, so not removed
Package 'nvidia-kernel-source-418' is not installed, so not removed
Package 'nvidia-kernel-source-418-server' is not installed, so not removed
Package 'nvidia-kernel-source-430' is not installed, so not removed
Package 'nvidia-kernel-source-435' is not installed, so not removed
Package 'nvidia-kernel-source-440' is not installed, so not removed
Package 'nvidia-kernel-source-450' is not installed, so not removed
Package 'nvidia-kernel-source-455' is not installed, so not removed
Package 'nvidia-utils-418' is not installed, so not removed
Package 'nvidia-utils-418-server' is not installed, so not removed
Package 'nvidia-utils-430' is not installed, so not removed
Package 'nvidia-utils-435' is not installed, so not removed
Package 'nvidia-utils-440' is not installed, so not removed
Package 'nvidia-utils-450' is not installed, so not removed
Package 'nvidia-utils-455' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-cuda-toolkit-doc' is not installed, so not removed
Package 'nvidia-cuda-toolkit-gcc' is not installed, so not removed
Package 'nvidia-cudnn' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-primus-vk-common' is not installed, so not removed
Package 'nvidia-primus-vk-wrapper' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-compute-utils-440-server' is not installed, so not removed
Package 'nvidia-compute-utils-450-server' is not installed, so not removed
Package 'nvidia-compute-utils-460' is not installed, so not removed
Package 'nvidia-compute-utils-460-server' is not installed, so not removed
Package 'nvidia-compute-utils-465' is not installed, so not removed
Package 'nvidia-compute-utils-470' is not installed, so not removed
Package 'nvidia-compute-utils-470-server' is not installed, so not removed
Package 'nvidia-compute-utils-495' is not installed, so not removed
Package 'nvidia-compute-utils-510' is not installed, so not removed
Package 'nvidia-compute-utils-510-server' is not installed, so not removed
Package 'nvidia-compute-utils-515' is not installed, so not removed
Package 'nvidia-compute-utils-515-server' is not installed, so not removed
Package 'nvidia-compute-utils-520' is not installed, so not removed
Package 'nvidia-compute-utils-525-server' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-dkms-440-server' is not installed, so not removed
Package 'nvidia-dkms-450-server' is not installed, so not removed
Package 'nvidia-dkms-460' is not installed, so not removed
Package 'nvidia-dkms-460-server' is not installed, so not removed
Package 'nvidia-dkms-465' is not installed, so not removed
Package 'nvidia-dkms-470' is not installed, so not removed
Package 'nvidia-dkms-470-server' is not installed, so not removed
Package 'nvidia-dkms-495' is not installed, so not removed
Package 'nvidia-dkms-510' is not installed, so not removed
Package 'nvidia-dkms-510-server' is not installed, so not removed
Package 'nvidia-dkms-515' is not installed, so not removed
Package 'nvidia-dkms-515-open' is not installed, so not removed
Package 'nvidia-dkms-515-server' is not installed, so not removed
Package 'nvidia-dkms-520' is not installed, so not removed
Package 'nvidia-dkms-520-open' is not installed, so not removed
Package 'nvidia-dkms-525-open' is not installed, so not removed
Package 'nvidia-dkms-525-server' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-driver-440-server' is not installed, so not removed
Package 'nvidia-driver-450-server' is not installed, so not removed
Package 'nvidia-driver-460' is not installed, so not removed
Package 'nvidia-driver-460-server' is not installed, so not removed
Package 'nvidia-driver-465' is not installed, so not removed
Package 'nvidia-driver-470' is not installed, so not removed
Package 'nvidia-driver-470-server' is not installed, so not removed
Package 'nvidia-driver-495' is not installed, so not removed
Package 'nvidia-driver-510' is not installed, so not removed
Package 'nvidia-driver-510-server' is not installed, so not removed
Package 'nvidia-driver-515' is not installed, so not removed
Package 'nvidia-driver-515-open' is not installed, so not removed
Package 'nvidia-driver-515-server' is not installed, so not removed
Package 'nvidia-driver-520' is not installed, so not removed
Package 'nvidia-driver-520-open' is not installed, so not removed
Package 'nvidia-driver-525-open' is not installed, so not removed
Package 'nvidia-driver-525-server' is not installed, so not removed
Package 'nvidia-fabricmanager-515' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-515' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-440-server' is not installed, so not removed
Package 'nvidia-headless-450-server' is not installed, so not removed
Package 'nvidia-headless-460' is not installed, so not removed
Package 'nvidia-headless-460-server' is not installed, so not removed
Package 'nvidia-headless-465' is not installed, so not removed
Package 'nvidia-headless-470' is not installed, so not removed
Package 'nvidia-headless-470-server' is not installed, so not removed
Package 'nvidia-headless-495' is not installed, so not removed
Package 'nvidia-headless-510' is not installed, so not removed
Package 'nvidia-headless-510-server' is not installed, so not removed
Package 'nvidia-headless-515' is not installed, so not removed
Package 'nvidia-headless-515-open' is not installed, so not removed
Package 'nvidia-headless-515-server' is not installed, so not removed
Package 'nvidia-headless-520' is not installed, so not removed
Package 'nvidia-headless-520-open' is not installed, so not removed
Package 'nvidia-headless-525' is not installed, so not removed
Package 'nvidia-headless-525-open' is not installed, so not removed
Package 'nvidia-headless-525-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-440-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-450-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460' is not installed, so not removed
Package 'nvidia-headless-no-dkms-460-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-465' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470' is not installed, so not removed
Package 'nvidia-headless-no-dkms-470-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-495' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510' is not installed, so not removed
Package 'nvidia-headless-no-dkms-510-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-515-server' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520' is not installed, so not removed
Package 'nvidia-headless-no-dkms-520-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-open' is not installed, so not removed
Package 'nvidia-headless-no-dkms-525-server' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-common-440-server' is not installed, so not removed
Package 'nvidia-kernel-common-450-server' is not installed, so not removed
Package 'nvidia-kernel-common-460' is not installed, so not removed
Package 'nvidia-kernel-common-460-server' is not installed, so not removed
Package 'nvidia-kernel-common-465' is not installed, so not removed
Package 'nvidia-kernel-common-470' is not installed, so not removed
Package 'nvidia-kernel-common-470-server' is not installed, so not removed
Package 'nvidia-kernel-common-495' is not installed, so not removed
Package 'nvidia-kernel-common-510' is not installed, so not removed
Package 'nvidia-kernel-common-510-server' is not installed, so not removed
Package 'nvidia-kernel-common-515' is not installed, so not removed
Package 'nvidia-kernel-common-515-server' is not installed, so not removed
Package 'nvidia-kernel-common-520' is not installed, so not removed
Package 'nvidia-kernel-common-525-server' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-kernel-source-440-server' is not installed, so not removed
Package 'nvidia-kernel-source-450-server' is not installed, so not removed
Package 'nvidia-kernel-source-460' is not installed, so not removed
Package 'nvidia-kernel-source-460-server' is not installed, so not removed
Package 'nvidia-kernel-source-465' is not installed, so not removed
Package 'nvidia-kernel-source-470' is not installed, so not removed
Package 'nvidia-kernel-source-470-server' is not installed, so not removed
Package 'nvidia-kernel-source-495' is not installed, so not removed
Package 'nvidia-kernel-source-510' is not installed, so not removed
Package 'nvidia-kernel-source-510-server' is not installed, so not removed
Package 'nvidia-kernel-source-515' is not installed, so not removed
Package 'nvidia-kernel-source-515-open' is not installed, so not removed
Package 'nvidia-kernel-source-515-server' is not installed, so not removed
Package 'nvidia-kernel-source-520' is not installed, so not removed
Package 'nvidia-kernel-source-520-open' is not installed, so not removed
Package 'nvidia-kernel-source-525-open' is not installed, so not removed
Package 'nvidia-kernel-source-525-server' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'nvidia-utils-440-server' is not installed, so not removed
Package 'nvidia-utils-450-server' is not installed, so not removed
Package 'nvidia-utils-460' is not installed, so not removed
Package 'nvidia-utils-460-server' is not installed, so not removed
Package 'nvidia-utils-465' is not installed, so not removed
Package 'nvidia-utils-470' is not installed, so not removed
Package 'nvidia-utils-470-server' is not installed, so not removed
Package 'nvidia-utils-495' is not installed, so not removed
Package 'nvidia-utils-510' is not installed, so not removed
Package 'nvidia-utils-510-server' is not installed, so not removed
Package 'nvidia-utils-515' is not installed, so not removed
Package 'nvidia-utils-515-server' is not installed, so not removed
Package 'nvidia-utils-520' is not installed, so not removed
Package 'nvidia-utils-525-server' is not installed, so not removed
Package 'nvidia-fabricmanager-450' is not installed, so not removed
Package 'nvidia-fabricmanager-460' is not installed, so not removed
Package 'nvidia-fabricmanager-470' is not installed, so not removed
Package 'nvidia-fabricmanager-510' is not installed, so not removed
Package 'nvidia-fabricmanager-525' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-450' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-460' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-470' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-510' is not installed, so not removed
Package 'nvidia-fabricmanager-dev-525' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
The following packages will be REMOVED
  dctrl-tools dkms libatomic1:i386 libbsd0:i386 libdrm-amdgpu1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386
  libelf1:i386 libexpat1:i386 libffi8:i386 libgl1:i386 libgl1-mesa-dri:i386
  libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386
  libicu70:i386 libllvm13:i386 libmd0:i386 libnvidia-cfg1-525
  libnvidia-common-525 libnvidia-compute-525:i386 libnvidia-decode-525
  libnvidia-decode-525:i386 libnvidia-egl-wayland1 libnvidia-encode-525
  libnvidia-encode-525:i386 libnvidia-extra-525 libnvidia-fbc1-525
  libnvidia-fbc1-525:i386 libnvidia-gl-525 libnvidia-gl-525:i386
  libsensors5:i386 libstdc++6:i386 libvulkan1:i386 libwayland-client0:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386
  libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxml2:i386 libxnvctrl0
  libxshmfence1:i386 libxxf86vm1:i386 mesa-vulkan-drivers:i386
  nvidia-compute-utils-525 nvidia-dkms-525 nvidia-driver-525
  nvidia-kernel-common-525 nvidia-kernel-source-525 nvidia-prime
  nvidia-settings nvidia-utils-525 pkg-config screen-resolution-extra
  xserver-xorg-video-nvidia-525
0 to upgrade, 0 to newly install, 69 to remove and 10 not to upgrade.
Remv nvidia-driver-525 [525.78.01-0ubuntu0.22.04.1]
Remv nvidia-dkms-525 [525.78.01-0ubuntu0.22.04.1]
Remv dkms [2.8.7-2ubuntu2.1]
Remv dctrl-tools [2.24-3build2]
Remv mesa-vulkan-drivers:i386 [22.0.5-0ubuntu0.3]
Remv libnvidia-fbc1-525:i386 [525.78.01-0ubuntu0.22.04.1]
Remv libgl1:i386 [1.4.0-1]
Remv libglx0:i386 [1.4.0-1]
Remv libglx-mesa0:i386 [22.0.5-0ubuntu0.3]
Remv libgl1-mesa-dri:i386 [22.0.5-0ubuntu0.3]
Remv libllvm13:i386 [1:13.0.1-2ubuntu2.1]
Remv libatomic1:i386 [12.1.0-2ubuntu1~22.04]
Remv libxcb-dri3-0:i386 [1.14-3ubuntu3]
Remv libxcb1:i386 [1.14-3ubuntu3] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxdmcp6:i386 [1:1.1.3-0ubuntu5] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libedit2:i386 [3.1-20210910-1build1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libbsd0:i386 [0.11.5-1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libdrm-amdgpu1:i386 [2.4.110-1ubuntu1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libdrm-nouveau2:i386 [2.4.110-1ubuntu1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libdrm-radeon1:i386 [2.4.110-1ubuntu1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libdrm2:i386 [2.4.110-1ubuntu1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libelf1:i386 [0.186-1build1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libexpat1:i386 [2.4.7-1ubuntu0.2] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libwayland-client0:i386 [1.20.0-1ubuntu0.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libffi8:i386 [3.4.2-4] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libglapi-mesa:i386 [22.0.5-0ubuntu0.3] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libglvnd0:i386 [1.4.0-1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxml2:i386 [2.9.13+dfsg-1ubuntu0.2] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libicu70:i386 [70.1-2] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libmd0:i386 [1.0.4-1build1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv xserver-xorg-video-nvidia-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-cfg1-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-gl-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-gl-525:i386 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-common-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-encode-525:i386 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-decode-525:i386 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-compute-525:i386 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-encode-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-decode-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-egl-wayland1 [1:1.1.9-1.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-extra-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libnvidia-fbc1-525 [525.78.01-0ubuntu0.22.04.1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libsensors5:i386 [1:3.6.0-7ubuntu1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libstdc++6:i386 [12.1.0-2ubuntu1~22.04] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libvulkan1:i386 [1.3.204.1-2] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxxf86vm1:i386 [1:1.1.4-1build3] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxfixes3:i386 [1:6.0.0-1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxcb-shm0:i386 libx11-6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libx11-6:i386 [2:1.7.5-1] [libxcb-present0:i386 libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxext6:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libx11-xcb1:i386 [2:1.7.5-1] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxext6:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxau6:i386 [1:1.0.9-1build5] [libxcb-present0:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxext6:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxcb-dri2-0:i386 [1.14-3ubuntu3] [libxcb-present0:i386 libxcb-glx0:i386 libxcb-randr0:i386 libxext6:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxcb-glx0:i386 [1.14-3ubuntu3] [libxcb-present0:i386 libxcb-randr0:i386 libxext6:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxcb-present0:i386 [1.14-3ubuntu3] [libxcb-randr0:i386 libxext6:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxcb-randr0:i386 [1.14-3ubuntu3] [libxext6:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxcb-shm0:i386 [1.14-3ubuntu3] [libxext6:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 ]
Remv libxcb-sync1:i386 [1.14-3ubuntu3] [libxext6:i386 libxcb-xfixes0:i386 ]
Remv libxcb-xfixes0:i386 [1.14-3ubuntu3] [libxext6:i386 ]
Remv libxext6:i386 [2:1.3.4-1build1]
Remv nvidia-settings [510.47.03-0ubuntu1]
Remv libxnvctrl0 [510.47.03-0ubuntu1]
Remv libxshmfence1:i386 [1.3-1build4]
Remv nvidia-compute-utils-525 [525.78.01-0ubuntu0.22.04.1]
Remv nvidia-kernel-common-525 [525.78.01-0ubuntu0.22.04.1]
Remv nvidia-kernel-source-525 [525.78.01-0ubuntu0.22.04.1]
Remv nvidia-prime [0.8.17.1]
Remv nvidia-utils-525 [525.78.01-0ubuntu0.22.04.1]
Remv pkg-config [0.29.2-1ubuntu3]
Remv screen-resolution-extra [0.18.2]
```

Hope this is of some help.

Alternatively, if this is a problem that's affecting others and is likely to be resolved, and my system isn't adding much insight, I'm prepared to wait and workaround the issue (as I've been doing).

---

### Post by #&amp;thj^% on 2023-01-20
This won't be resolved by an update, This will take a user to fix it.
This would make me nuts, having a system in this state. (just me)
Now this is your choice, to try or just to wait it it out. (I'm not very good at setting on my hands...action action action)
This is where I would start though, by removing the Nvidia driver, then attack the removal of the oracle-kernel.
I saw nothing in your return that worried me, as far as removing Nvidia, 
Has anyone affected filed a bug-report yet???

---

### Post by BJC_001 on 2023-01-20
> **1fallen said:**
> This won't be resolved by an update, This will take a user to fix it.
That's one of the things I'm trying to assess.

On one hand, I don't know what kernel flavour the system was using prior to these issues. Perhaps it was previously using the oracle kernel (possibly as a requirement for the nVidia driver). If that's the case, then it seems possible that a future update might fix the issue.

On the other hand, if the problems have arisen because an odd kernel flavour has been installed, then it seems likely that I'll need to intervene and take remedial action. In that case, if I'm going to need to do something, better now than later.

> **1fallen said:**
> This would make me nuts, having a system in this state. (just me)
It bothers me too but experience suggests that patience can be helpful in these cases.

> **1fallen said:**
> This is where I would start though, by removing the Nvidia driver, then attack the removal of the oracle-kernel.
I saw nothing in your return that worried me, as far as removing Nvidia,
I've now selected the Nouveau driver, rather than the nVidia one. I then tried, again, the command to directly uninstall the oracle kernel ([FONT=courier new]sudo apt remove linux-image-5.15.0-1025-oracle[/FONT]). I aborted as it still wants to *install* an unsigned version instead. That's the same as before, but I was curious.

> **1fallen said:**
> Has anyone affected filed a bug-report yet???
I haven't. I still feel like I'm trying to confirm what the problem is. Is it that the system doesn't work with the oracle kernel? Alternatively, is it that the oracle kernel has been installed inadvertently? If the latter, it seems like it'd be helpful to identify the dependency that got it installed. If I were to file a report, I'd like to assemble the information that'd be relevant.

I'm also conscious that I don't want to waste anyone's time - yours included. However, if others are having the same issue, then I hope this thread might help them too.

I would like to thank you again for your help and I remain open to suggestions.

---

### Post by tea for one on 2023-01-20
Have a look at post no. 7 here [https://ubuntuforums.org/showthread.php?t=2473057](https://ubuntuforums.org/showthread.php?t=2473057)
It seems that you have to remove the Nvidia driver (or use an earlier version of the Nvidia driver) before removing the oracle kernel.

Not having Nvidia, I can't test it for you, although I wish I could.

---

### Post by #&amp;thj^% on 2023-01-20
> **BJC_001 said:**
> That's one of the things I'm trying to assess.

On one hand, I don't know what kernel flavour the system was using prior to these issues. Perhaps it was previously using the oracle kernel (possibly as a requirement for the nVidia driver). If that's the case, then it seems possible that a future update might fix the issue.

The default kernel will never have a oracle naming to it, it will always be generic or signed.
This oracle thing is brand new as far as coming in as "non-selected" and non functioning.. Just to show the Oracle kernel only has "nvidia-515" you started with Nvidia-525....you see my point now.
> **BJC_001 said:**
> 
On the other hand, if the problems have arisen because an odd kernel flavour has been installed, then it seems likely that I'll need to intervene and take remedial action. In that case, if I'm going to need to do something, better now than later.
Bingo, that's what I've been trying to show you.

> **BJC_001 said:**
> 
It bothers me too but experience suggests that patience can be helpful in these cases.
I can't fault that kind of thinking, but here we need to roll up our sleeves and take action.

> **BJC_001 said:**
> 
I've now selected the Nouveau driver, rather than the nVidia one. I then tried, again, the command to directly uninstall the oracle kernel ([FONT=courier new]sudo apt remove linux-image-5.15.0-1025-oracle[/FONT]). I aborted as it still wants to *install* an unsigned version instead. That's the same as before, but I was curious.
The current nvidia driver will keep pulling that in...It needs to be removed to release the correct kernel.

> **BJC_001 said:**
> I'm also conscious that I don't want to waste anyone's time - yours included. However, if others are having the same issue, then I hope this thread might help them too.

I would like to thank you again for your help and I remain open to suggestions.
I have free will, your not wasting my time, but you are hindering my efforts to help you.
Trust me I understand, you don't know me from Adam, but when asking for help, well you get it without me saying anything else.

---

### Post by BJC_001 on 2023-01-22
Hi,

Thanks to this forum, and notably @1fallen, I have resolved this issue. For the benefit of anyone else that is experiencing the same issue, here's what I did.

It's been identified that the problems are caused by the installation of a linux kernel that simply isn't working. That's the *oracle* kernel flavour. That kernel seems to have been installed for nVidia display drivers. The solution is to explicitly remove that kernel.

The first thing I did was change the nVidia display driver, using the *Additional Drivers* page of the *Software & Updates* application. I switched to *"Using NVIDIA driver metapackage from nvidia-driver-470 (proprietary)"*. It's not clear that this is required but I wanted to ensure that I wasn't actively using a driver that might have a dependency on the oracle kernel. After making the change, I restarted just to be sure.

I ran the following command to identify installed packages that mentioned the *oracle* flavour kernel:
```
apt list --installed | grep oracle
```

That generated the following results:
```
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-5.15.0-1025-oracle/jammy-updates,jammy-security,now 5.15.0-1025.31 amd64 [installed,automatic]
linux-modules-5.15.0-1025-oracle/jammy-updates,jammy-security,now 5.15.0-1025.31 amd64 [installed,automatic]
linux-objects-nvidia-515-5.15.0-1025-oracle/jammy-updates,jammy-security,now 5.15.0-1025.31+1 amd64 [installed,automatic]
linux-signatures-nvidia-5.15.0-1025-oracle/jammy-updates,jammy-security,now 5.15.0-1025.31+1 amd64 [installed,automatic]
```

I then ran the following command to remove those, specific packages:
```
sudo apt-get remove linux-image-5.15.0-1025-oracle linux-modules-5.15.0-1025-oracle linux-signatures-nvidia-5.15.0-1025-oracle linux-objects-nvidia-515.5.15.0-1025-oracle
```

That reported the following: *[N.B. An important thing was that the command was not going to install anything, including an unsigned kernel.]*
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note: selecting 'linux-objects-nvidia-515-5.15.0-1025-oracle' for regex 'linux-objects-nvidia-515.5.15.0-1025-oracle'
The following packages will be REMOVED
  linux-image-5.15.0-1025-oracle linux-modules-5.15.0-1025-oracle linux-objects-nvidia-515-5.15.0-1025-oracle
  linux-signatures-nvidia-5.15.0-1025-oracle
0 to upgrade, 0 to newly install, 4 to remove and 3 not to upgrade.
After this operation, 241 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 190877 files and directories currently installed.)
Removing linux-signatures-nvidia-5.15.0-1025-oracle (5.15.0-1025.31+1) ...
Removing linux-image-5.15.0-1025-oracle (5.15.0-1025.31) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.15.0-58-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.15.0-58-generic
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.15.0-1025-oracle
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-58-generic
Found initrd image: /boot/initrd.img-5.15.0-58-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-modules-5.15.0-1025-oracle (5.15.0-1025.31) ...
Removing linux-objects-nvidia-515-5.15.0-1025-oracle (5.15.0-1025.31+1) ...
```

I then quickly checked the */boot/grub/grub.cfg* file to confirm that the toplevel *menuentry* was referencing the 5.15.0-58-generic kernel.

I then restarted, using the default grub Ubuntu menu option and it started into a working system. So, that seems to have removed the problematic kernel flavour and resolved the problem for me. Hopefully this confirmation might help others in the same position.

Thanks again to those in this forum for helping.

---

### Post by #&amp;thj^% on 2023-01-22
Thanks for sharing, I guess it's better if we learn to use our own methods with the same results as "globs"
Just glad your up and running again.

---

