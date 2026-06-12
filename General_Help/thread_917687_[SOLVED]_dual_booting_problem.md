---
title: "[SOLVED] dual booting problem"
date: 2008-09-12
forum: General Help
---

### Post by suhaib1thariq on 2008-09-12
hai, i am having amd 64 and now using windows xp service pack 2....i want 2 use ubuntu i installed ubuntu by making apic disabled ,,after that windows is not working.if i had enabled apic while ubuntu loading it shows...
"[    0.396000]..MP-BIOS BUG:8254 TIMER NOT CONNECTED TO IO-APIC
[    0.396000].. KERNEL PANIC-NOT SYNCING TO APIC +TIMER DOESN'T WORK! BOOT WITH APIC=DEBUG AND SEND A REPORT THEN TRY WITH THE 'NOAPIC' OPTION"
     HOW CAN I RESOLVE AND USE DUAL BOOTING IN MY SYSTEM.........

---

### Post by quibbler on 2008-09-12
> **suhaib1thariq said:**
> hai, i am having amd 64 and now using windows xp service pack 2....i want 2 use ubuntu i installed ubuntu by making apic disabled ,,after that windows is not working.if i had enabled apic while ubuntu loading it shows...
"[    0.396000]..MP-BIOS BUG:8254 TIMER NOT CONNECTED TO IO-APIC
[    0.396000].. KERNEL PANIC-NOT SYNCING TO APIC +TIMER DOESN'T WORK! BOOT WITH APIC=DEBUG AND SEND A REPORT THEN TRY WITH THE 'NOAPIC' OPTION"
     HOW CAN I RESOLVE AND USE DUAL BOOTING IN MY SYSTEM.........
Try this:
leave apic on in the bios
start the computer...at the grub screen go to your ubuntu option
and press e to edit the line
it should look something like this but not exactly your UUID will be different 

/boot/vmlinuz-2.6.24-20-generic root=UUID=6ad3a146-1823-4736-a4fb-8eec618ebf80 ro quiet

go to the end of the line and add this

noapic nolapic acpi=off pci=noacpi

your line will look like this but with your UUID

/boot/vmlinuz-2.6.24-20-generic root=UUID=6ad3a146-1823-4736-a4fb-8eec618ebf80 ro quiet noapic nolapic acpi=off pci=noacpi

now press b to boot.
if this works, you will have to permently edit your /boot/grub/menu.lst  

Let 's hope it works.

Regards quibbler

---

### Post by suhaib1thariq on 2008-09-14
thank u...quibbler .........it's working thanks a lot

---

