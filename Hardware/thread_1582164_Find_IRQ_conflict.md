---
title: "Find IRQ conflict"
date: 2010-09-26
forum: Hardware
---

### Post by KillKRT on 2010-09-26
Hi,

I have an M-Audio Fast Track Pro (USB audio sound card) and I get a lot of clicks/pops even with high latency (44ms), even if I use M-Audio ASIO driver under Windows. I read that this problem could be due to an IRQ conflict, that is there are other hardware devices sharing the same IRQ channel.
How can I detect which hardware devices are sharing the M-Audio one?

Thank you.

By.

---

### Post by P4man on 2010-09-26
open a terminal and type

> lsdev

But Id just go in to the BIOS and see if there isnt an option to assign an IRQ to USB.

---

### Post by KillKRT on 2010-09-26
> **P4man said:**
> open a terminal and type



But Id just go in to the BIOS and see if there isnt an option to assign an IRQ to USB.

I try lsdev, but I wasn't able to find my audio card in the output list :oops:, could you help me?

```

Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:1a.0                 d100-d11f
0000:00:1a.1                 d200-d21f
0000:00:1a.2                 d000-d01f
0000:00:1d.0                 d300-d31f
0000:00:1d.1                 d400-d41f
0000:00:1d.2                 d500-d51f
0000:00:1f.0                 0400-047f 0480-04bf
0000:00:1f.2                 d600-d607 d700-d703 d800-d807 d900-d903 da00-da0f db00-db0f
0000:00:1f.3                 0500-051f
0000:00:1f.5                 dd00-dd07 de00-de03 df00-df07 e000-e003 e100-e10f e200-e20f
0000:01:00.0                   a000-a07f
0000:03:00.1                   b000-b007   b100-b103   b200-b207   b300-b303   b400-b40f
0000:04:00.0                   c000-c0ff
acpi                      9 
ACPI                           0400-0403   0404-0405   0408-040b   0410-0415   0420-042f
ahci                     19 
ata_piix                       d600-d607   d700-d703   d800-d807   d900-d903   da00-da0f   db00-db0f   dd00-dd07   de00-de03   df00-df07   e000-e003   e100-e10f   e200-e20f
b43                      20 
cascade             4       
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
eth0                     28 
fpu                          00f0-00ff
i8042                  1 12 
Intel                    22 
IO-APIC-edge              4 
keyboard                     0060-0060 0064-0064
nvidia                   16 
parport0            3     7  0378-037a 0778-077a
pata_jmicron                     b000-b007     b100-b103     b200-b207     b300-b303     b400-b40f
PCI                          0cf8-0cff 9000-9fff a000-afff b000-bfff c000-cfff
pic1                         0020-0021
pic2                         00a0-00a1
pnp                          0290-029f   0290-0294 04d0-04d1 0800-087f 0880-088f
r8169                            c000-c0ff
rtc0                      8  0070-0073
serial                       03f8-03ff
timer                     0 
timer0                       0040-0043
timer1                       0050-0053
uhci_hcd                       d000-d01f   d100-d11f   d200-d21f   d300-d31f   d400-d41f   d500-d51f
uhci_hcd:usb4            21 
uhci_hcd:usb6            23 
uhci_hcd:usb8            18 
uvesafb                        03c0-03df
vga+                         03c0-03df

```

---

### Post by P4man on 2010-09-26
Its usb audio, so it doesnt get a IRQ for itself. Its one of the uhci_hcd:usbx devices (thats a root hub if Im not mistaken). I dont see a conflict there though.

---

### Post by KillKRT on 2010-09-26
> **P4man said:**
> Its usb audio, so it doesnt get a IRQ for itself. Its one of the uhci_hcd:usbx devices (thats a root hub if Im not mistaken). I dont see a conflict there though.

Reading my motherboard documentation (GIGABYTE GA-P35-DS3) it seems there are 3 root hub (and as you said, they are named uhci_hcd:usbx). So maybe the problem is which device is sharing the root hub... I'll try to change USB devices connection configuration.

Thank you.

---

### Post by Fafler on 2010-09-26
Thats rather weird. The uhci_hdc devices is the legacy USB 1.1 parts of the of the host controller. All USB 2.0 devices should be handled by a ehci device, but i don't see one present on your system. Maybe it's just lsdev.

Try using lspci and look for similar output to this:

```
fafler@carbon:~$ lspci | grep USB
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
fafler@carbon:~$ 

```

The first four is the legacy ports for USB 1.1 devices and the last one if for USB 2.0. All physical ports are mapped to both a port on both a UHCI and the EHCI controller.

Now, to get the best performance possible, you need to make sure your sound card actually uses the EHCI controller. Maybe it has been disabled in you BIOS?

IRQ conflicts very rarely cause problems these days.

---

### Post by P4man on 2010-09-26
Good point fafler. Looks like lsdev is a bit out of date. You can actually view IRQs by opening the file browser and going to

/proc/interrupts

just open it with gedit or what ever.
Here is mine:
```

     CPU0       CPU1       
  0:         34          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 16:         58          0   IO-APIC-fasteoi   uhci_hcd:usb3
 17:         54          0   IO-APIC-fasteoi   ahci, HDA Intel
 18:          5          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb7, pata_jmicron, ohci1394
 19:         48         32   IO-APIC-fasteoi   uhci_hcd:usb6, EMU10K1
 21:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 23:      62902          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5
 28:      60806          0   PCI-MSI-edge      ahci
 29:         60      51284   PCI-MSI-edge      sky2@pci:0000:03:00.0
 30:        285     972118   PCI-MSI-edge      fglrx[0]@PCI:1:0:0
NMI:          0          0   Non-maskable interrupts
LOC:     928766     163649   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:      18175      13674   Rescheduling interrupts
CAL:        348        711   Function call interrupts
TLB:       2833       1492   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         10         10   Machine check polls
ERR:          1
MIS:          0

```
And your hunch that he might be using USB 1.1 sounds like a good one.

---

### Post by KillKRT on 2010-09-26
> **Fafler said:**
> Thats rather weird. The uhci_hdc devices is the legacy USB 1.1 parts of the of the host controller. All USB 2.0 devices should be handled by a ehci device, but i don't see one present on your system. Maybe it's just lsdev.

Try using lspci and look for similar output to this:

```
fafler@carbon:~$ lspci | grep USB
...

```

The first four is the legacy ports for USB 1.1 devices and the last one if for USB 2.0. All physical ports are mapped to both a port on both a UHCI and the EHCI controller.

Now, to get the best performance possible, you need to make sure your sound card actually uses the EHCI controller. Maybe it has been disabled in you BIOS?

IRQ conflicts very rarely cause problems these days.


Thanks... I think EHCI is enabled, my lspci output is:

```

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)

```

The MB manual states that all USB ports are 2.0/1.1, so I think I can select any port to connect my sound card. Anyway how can I find where is currently connected?

Thank you.

---

### Post by P4man on 2010-09-26
unplug it, plug it in again. Then open a terminal and type

dmesg

look at (and post) the last lines. Here is what is shows when I plug a USB headset:
```


[ 3406.240040] usb 4-1: new full speed USB device using uhci_hcd and address 2
[ 3406.404222] usb 4-1: configuration #1 chosen from 1 choice
[ 3406.411195] input: Microsoft LifeChat LX-3000  as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.3/input/input7
[ 3406.411288] generic-usb 0003:045E:070F.0005: input,hidraw4: USB HID v1.00 Device [Microsoft LifeChat LX-3000 ] on usb-0000:00:1a.1-1/input3
[ 3406.526603] usbcore: registered new interface driver snd-usb-audio

```

Looks like a USB 1.1 device (its just a headset)

---

### Post by KillKRT on 2010-09-26
> **P4man said:**
> Good point fafler. Looks like lsdev is a bit out of date. You can actually view IRQs by opening the file browser and going to

/proc/interrupts

just open it with gedit or what ever.
Here is mine:
```

...

```
And your hunch that he might be using USB 1.1 sounds like a good one.

This is my output:

```

killkrt@black:~$ cat /proc/interrupts | grep ehci
 18:       1462       1058       4580       5501   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb8
 23:          1          0          0          1   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6

```

It seems that my *EHCI controllers* are served on IRQ 18 and 23 and share these channels with USB 1.1 port 5/6 and with IO-APIC-fasteoi. :-k
Maybe the problem (of high latency) is due to M-Audio driver, I'm working on Windows 7 64bit. Under Ubuntu Studio 10.04 (64bit) I have not any heavy plug-in in order to test latency, but with low latency (about 10ms) I sometimes get some click!

---

### Post by KillKRT on 2010-09-26
> **P4man said:**
> unplug it, plug it in again. Then open a terminal and type

dmesg

look at (and post) the last lines. Here is what is shows when I plug a USB headset:
```

...

```

Looks like a USB 1.1 device (its just a headset)

Here is my output:

```

[ 5838.025273] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 5838.374472] usb 3-1: configuration #1 chosen from 2 choices

```

Ummm... Am I wrong or is it connected as a USB 1.1 device?

---

### Post by P4man on 2010-09-26
Yep. But it seems to be a native usb 1.1 device (thats what google tells me anyway).

Just something quick to try, put a self powered hub inbetween the audio device and your PC.

I also just saw your previous post about sharing an IRQ with io-apic. This is way above my paygrade, it might be completely normal,  but you can could try disabling apic in the kernel. Its easy enough, see here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

YOu likely also have BIOS options about that, but I have no idea what you should use there really.

edit: 2 More things.
Can you post the complete output of dmesg?
And are you using a RT kernel ?

---

