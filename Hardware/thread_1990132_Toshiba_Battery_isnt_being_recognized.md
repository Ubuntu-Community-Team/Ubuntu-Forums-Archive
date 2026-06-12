---
title: "Toshiba Battery isnt being recognized"
date: 2012-05-29
forum: Hardware
---

### Post by abimael08 on 2012-05-29
I have a Toshiba Satellite L745-S4310, my battery isnt being detected by Ubuntu 12.04. I tried doing the steps from the following ([http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html)) however, when I attempted to type the first command

# cat /sys/firmware/acpi/tables/DSDT > DSDT.dat

it said Permission Denied. I have tried to figure out how to FIX this battery issue, it seems to be my ONLY problem with UBUNTU, something I would love to fix so that it doesnt randomly just show up like at 43% or 15%. 

Please Assist

---

### Post by 2F4U on 2012-05-29
You would have to add sudo in front of the command. This filesystem is not accessible by normal users. You will then be asked to provide your password.

---

### Post by abimael08 on 2012-06-04
ok thanks

---

