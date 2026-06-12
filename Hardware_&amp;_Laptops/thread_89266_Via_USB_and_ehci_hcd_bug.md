---
title: "Via USB and ehci_hcd bug"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by Mac_D83 on 2005-11-12
[Update] It seems that this is a bios bug and not a ehci_hcd bug.

Hi there

I've just bought a Shg-notebook 4020(rebranded Mitac 8666) and I have some trouble getting the USB to work properly. I get the following message from dmesg when I try to attach my Verbatim USB memory 

[4294838.871000] usb 4-4: new high speed USB device using ehci_hcd and address 2
[4294839.871000] ehci_hcd 0000:00:10.3: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[4294850.365000] usb 4-4: device not accepting address 2, error -110
[4294850.431000] usb 4-4: new high speed USB device using ehci_hcd and address 3
[4294861.928000] usb 4-4: device not accepting address 3, error -110
[4294861.990000] usb 4-4: new high speed USB device using ehci_hcd and address 4
[4294872.413000] usb 4-4: device not accepting address 4, error -110
[4294872.475000] usb 4-4: new high speed USB device using ehci_hcd and address 5
[4294882.905000] usb 4-4: device not accepting address 5, error -110

It also fail mount the drive and to add an entry in /dev. I have updated my pci.ids file, and lspci says I have the following USB hardware

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

I have also tried to connect my MS explorer mouse. It kind of works... It is properly regonized, but it is praticaly unusable because it feels very slow. The output from dmesg when I connect the mouse is

[4295723.710000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[4295725.270000] usbcore: registered new driver hiddev
[4295725.658000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse\uffff E xplorer] on usb-0000:00:10.1-2
[4295725.658000] usbcore: registered new driver usbhid
[4295725.658000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver

All of my USB devices work perfectly on my desktop Ubuntu install. I've searched the forums, and found a stop-gap solution for the problem in this thread 
[http://ubuntuforums.org/showthread.php?t=81674&highlight=usb]("http://ubuntuforums.org/showthread.php?t=81674&highlight=usb")

The following command "fixes" the problem with the USB memory but not the mouse

$ sudo modprobe -r ehci_hcd

Now dmesg says

2 13:25:27 localhost kernel: [4297712.210000] usb 2-2: new full speed USB device using uhci _hcd and address 3
Nov 12 13:25:29 localhost kernel: [4297714.252000] scsi0 : SCSI emulation for USB Mass Storage d evices
Nov 12 13:25:29 localhost usb.agent[8971]:      usb-storage: already loaded
Nov 12 13:25:34 localhost kernel: [4297719.552000]   Vendor: VBTM      Model: Store 'n' Go Rev: 1.04
Nov 12 13:25:34 localhost kernel: [4297719.552000]   Type:   Direct-Access ANSI SCSI revision: 00
Nov 12 13:25:36 localhost kernel: [4297721.252000] SCSI device sda: 1003520 512-byte hdwr sector s (514 MB)
Nov 12 13:25:36 localhost kernel: [4297721.552000] sda: Write Protect is off
Nov 12 13:25:37 localhost kernel: [4297722.752000] SCSI device sda: 1003520 512-byte hdwr sector s (514 MB)
Nov 12 13:25:37 localhost kernel: [4297723.052000] sda: Write Protect is off
Nov 12 13:25:38 localhost kernel: [4297723.052000]  /dev/scsi/host0/bus0/target0/lun0: p1
Nov 12 13:25:38 localhost kernel: [4297723.354000] Attached scsi removable disk sda at scsi0, ch annel 0, id 0, lun 0
Nov 12 13:25:38 localhost scsi.agent[9016]:      sd_mod: loaded sucessfully (for disk)
Nov 12 13:27:59 localhost kernel: [4297864.294000] usb 2-2: USB disconnect, address 3
Nov 12 13:27:59 localhost kernel: [4297864.352000] SCSI error : <0 0 0 0> return code = 0x10000
Nov 12 13:27:59 localhost kernel: [4297864.352000] end_request: I/O error, dev sda, sector 268
Nov 12 13:28:22 localhost kernel: [4297887.210000] usb 2-2: new full speed USB device using uhci_hcd and address 4Nov 12 13:28:24 localhost kernel: [4297889.252000] scsi1 : SCSI emulation for USB Mass Storage devices
Nov 12 13:28:24 localhost usb.agent[9263]:      usb-storage: already loaded
Nov 12 13:28:29 localhost kernel: [4297894.552000]   Vendor: VBTM      Model: Store 'n' Go      Rev: 1.04
Nov 12 13:28:29 localhost kernel: [4297894.552000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Nov 12 13:28:31 localhost kernel: [4297896.152000] SCSI device sda: 1003520 512-byte hdwr sectors (514 MB)
Nov 12 13:28:31 localhost kernel: [4297896.452000] sda: Write Protect is off
Nov 12 13:28:32 localhost kernel: [4297897.652000] SCSI device sda: 1003520 512-byte hdwr sectors (514 MB)
Nov 12 13:28:32 localhost kernel: [4297897.952000] sda: Write Protect is off
Nov 12 13:28:33 localhost kernel: [4297897.952000]  /dev/scsi/host1/bus0/target0/lun0: p1
Nov 12 13:28:33 localhost kernel: [4297898.254000] Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
Nov 12 13:28:33 localhost scsi.agent[9310]:      sd_mod: loaded sucessfully (for disk)
Nov 12 13:35:40 localhost kernel: [4298325.294000] usb 2-2: USB disconnect, address 4
Nov 12 13:35:43 localhost kernel: [4298328.960000] usb 2-2: new low speed USB device using uhci_hcd and address 5
Nov 12 13:35:45 localhost kernel: [4298330.758000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse\uffff Explorer] on usb-0000:00:10.1-2

So it kind of works, but it doesn't seem as a viable solution to unload the ehci_hcd module every time I want to use the USB memory. Does anyone know another solution, eg. upgrading the kernel or the ehci_hcd module?

Michael Mc Donnell

---

### Post by ggravier on 2006-07-06
Just so that you know that I have the exact same behavior, and the modprobe -r fixes things the exact same way, on a Shuttle ST20G5 PC which has an nVIDIA chipset.

So... clearly a bug... which needs to be squashed.

Gilles

---

### Post by cedced on 2006-07-15
just wanted to confirm this bug.

I have a VIA USB controller (VT82xxxxx UHCI USB 1.1 Controller (rev 80)), and i experience the exact same problem.

modprobe -r ehci_hcd does indeed fix the problem, but an upstream fix would be nice :)

---

### Post by Mac_D83 on 2006-07-17
Can you please post the output of lspci? I think the problem is caused by either the USB 2.0 controller(because removing the module ehci_hcd helps) or a combination of the USB 1.1 and USB 2.0 controller.

Michael Mc Donnell

---

### Post by cedced on 2006-07-18
> **Mac_D83 said:**
> Can you please post the output of lspci? I think the problem is caused by either the USB 2.0 controller(because removing the module ehci_hcd helps) or a combination of the USB 1.1 and USB 2.0 controller.

Michael Mc Donnell


```
ced@chasiewbao:~$ lspci 
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:09.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 20)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```


I'm a bit rusty with modules configuration. Could you remind me how to disable a module (ehci_hcd) permanently, so i don't have to remove it manually at each reboot. Thanks.

---

### Post by cedced on 2006-07-18
Something I forgot to mention: I'm running Dapper Drake with the latest kernel installed (2.6.15-26-386). I believe this bug was introduced a few kernel revisions ago. And for the records, the machine is a TwinHead E14A laptop.

---

### Post by Mac_D83 on 2006-07-19
> I'm a bit rusty with modules configuration. Could you remind me how to disable a module (ehci_hcd) permanently, so i don't have to remove it manually at each reboot. Thanks.
See
[http://www.ubuntuforums.org/showthread.php?t=155289](http://www.ubuntuforums.org/showthread.php?t=155289)

You have to add "blacklist ehci_hcd" to the end of the file /etc/modprobe.d/blacklist

The following command ought to do it(haven't tested it though)

```
$ sudo echo "blacklist ehci_hcd" >> /etc/modprobe.d/blacklist
```

Michael Mc Donnell

---

### Post by Mac_D83 on 2006-07-19
I searched the lkml a bit and found this
[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/a57178354fc19045/c43fe79214f1f5a1?lnk=st&q=Unlink+after+no-IRQ%3F+Controller+is+probably+using+the+wrong+IRQ+via+ehci&rnum=1&hl=en#c43fe79214f1f5a1](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/a57178354fc19045/c43fe79214f1f5a1?lnk=st&q=Unlink+after+no-IRQ%3F+Controller+is+probably+using+the+wrong+IRQ+via+ehci&rnum=1&hl=en#c43fe79214f1f5a1)
which linked to this
[http://bugzilla.kernel.org/show_bug.cgi?id=6654](http://bugzilla.kernel.org/show_bug.cgi?id=6654)
So you just have to pass "acpi=noirq" to the kernel(though it might break something else?). You can do it by editing the file /boot/grub/menu.lst
```
$ sudo gedit /boot/grub/menu.lst
```

Scroll down until you find something like
```

title        Ubuntu, kernel 2.6.15-25-386
root         (hd0,1)
kernel       /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
...

```
Add the option "acpi=noirq" so you'll have something like
```

title        Ubuntu, kernel 2.6.15-25-386
root         (hd0,1)
kernel       /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash acpi=noirq
...

```

That fixed it for me, and USB 2.0 is at full speed :D

Michael Mc Donnell

---

### Post by Mac_D83 on 2006-07-20
Well I think i've kinda found out why I've had trouble with my laptop. I also had problems with speedstep, so I checked out the ACPI support

```
mac@mac-laptop:~$ dmesg |grep ACPI
[17179569.184000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[17179569.184000] ACPI: RSDT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bffbd60
[17179569.184000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bfffb00
[17179569.184000] ACPI: MADT (v001 INSYDE APIC_000 0x30303030 0000 0x00010200) @ 0x1bfffb90
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030522) @ 0x1bffbd90
[17179569.184000] ACPI: DSDT (v001 INSYDE    PN800 0x00001000 INTL 0x02002036) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179572.688000] ACPI: Looking for DSDT ... not found!
[17179572.692000] ACPI: setting ELCR to 0ea0 (from 0ca0)
[17179572.804000] ACPI: bus type pci registered
[17179572.804000] ACPI: Subsystem revision 20051216
[17179572.808000] ACPI: Interpreter enabled
[17179572.808000] ACPI: Using PIC for interrupt routing
[17179572.808000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.808000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.812000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.828000] ACPI: Embedded Controller [EC0] (gpe 1) interrupt mode.
[17179572.832000] pnp: PnP ACPI init
[17179572.836000] pnp: PnP ACPI: found 8 devices
[17179572.836000] PnPBIOS: Disabled by ACPI PNP
[17179573.276000] ACPI wakeup devices:
[17179573.276000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.648000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.648000] ACPI: Processor [CPU0] (supports 16 throttling states)
[17179574.656000] ACPI: Thermal Zone [TZ0] (0 C)
[17179622.572000] ACPI: AC Adapter [AC] (on-line)
[17179622.644000] ACPI: Power Button (FF) [PWRF]
[17179622.644000] ACPI: Lid Switch [LID]
[17179622.644000] ACPI: Sleep Button (CM) [SBTN]
[17179622.644000] ACPI: Power Button (CM) [PBTN]
[17179622.740000] ACPI: Battery Slot [BAT0] (battery present)
[17179622.764000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)

```
This line especially caught my attention
```
[17179572.688000] ACPI: Looking for DSDT ... not found!
```
So it appears that ACPI isn't supported for Mitac 8666(8x66?) under Linux!?! No wonder it doesn't work. This explains why i have to give the control of IRQ to the BIOS. So I have to either upgrade my BIOS or modify the DSDT? Maybe you guys need to do the same?

---

### Post by cedced on 2006-07-22
> **Mac_D83 said:**
> I searched the lkml a bit and found this
[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/a57178354fc19045/c43fe79214f1f5a1?lnk=st&q=Unlink+after+no-IRQ%3F+Controller+is+probably+using+the+wrong+IRQ+via+ehci&rnum=1&hl=en#c43fe79214f1f5a1](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/a57178354fc19045/c43fe79214f1f5a1?lnk=st&q=Unlink+after+no-IRQ%3F+Controller+is+probably+using+the+wrong+IRQ+via+ehci&rnum=1&hl=en#c43fe79214f1f5a1)
which linked to this
[http://bugzilla.kernel.org/show_bug.cgi?id=6654](http://bugzilla.kernel.org/show_bug.cgi?id=6654)
So you just have to pass "acpi=noirq" to the kernel(though it might break something else?).

That fixed it for me, and USB 2.0 is at full speed :D

Michael Mc Donnell

I gave it a try but it didn't fix the problem for me.

I had to blacklist the ehci_hcd module as suggested by Mac_D83 to get my USB devices recognized. The problem is that with only uhci_hcd module left, USB is stuck on 1.1 low speed...

I tried removing uhci_hcd instead of ehci_hcd but I didnt work at all. Bad luck.

Anyway, thanks for your help guys. At least it works at slow speed. I may compile one of the newer kernel and see if there's any fix upstream.

---

### Post by cedced on 2006-07-25
FYI, I opened a bug report on launchpad.net: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/53972](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/53972)

---

### Post by mahalia on 2007-02-12
thanks for the info on how to fix the usb problem, i have an amilo l7310 gw laptop, was driving me crazy,ps if you update automatically, the updater erases the fix from the file you mention so you have to renter the info, especially if it adds new kernel.wierd

---

