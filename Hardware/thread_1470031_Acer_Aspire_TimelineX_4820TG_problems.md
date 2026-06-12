---
title: "Acer Aspire TimelineX 4820TG problems"
date: 2010-05-02
forum: Hardware
---

### Post by kjellml on 2010-05-02
Hi

I have a [Acer Aspire TimelineX 4820TG]("http://www.acer.no/acer/product.do?link=oln85e.redirect&changedAlts=&kcond48e.c2att101=-1&CRC=2759084358#wrAjaxHistory=0") laptop.

My specs are:
Intel Core i5 cpu
4GB ram
Hybrid GPU - Intel IGP and Ati Mobility 5470
500GB Harddrive
14" screen

My problems are primary related to the hybrid GPU. I cant get decent performance. The hybrid GPU can either be locked in ATI mode, or switchable between the Intel IGP and Ati.

The ATI driver that "Jockey" activates performs really bad. Compiz effects shows heavy tearing and such. My Lenovo U350 with GMA4500 GPU performs flawlessly on this.


Anybody out there with some insight and tips for me?

---

### Post by Snake231088 on 2010-05-11
The battery state is recognized ok under Ubuntu 10.04?
Because i have the Acer Aspire 5745G and the battery state is not recognized under Ubuntu 10.04, and in an other forum there is another user that has 1 acer aspire timelinex 4820tg and doesn't recognized battery state too.
The  problem is that ubuntu sees the battery always at 100% and always connected to the power.
(sorry  for my English)
Please answer me.

---

### Post by marincop on 2010-05-14
I also have  same problem,too .  Acer TimelineX 4820 Battery status can not show. 9.4 and 10.04 are same status.
Is this the ACPI's problem ? anyone can help ?:(

---

### Post by Snake231088 on 2010-05-14
I think that is a BIOS problem, because the BIOS is very new.
Help!

---

### Post by Amivit on 2010-05-27
I myself have bought the TM 4820TG TimelineX and am having the exact same problem. I would also like to only make use of the onboard intel graphic card and not the more power-consuming ATI HD 5470. 

For starters, how do I find out exactly which GPU is being used at the time being? lspci lists both the Intel and the ATI but I want to know which one is being used.

```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]

```

---

### Post by marm0tte on 2010-06-11
Hello,

I have a 4820TG too, and the same problems as you. The DSDT is buggy (ACPI problems), ethernet card doesn't works, wifi Fn+F3 button disable it but doesn't reenable it ...

Another tread have been open on the ubuntu forums, I will join them to try to help to solve all the problems :
[http://ubuntuforums.org/showthread.php?t=1495123](http://ubuntuforums.org/showthread.php?t=1495123)

---

