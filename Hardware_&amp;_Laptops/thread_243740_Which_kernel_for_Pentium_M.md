---
title: "Which kernel for Pentium M?"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by obi-nine on 2006-08-25
Hi folks,

I was reading a recent Digg post which had [ten tips for optimizing Ubuntu]("http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50") and one of the things that it sugested was to upgrade from a 386 kernel to a 686 if I was running a PII or greater.  I did some research that seemed to suggest that a Pentium M (which I have) is basically an energy efficient Pentium 4 so I tried installing the 686 kernel. But when I tried to re-boot with it it just seized (both in normal and in safe mode).

Anyone have any ideas on this??

thanks,

obi9

---

### Post by Woei on 2006-08-25
> **obi-nine said:**
> Hi folks,

I was reading a recent Digg post which had [ten tips for optimizing Ubuntu]("http://tips.linux.com/article.pl?sid=06/06/08/1651225&tid=50") and one of the things that it sugested was to upgrade from a 386 kernel to a 686 if I was running a PII or greater.  I did some research that seemed to suggest that a Pentium M (which I have) is basically an energy efficient Pentium 4 so I tried installing the 686 kernel. But when I tried to re-boot with it it just seized (both in normal and in safe mode).

Anyone have any ideas on this??


I have a Centrino laptop with a 'Dothan' Pentium M, and I'm running the 686 kernel too. It's the right kernel for the CPU. I don't have any problem with either the 386 (really 486) or 686 kernels.

At what point in the boot process does it halt, and are there any messages shown ? You can disable the splash screen that hides most of the scary, but in this case, interesting messages by adding the 'nosplash' option in /boot/grub/menu.lst at the end of the 686 kernel line at the bottom of the file.

---

### Post by obi-nine on 2006-08-25
hmm... doesn't get that far... only as far as "OK. Linux kernel loading" and then sits there (w/o any disk activity).

Safe mode gets a little farther (but not much).  Strange.

All I did was install the linux-image using synaptic.Do I have to do anything else?

thnx,

obi9

---

### Post by Woei on 2006-08-26
> **obi-nine said:**
> hmm... doesn't get that far... only as far as "OK. Linux kernel loading" and then sits there (w/o any disk activity).

Safe mode gets a little farther (but not much).  Strange.

All I did was install the linux-image using synaptic.Do I have to do anything else?


No, it should have worked just fine. Define "a little further" though. BTW, have you been playing around with prelink ?

---

### Post by obi-nine on 2006-08-26
Don't know anything about prelink.

Safe mode gets to: 

**ACPI: PCI Root Bridge [PC10] (000:00)**.

before hang.

thanks,

obi9

---

