---
title: "Question about udev rules"
date: 2012-09-15
forum: Hardware
---

### Post by mp035 on 2012-09-15
Hi All,
I have been having issues where my FTDI devices were not getting assigned the permissions which I put in a custom udev rules file.  I narrowed it down to a conflict with another file, but I do not understand why there is a conflict.

Here are the 2 files

XX-ftdi.rules:
```



ATTR{idVendor}=="0403", ATTR{idProduct}=="6001", MODE="0666"

```

51-century-cd.rules:
```



ATTR{idVendor}=="0b0d", ATTR{idProduct}=="0000", MODE="0666"

```

If I name XX-ftdi.rules as 50-ftdi.rules, the permissions are not assigned, however if I name XX-ftdi.rules as 52-ftdi.rules, everything works as expected.  Can anyone explain why the century cd rules is wiping the permissions?

I really need to understand this as I am the developer of optio-cd and I distribute a rules file which could possibly be causing users some trouble.

---

