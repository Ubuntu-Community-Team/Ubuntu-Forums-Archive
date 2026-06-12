---
title: "Battery Charge Monitor -- Not working :("
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by salvius on 2005-08-21
Hello everyone,

I have managed to get my broadcom card fixed, but one problem remains.  When I unplug AC, the Battery Charge Monitor shows that unknown time is left, and thus I can never tell when the system will shut down.  I have tried acpi=force (or on) but that didn't work.  

I have also read the possibility of patching up the kernel, but this is completely unknown waters for me.

The (what I believe to relevant) part of dmesg:

```
  ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
    ACPI-0352: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
search_node ddaa1ee0 start_node ddaa1ee0 return_node 00000000
    ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ddaa1d e0), AE_NOT_FOUND
```

---

### Post by luca_linux on 2005-08-22
What laptop have you got?

---

### Post by salvius on 2005-08-22
[QUOTE=luca_linux]What laptop have you got?[/QUOTE]

It's an Acer Aspire 5002WLMI.

---

### Post by luca_linux on 2005-08-23
Maybe you need Smart Battery support: [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/)

---

### Post by Moobuntu on 2005-08-23
Having a similar problem, only I'm using a Toshiba Satellite Pro L10 (PSL15E-00F0179I). I guess I'll have to wait until SBS is built in. :|

---

