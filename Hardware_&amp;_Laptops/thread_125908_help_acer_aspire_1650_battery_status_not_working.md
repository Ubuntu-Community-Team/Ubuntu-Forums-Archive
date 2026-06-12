---
title: "help: acer aspire 1650 battery status not working"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by dabd on 2006-02-05
I get the following error when I execute the following:

```
cat /proc/acpi/battery/BAT1/state
present:                 yes
ERROR: Unable to read battery status
```

Also my dmesg has lots of AE_NOT_FOUND acpi errors like this (this a snippet):

```
e62d00), AE_NOT_FOUND
[4342403.343000]     ACPI-0362: *** Error: Looking up [Z00C] in namespace, AE_NOT_FOUND
[4342403.343000] search_node dfe62e00 start_node dfe62e00 return_node 00000000
[4342403.343000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node dfe62d00), AE_NOT_FOUND
[4342413.302000]     ACPI-0362: *** Error: Looking up [Z00C] in namespace, AE_NOT_FOUND
```



I am running breezy with kernel 2.6.12-10-386. 

 Should I update my kernel to 2.6.16-rc1 and patch it with the latest acpi patch to try to fix this problem?

---

### Post by Greg2 on 2006-02-05
[QUOTE=dabd]Should I update my kernel to 2.6.16-rc1 and patch it with the latest acpi patch to try to fix this problem?[/QUOTE]
You can try that, or you can try using a kernel boot parameter in your /boot/grub/menu.1st file. You may want to try using “acpi=strict” (without the quotes) worked for my HP battery status. Please do a search for 'kernel boot parameters' because it's more complex then I completely understand at this time.:-k

---

