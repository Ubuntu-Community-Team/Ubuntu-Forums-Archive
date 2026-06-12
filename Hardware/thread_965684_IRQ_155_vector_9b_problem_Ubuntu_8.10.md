---
title: "IRQ 155 vector 9b problem Ubuntu 8.10"
date: 2008-10-31
forum: Hardware
---

### Post by timtech on 2008-10-31
I've just installed Ubuntu 8.10 on my Intel Core Duo 2 box and the syslog is constantly filling up with the following IRQ problem:

```
Oct 31 19:51:36 ubuntu kernel: [   11.748200] ->handle_irq():  c01771c0, handle_bad_irq+0x0/0x2a0
Oct 31 19:51:36 ubuntu kernel: [   11.748204] ->chip(): c0475080, no_irq_chip+0x0/0x40
Oct 31 19:51:36 ubuntu kernel: [   11.748207] ->action(): 00000000
Oct 31 19:51:36 ubuntu kernel: [   11.748209]   IRQ_DISABLED set
Oct 31 19:51:36 ubuntu kernel: [   11.748210] unexpected IRQ trap at vector 9b
Oct 31 19:51:36 ubuntu kernel: [   11.748213] irq 155, desc: c049eb00, depth: 1, count: 0, unhandled: 0
Oct 31 19:51:36 ubuntu kernel: [   11.748215] ->handle_irq():  c01771c0, handle_bad_irq+0x0/0x2a0
Oct 31 19:51:36 ubuntu kernel: [   11.748219] ->chip(): c0475080, no_irq_chip+0x0/0x40
Oct 31 19:51:36 ubuntu kernel: [   11.748222] ->action(): 00000000
Oct 31 19:51:36 ubuntu kernel: [   11.748223]   IRQ_DISABLED set
Oct 31 19:51:36 ubuntu kernel: [   11.748225] unexpected IRQ trap at vector 9b

```

..repeated hundreds of times...

/proc/interrupts is:
```
           CPU0       CPU1       
  0:        138          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  8:          2          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:       1745          0   IO-APIC-edge      pata_via
 15:          0          0   IO-APIC-edge      pata_via
 17:       1691          0   IO-APIC-fasteoi   HDA Intel
 20:       1318          0   IO-APIC-fasteoi   uhci_hcd:usb2
 21:      33390          0   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb4, sata_via
 22:        484          0   IO-APIC-fasteoi   uhci_hcd:usb3
 23:          0          0   IO-APIC-fasteoi   uhci_hcd:usb5
155:      20087          0      none-<NULL>  
222:          0          0   PCI-MSI-edge      aerdrv
223:          0          0   PCI-MSI-edge      aerdrv
NMI:          0          0   Non-maskable interrupts
LOC:      17824      16995   Local timer interrupts
RES:       3432       4374   Rescheduling interrupts
CAL:       6163       6126   function call interrupts
TLB:        323        334   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          0
MIS:          0
```

So IRQ 155 is null?  Not sure what that's all about.

uname -a output: 
```
Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
```

Ideas appreiciated - thanks!

---

### Post by LeeHamo on 2008-11-01
I had the same problem when installing 8.10 when it said restart computer after install i got that come up about 50 times, filling screen, had to hold power button to get rid of it, grub loaded fine on restart showing 8.10, im on it now, when i clicked on 8.10 in grub just before the screen went off there was another unexpected something on one line but it went off too quick for me to read it.

Is this gonna be a problem, is there something i need to do?

What is irq vector 9b

Thanks all.

---

### Post by timtech on 2008-11-02
I kinda fixed the symptom by appending:

noapic nolapic

to the boot options at system start time.  (ESC to go to menu, choose 'e' to edit the commands, find the line starting with kernel and press 'e' again, append noapic nolapic press Enter then 'b' to boot.)

---

### Post by LeeHamo on 2008-11-02
How did you find out about this fix? lucky guess?

does it definately work?

---

### Post by antmen on 2008-11-02
noapic nolapic stop message irq 155 vertor 9b but driver nvidia stop.

---

### Post by timtech on 2008-11-03
> **antmen said:**
> noapic nolapic stop message irq 155 vertor 9b but driver nvidia stop.

try installing nvidia drivers after you have put the noapic nolapic stuff on

---

### Post by timtech on 2008-11-05
Found a problem with using noapic nolapic - if you have a multiple core CPU it will disable all of them except one :confused:

If you look at dmesg | less you will see 'SMP disabled' near the top after the noapic stuff.

---

### Post by Maggush on 2008-11-12
I have the exact same problem, any new findings? =)


Regards // Maggush

---

### Post by dariusdwtt on 2008-12-11
similar thing here... sounds serious...

---

### Post by dariusdwtt on 2008-12-11
noapic nolapic worked and nvidia is fine :)

---

### Post by aputsiaq on 2009-01-19
I've experienced a similiar problem "unexpected IRQ trap at vector 9b" that kept on filling up my log files (System > Administration > System Log). My desktop was running slow and at times hanging a few seconds. 
I use Nvidia GeForce 7600 GS, 2GB RAM, Samsung HD400LJ SATA, ASUS motherboard with VIA P4M890 chipset.

Putting acpi=off in as a boot parameter did seem to help, but it disabled my USB-keyboard. I tried changing several settings in my BIOS without any success. I've read elsewhere pci=noacpi as a suggestion, but I don't understand what this does and didn't try that.

The solution was to use the oldest linux-kernel already installed, which was linux-ubuntu-modules-2.6.22-14-generic. I tried using version 2.6.24-21 and 2.6.24-16, but experienced the same problem.

**Edit:** Possible solution: append "[pci=conf1]("http://tldp.org/HOWTO/BootPrompt-HOWTO-4.html")" as a boot-parameter.
Before setting the parameter /var/log/syslog was under heavy pressure. In order to append parameter, open a terminal and type "sudo gedit /boot/grub/menu.lst". The place to append the parameter:
kernel	/boot/vmlinuz-2.6.27-7-generic root=UUID=### ro [COLOR="SeaGreen"]**pci=conf1**[/COLOR]

---

### Post by Maggush on 2009-03-07
I just wanted to make a bump since this problem forces me to use windows instead of linux, and since I prefer linux before windows, I was just wondering if someone has any new ideas of how to fix the problem. It would be really helpful. 

Regards Maggush.:)

---

### Post by dariusdwtt on 2009-03-14
double bump

---

### Post by dariusdwtt on 2009-03-14
double bump

---

### Post by Maggush on 2009-04-10
Another bump. This problem is killing me. haha

---

