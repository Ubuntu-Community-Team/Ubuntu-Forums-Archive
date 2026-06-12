---
title: "ACPI problem for Acer Laptop resolved"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by Iacopo_I on 2005-06-14
**Problem with ACPI for Acer Laptops 1680 series (1681WLCi) DEFINITIVELY RESOLVED**

In the past week I have worked a lot to try to resolve some problems regarding the use of the Power Management on my laptop. Thanks to google I find a lot of useful information but I was unable to find a real definitive solution for this kind of laptop.
The problem are:
    1- This kind of laptops doesn't support APM (Advanced Power Management) but only ACPI (Advanced Configuration and Power Interface)
    2- Today many company build their BIOS only supporting Microsoft OS, so they are incompatible with some standard used by every other OS
    3- I can't find anything in the directories /proc/acpi/ac_adapter and /proc/acpi/battery so I was unable to see the status of my battery and I can't implement the functionality of ACPI on my system
    4- The DSDT (Differentiated System Description Table) resulted to be bugged, I had to correct it
    5- There is a missing ECDT (Embedded Control Description Table) on my system so I have had to patch the kernel to resolve this problem
    6- Acer Laptops uses a so called Smart Batteries System that has a different way to work

You can find an exaustive guide at this link:

[http://www.whoopy.it/linux/](http://www.whoopy.it/linux/) 

The problem is resolved on my Acer Aspire 1981Wlmi with SuSe 9.3 but I think this method is applicable to all the Acer Laptop with other Linux distributions too.


Goodbye,
Iacopo_I

---

### Post by Nikos.Alexandris on 2006-05-16
[QUOTE=Iacopo_I]**Problem with ACPI for Acer Laptops 1680 series (1681WLCi) DEFINITIVELY RESOLVED**

In the past week I have worked a lot to try to resolve some problems regarding the use of the Power Management on my laptop. Thanks to google I find a lot of useful information but I was unable to find a real definitive solution for this kind of laptop.
The problem are:
    1- This kind of laptops doesn't support APM (Advanced Power Management) but only ACPI (Advanced Configuration and Power Interface)
    2- Today many company build their BIOS only supporting Microsoft OS, so they are incompatible with some standard used by every other OS
    3- I can't find anything in the directories /proc/acpi/ac_adapter and /proc/acpi/battery so I was unable to see the status of my battery and I can't implement the functionality of ACPI on my system
    4- The DSDT (Differentiated System Description Table) resulted to be bugged, I had to correct it
    5- There is a missing ECDT (Embedded Control Description Table) on my system so I have had to patch the kernel to resolve this problem
    6- Acer Laptops uses a so called Smart Batteries System that has a different way to work

You can find an exaustive guide at this link:

[http://www.whoopy.it/linux/](http://www.whoopy.it/linux/) 

The problem is resolved on my Acer Aspire 1981Wlmi with SuSe 9.3 but I think this method is applicable to all the Acer Laptop with other Linux distributions too.


Goodbye,
Iacopo_I[/QUOTE]
Hi!

I 've tried in the past, spending some nights... in Debian Sarge first & in Ubuntu Breezy later, to solve this problem on my Acer Aspire 1681 WLMi. Unfortunately, I did not succeed. I think this is the only thing that doesn't do this machine with Ubuntu.

Yesterday I got the Dapper Drake flight cd 7... and it worked! I think that with Ubuntu Dapper Drake all Acer Aspire users are goint to be HAppY!

So for those who still suffer by NON-battery-status just wait till next month...

Greetings,

Nikos.

---

