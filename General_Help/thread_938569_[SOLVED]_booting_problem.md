---
title: "[SOLVED] booting problem"
date: 2008-10-05
forum: General Help
---

### Post by suhaib1thariq on 2008-10-05
i previosely had ubuntu gutsy and windows in that i had i had problem of dual booting i can able to boot windows alone if i tried for ubuntu gutsy it showed 
          "[ 0.396000]..MP-BIOS BUG:8254 TIMER NOT CONNECTED TO IO-APIC
[ 0.396000].. KERNEL PANIC-NOT SYNCING TO APIC +TIMER DOESN'T WORK! BOOT WITH APIC=DEBUG AND SEND A REPORT THEN TRY WITH THE 'NOAPIC' OPTION"


so i added a line "noapic nolapic acpi=offpci=noacpi" at tht end of following line in grub screen of my ubuntu option 
"kernel/boot/vmlinuz-2.624-16-generic root=vvid =165bae76-b3c2-4266-83a7-0680463f549-2.6.24-16-generic roquiet splash" 


i had now installed hardy....again i can't able to boot hardy..i again edit the grub page as i did before ....it enters in to hardy...but when i restarted it again not booting....i had to re enter the that line to boot....i need solution for to boot......

---

### Post by plucky on 2008-10-05
> **suhaib1thariq said:**
> i previosely had ubuntu gutsy and windows in that i had i had problem of dual booting i can able to boot windows alone if i tried for ubuntu gutsy it showed 
          "[ 0.396000]..MP-BIOS BUG:8254 TIMER NOT CONNECTED TO IO-APIC
[ 0.396000].. KERNEL PANIC-NOT SYNCING TO APIC +TIMER DOESN'T WORK! BOOT WITH APIC=DEBUG AND SEND A REPORT THEN TRY WITH THE 'NOAPIC' OPTION"


so i added a line "noapic nolapic acpi=offpci=noacpi" at tht end of following line in grub screen of my ubuntu option 
"kernel/boot/vmlinuz-2.624-16-generic root=vvid =165bae76-b3c2-4266-83a7-0680463f549-2.6.24-16-generic roquiet splash" 


i had now installed hardy....again i can't able to boot hardy..i again edit the grub page as i did before ....it enters in to hardy...but when i restarted it again not booting....i had to re enter the that line to boot....i need solution for to boot......

To make it permanent,you have to edit menu.lst and add the options to the kernel line.To do so open a terminal and ```
gksudo gedit /boot/grub/menu.lst
``` add your options and save.You should now be able to boot without editing the grub page.


Good Luck

---

