---
title: "# cat /proc/pci"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by Ominus on 2005-03-01
Dunno if here is the right place for this thread.. but i got a problem installing a hardware since the command #cat /proc/pci gives me a "file not found" message. So i can't figure whats the IRQ and I/O to try a setserial command. What should i do?

---

### Post by alastair on 2005-03-01
Try

lspci

and note that you can give one or more "-v" args for more information.

---

### Post by Ominus on 2005-03-01
Sure... i tryed "lspci -vv" too... but still no success.. it doesn't show IRQ or I/O.

---

### Post by alastair on 2005-03-01
Mine seems to :

lspci -vv | grep Interrupt

        Interrupt: pin A routed to IRQ 11
        Interrupt: pin B routed to IRQ 11
        Interrupt: pin C routed to IRQ 11
        Interrupt: pin D routed to IRQ 11

etc.

---

### Post by Ominus on 2005-03-02
Interrupt: pin A routed to IRQ 169  :-k  :-k  makes any sense??

---

### Post by alastair on 2005-03-02
Look in the syslog :

/var/log/syslog
dmesg

Pay close attention to mention of ACPI and IRQ - see if anything's odd.

Perhaps this is an ACPI issue i.e. interupt routing via ACPI, or something

---

### Post by Ominus on 2005-03-03
Hum... i'm not good in such things... a lot of things appeared in that log... by the way... i tryed setserial with IRQ 0 to 15.. and none of them worked...
Ubuntu absolutly won't find my modem...  :cry:

---

### Post by alastair on 2005-03-04
Just edit the "/var/log/syslog" file, or look at the output of the command "dmesg".

Look for lines mentioning (case insensitive) "acpi", "irq" , "serial" maybe.

In my "dmesg" (and "syslog") is a note :

PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.

So - do you see anything like this as well?

If so, perhaps try booting linux with the "pci=routeirq" argument i.e.

Stop at the boot/grub screen (ESC)
locate your kernel (default selected probably)
"e" to edit (and perhaps "e" again on the kernel line)
add "pci=routeirq" to the end
"b" to boot

Maybe this helps. Maybe not.

---

### Post by Ominus on 2005-03-05
Well... i tryed dmesg, I think the only relevant things are:

"PCI: Using ACPI for IRQ routing
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 169

...

Using vector-based indexing
IRQ to pin mappings:
IRQ0 -> 0:2
IRQ1 -> 0:1
IRQ3 -> 0:3
IRQ4 -> 0:4
IRQ5 -> 0:5
IRQ6 -> 0:6
IRQ7 -> 0:7
IRQ8 -> 0:8
IRQ9 -> 0:9
IRQ10 -> 0:10
IRQ11 -> 0:11
IRQ12 -> 0:12
IRQ13 -> 0:13
IRQ14 -> 0:14
IRQ15 -> 0:15
IRQ169 -> 0:16"

"0000:00:08.0" is my modem...


I also tryed the "pci=routeirq" thing... but I got a 

PCI: Unknown Command: "routeirq"

And also, in my "dmesg" there was no notes like yours...

---

