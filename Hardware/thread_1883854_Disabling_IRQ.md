---
title: "Disabling IRQ"
date: 2011-11-20
forum: Hardware
---

### Post by waxhead on 2011-11-20
Hi Everyone,

I've been pulling my hair out with problems on my mythbuntu be/fe box since replacing the motherboard.

The backend has 3 PCI haupagge dual tuners in it.  The TV stream works fine initially until the irqs get disabled.

The motherboard was replaced with a P8Z68-V LE, since then I have been seeing this in the logs:


ov 20 18:56:47 mediacentre kernel: [  222.113456] irq 19: nobody cared (try booting with the "irqpoll" option)
Nov 20 18:56:47 mediacentre kernel: [  222.113460] Pid: 2641, comm: mythfrontend.re Tainted: P         C  3.0.0-13-generic #22-Ubuntu
Nov 20 18:56:47 mediacentre kernel: [  222.113462] Call Trace:
Nov 20 18:56:47 mediacentre kernel: [  222.113467]  [<c151902f>] ? printk+0x2d/0x2f
Nov 20 18:56:47 mediacentre kernel: [  222.113470]  [<c10aac99>] __report_bad_irq+0x29/0xd0
Nov 20 18:56:47 mediacentre kernel: [  222.113473]  [<c10ab064>] note_interrupt+0x104/0x150
Nov 20 18:56:47 mediacentre kernel: [  222.113475]  [<c10a958e>] handle_irq_event_percpu+0x9e/0x200
Nov 20 18:56:47 mediacentre kernel: [  222.113478]  [<c1026038>] ? default_spin_lock_flags+0x8/0x10
Nov 20 18:56:47 mediacentre kernel: [  222.113481]  [<c101d45d>] ? __io_apic_modify_irq+0x7d/0x90
Nov 20 18:56:47 mediacentre kernel: [  222.113483]  [<c10a972b>] handle_irq_event+0x3b/0x60
Nov 20 18:56:47 mediacentre kernel: [  222.113485]  [<c10ab7a0>] ? unmask_irq+0x30/0x30
Nov 20 18:56:47 mediacentre kernel: [  222.113487]  [<c10ab7ee>] handle_fasteoi_irq+0x4e/0xc0
Nov 20 18:56:47 mediacentre kernel: [  222.113488]  <IRQ>  [<c1533f72>] ? do_IRQ+0x42/0xc0
Nov 20 18:56:47 mediacentre kernel: [  222.113492]  [<c10af55d>] ? rcu_irq_exit+0xd/0x10
Nov 20 18:56:47 mediacentre kernel: [  222.113494]  [<c152dd20>] ? do_debug+0x180/0x180
Nov 20 18:56:47 mediacentre kernel: [  222.113496]  [<c1533eb0>] ? common_interrupt+0x30/0x38
Nov 20 18:56:47 mediacentre kernel: [  222.113498]  [<c1520000>] ? ext4_check_descriptors+0x224/0x34e
Nov 20 18:56:47 mediacentre kernel: [  222.113499] handlers:
Nov 20 18:56:47 mediacentre kernel: [  222.113502] [<c13b47f0>] usb_hcd_irq
Nov 20 18:56:47 mediacentre kernel: [  222.113504] [<c13b47f0>] usb_hcd_irq
Nov 20 18:56:47 mediacentre kernel: [  222.113505] Disabling IRQ #19

After days of googling this I found this link:

[http://phoronix.com/forums/showthread.php?63509-Sandy-Bridge-PCI-Card-Drivers-Fail-with-quot-Disabling-IRQ-quot](http://phoronix.com/forums/showthread.php?63509-Sandy-Bridge-PCI-Card-Drivers-Fail-with-quot-Disabling-IRQ-quot)


So it might not be related to the ASUS boards per se' but the sandy bridge with the PCI cards...

Here's some info on the setup:

lsusb:

Bus 003 Device 002: ID 2040:9941 Hauppauge WinTV Nova-T-500
Bus 004 Device 002: ID 2040:9950 Hauppauge WinTV Nova-T-500
Bus 005 Device 002: ID 2040:8400 Hauppauge WinTV Nova-T-500

cat /proc/interrupts

           CPU0       CPU1       CPU2       CPU3       
  0:         43          0          0          0   IO-APIC-edge      timer
  1:          2          0          0          0   IO-APIC-edge      i8042
  8:          1          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          4          0          0          0   IO-APIC-edge      i8042
 16:      49647          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb7, uhci_hcd:usb8, nvidia
 17:     303324          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb3, uhci_hcd:usb9, uhci_hcd:usb10
 18:     532390          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb4
 19:     200002          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb5, uhci_hcd:usb6
 21:         11          0          0          0   IO-APIC-fasteoi   mei
 23:      30221          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, ehci_hcd:usb2
 40:          0          0          0          0   PCI-MSI-edge      PCIe PME
 41:          0          0          0          0   PCI-MSI-edge      PCIe PME
 42:          0          0          0          0   PCI-MSI-edge      PCIe PME
 43:          0          0          0          0   PCI-MSI-edge      PCIe PME
 44:          0          0          0          0   PCI-MSI-edge      PCIe PME
 45:          0          0          0          0   PCI-MSI-edge      PCIe PME
 46:          0          0          0          0   PCI-MSI-edge      PCIe PME
 47:       5820          0          0          0   PCI-MSI-edge      eth0
 48:     154073          0          0          0   PCI-MSI-edge      ahci
 49:         20          0          0          0   PCI-MSI-edge      xhci_hcd
 50:          0          0          0          0   PCI-MSI-edge      xhci_hcd
 51:          0          0          0          0   PCI-MSI-edge      xhci_hcd
 52:          0          0          0          0   PCI-MSI-edge      xhci_hcd
 53:          0          0          0          0   PCI-MSI-edge      xhci_hcd
 54:       6393          0          0          0   PCI-MSI-edge      hda_intel
NMI:          0          0          0          0   Non-maskable interrupts
LOC:     618218     509054     429673     520949   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:      83707      54463     144454      45117   Rescheduling interrupts
CAL:        497        864        526        746   Function call interrupts
TLB:       4165       2401       2278       2328   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          4          4          4          4   Machine check polls
ERR:          0
MIS:          0


and this is the listed IRQ's that get disabled from lspci -v

09:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c020 [size=32]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: uhci_hcd

09:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at fb101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: ehci_hcd

09:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c000 [size=32]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: uhci_hcd

09:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at fb100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
        Kernel driver in use: ehci_hcd

---

### Post by vdkeybus on 2011-12-08
I have a very similar (if not the same) issue, on Ubuntu 11.10 with 3.0.0-13 kernel. Thank you for reporting it.

I have already reported the problem on the Linux Kernel mailing list ([https://lkml.org/lkml/2011/11/29/445](https://lkml.org/lkml/2011/11/29/445)), as it seems to affect also the (untainted) current mainline kernel 3.2-rc2.

J.

---

### Post by ian dobson on 2011-12-09
Hi,

There's a bug in the kernel in version 2.6.39 to 3.2.rc4? That stops the irqpoll and irqfixup kernel commandline options from working.

From what I understand the sandybridge chipset doesn't have a PCI bus controller, so all montherboard manufacturers use a PCI-express to PCI bridge chip. And sometimes this chip looses/forgets an interrupt (I have the same problem with 2 PCI tuners on my mythtv backend.)

There is a patch that gets irqpoll working again > 2.6.39 kernels, which I've applied to my 3.0kernel on my myth box and it's been running for 4weeks now (24/7) without a single hickup.

From what I've heard the patch should make it into the Ubuntu 11.10 kernel sometime soon.

Regards
Ian Dobson

---

### Post by terryxela on 2011-12-11
> **ian dobson said:**
> Hi,

There is a patch that gets irqpoll working again > 2.6.39 kernels, which I've applied to my 3.0kernel on my myth box and it's been running for 4weeks now (24/7) without a single hickup.

Regards
Ian Dobson

Ian, I have a similar problem and the channel program does not work for the SBT. I have checked any possible config for the serial port without any luck.
Would you please post the link of the patch.
TIA

-=terry=-

---

### Post by ian dobson on 2011-12-11
Hi,

The patch has made it into the latest ubuntu kernel (3.0.14-23) from what I've read (I'm currently testing it).

If your channel change script uses a serial port, that the irqpoll patch won't help you.

Regards
Ian Dobson

---

### Post by terryxela on 2011-12-11
> **ian dobson said:**
> Hi,

The patch has made it into the latest ubuntu kernel (3.0.14-23) from what I've read (I'm currently testing it).

If your channel change script uses a serial port, that the irqpoll patch won't help you.

Regards
Ian Dobson

Thxs Ian

-=terry=-

---

### Post by ian dobson on 2011-12-13
> **ian dobson said:**
> Hi,

The patch has made it into the latest ubuntu kernel (3.0.14-23) from what I've read (I'm currently testing it).

If your channel change script uses a serial port, that the irqpoll patch won't help you.

Regards
Ian Dobson

Looks as if I spoke too soon, after running for 2 days the DVB-c tuners bombed out with a irq error. back to my home grown kernel......

Regards
Ian Dobson

---

