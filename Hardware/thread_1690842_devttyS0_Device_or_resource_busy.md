---
title: "/dev/ttyS0: Device or resource busy"
date: 2011-02-19
forum: Hardware
---

### Post by piyushpandey on 2011-02-19
hello to everybody

I have Ubuntu Lucid 10.04 installed on my Desktop and I have a PCI serial card in my computer and it has only one serial port.

Actually I want to use this serial port for the serial communication and for that I executed this command :

$ setserial -g /dev/ttyS[0123]

and I got this as output:

/dev/ttyS0: Device or resource busy
/dev/ttyS1, UART: undefined, Port: 0xee00, IRQ: 16
/dev/ttyS2, UART: undefined, Port: 0xed00, IRQ: 17
/dev/ttyS3, UART: unknown, Port: 0xec00, IRQ: 17

in this it is showing that my serisl port named /dev/ttyS0 is busy and can't be used for the serial communication.

But it is happening from past couple of days, and before that everything was just fine and on the execution of the previous command it was giving this as output:

/dev/ttyS0, UART: undefined, Port: 0xef00, IRQ: 16
/dev/ttyS1, UART: undefined, Port: 0xee00, IRQ: 16
/dev/ttyS2, UART: undefined, Port: 0xed00, IRQ: 17
/dev/ttyS3, UART: unknown, Port: 0xec00, IRQ: 17


So now what is this happening ...........................:(


I also googled a lot and got various hints but nothing worked well , and I tried to know whether the interrupt no. 16 being used by some other device than for that I checked the /proc/interrupts file and got the following result:

           CPU0       CPU1       
  0:         69          0   IO-APIC-edge      timer
  1:         43       5783   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:     455224          0   IO-APIC-edge      i8042
 14:          0          0   IO-APIC-edge      ata_piix
 15:          0          0   IO-APIC-edge      ata_piix
[COLOR=Red] 16:        891     121426   IO-APIC-fasteoi   uhci_hcd:usb5, i915, HDA Intel, serial[/COLOR]
 17:          4          0   IO-APIC-fasteoi 
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:     149907          0   IO-APIC-fasteoi   ata_piix, uhci_hcd:usb3
 20:         56      49397   IO-APIC-fasteoi   ohci1394, eth0
 23:     478297          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2
NMI:          0          0   Non-maskable interrupts
LOC:    1844145    1720957   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:      74493      98624   Rescheduling interrupts
CAL:         90        128   Function call interrupts
TLB:       7221       7432   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         23         23   Machine check polls
ERR:          1
MIS:          0
~
~
~
~

In this file I saw that the serial port and the Intel HDA both are using the same interrupt no 16 and therefore I think the serial port is not responding or is busy.

I checked the other serial port /dev/ttyS1 with the same IRQ 16 and executed this command :

$ setserial /dev/ttyS1 -a

and got the following result:

/dev/ttyS1, Line 1, UART: undefined, Port: 0xee00, IRQ: 16
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test



So this was free and I tried to use it.
So I tried to switch over to other serial port by running the following command:

$ setserial /dev/ttyS1 uart 16550A
$ setserial /dev/ttyS1  -a

and the result was this:

/dev/ttyS1, Line 1, UART: 16550A, Port: 0xee00, IRQ: 16
    Baud_base: 115200, close_delay: 50, divisor: 0
    closing_wait: 3000
    Flags: spd_normal skip_test

So I tried to use it and when I did this the system gets shutdown.:confused:


I tried this with the other two ports also but got nothing working and the system shuts down in each case and the result obtained all the time was same :

$ setserial /dev/ttyS0 -a
/dev/ttyS0: Device or resource busy

So I want to know how I can troubleshoot this problem .......please help me out of this .


Thank you

---

