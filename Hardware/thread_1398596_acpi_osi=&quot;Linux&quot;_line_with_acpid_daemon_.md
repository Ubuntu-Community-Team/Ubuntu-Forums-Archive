---
title: "acpi_osi=&quot;Linux&quot; line with acpid daemon restart - laptop fan stops ?"
date: 2010-02-04
forum: Hardware
---

### Post by jenaniston on 2010-02-04
A thread started earlier this year pointed out the following way to stop a constant running laptop fan . . .
[http://ubuntuforums.org/showthread.php?t=1232887](http://ubuntuforums.org/showthread.php?t=1232887)

They fixed line in the**  /boot/grub/menu.lst** file with a text editor by adding **acpi_osi="Linux"** at end
to read something like . . . 

```
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=55b3c634-36c5-4a06-b8ec-8d51a8cb97d4 ro quiet splash acpi_osi="Linux"

```and then save and restart - this should fix fan problem in (toshiba/HP/ ? other) laptops.

I am researching why this should work as I am about to try it on a Sharp laptop
 with a constant running fan and hddtemp from 27-34 C. only.

but ***why*** should this work ?
Is power management in laptops not recognizing OS as linux a problem for fan if not specified  . . . I dunno.

Thanks for any insight into this.

---

### Post by compengi on 2011-03-09
hi, the answer to your question lies in this link [https://bugzilla.kernel.org/show_bug.cgi?id=13278](https://bugzilla.kernel.org/show_bug.cgi?id=13278)

---

### Post by www.rzr.online.fr on 2011-10-15
[http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do](http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do)

---

