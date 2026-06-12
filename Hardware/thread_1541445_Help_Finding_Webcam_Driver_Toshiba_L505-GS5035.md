---
title: "Help Finding Webcam Driver Toshiba L505-GS5035"
date: 2010-07-29
forum: Hardware
---

### Post by illusionate on 2010-07-29
I posted and sucessful install guide and ACPI work around and am loving Unbuntu.
Currently using 9.10 because I'm afraid to upgrade to 10.04 because of ACPI issues.

Okay to the issue:

I am dumbfounded trying to find the driver to my webcam on my L505-GS5035. Is there a command I can type to find my webcam driver and look for a native linux driver Or should I try NDISwrapper?

---

### Post by iponeverything on 2010-07-29
the bus id might show up with:


```
lsusb
```

mine shows up with lsusb as 

```
Bus 001 Device 002: ID 17ef:480c Lenovo
```

You can do a google search using the busid and some other keywords.

---

### Post by cgroza on 2010-07-29
GSPCA doesn't works for you? Did you tried installing cheese to test your webcam?
If not try:

```
sudo apt-get install cheese
```

---

