---
title: "Thinkpad X60 Feisty - Suspend issue SOLVED"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by alastair on 2007-05-06
I have a Thinkpad X60s running Edgy. Suspend and hibernate work well (generally).

Yesterday, I installed Feisty (on a different HDD) and was depressed to
see that suspend FAILS. The laptp suspends OK, but does not resume. It
gives a blank screen and on/off busy cursor every now and then. This would
mean a return to Edgy.

However - I have FIXED suspend (and hibernate also works) by adding
the option "ec_intr=0" to the grub boot stanza i.e.

In file /boot/grub/menu.lst - my boot line now looks like :
   
```
# defoptions=quiet splash vga=791 ec_intr=0
```

This was recommended in the Thinkwiki page :

[http://www.thinkwiki.org/wiki/How_to_make_ACPI_work]("http://www.thinkwiki.org/wiki/How_to_make_ACPI_work")

> Many ThinkPads have been hit by a recent (kernel 2.6.16) change to ACPI4Linux that changed the default means of accessing the ACPI Embedded Controller as a way to shake out underlying bugs in the EC access code. If your ThinkPad fails to resume properly (a blinking Sleep light on resume that doesn't go away, or a hang when trying to suspend/standby a second time), adding ec_intr=0 to your kernel command line may help.

I hope this helps someone else.

Alastair

---

### Post by saintjohnny on 2007-05-08
Thanks.  I feel like this is just a band aid and its hurting something else, but it has to be better than "acpi=off"  :)   Cheers


> **alastair said:**
> I have a Thinkpad X60s running Edgy. Suspend and hibernate work well (generally).

Yesterday, I installed Feisty (on a different HDD) and was depressed to
see that suspend FAILS. The laptp suspends OK, but does not resume. It
gives a blank screen and on/off busy cursor every now and then. This would
mean a return to Edgy.

However - I have FIXED suspend (and hibernate also works) by adding
the option "ec_intr=0" to the grub boot stanza i.e.

In file /boot/grub/menu.lst - my boot line now looks like :
   
```
# defoptions=quiet splash vga=791 ec_intr=0
```

This was recommended in the Thinkwiki page :

[http://www.thinkwiki.org/wiki/How_to_make_ACPI_work]("http://www.thinkwiki.org/wiki/How_to_make_ACPI_work")



I hope this helps someone else.

Alastair

---

### Post by Sunflower1970 on 2007-05-08
Anyone try this on an R40 yet? I'd love to upgrade mine, but suspend just doesn't work.

---

### Post by qopax on 2007-05-21
Didn't help me on my thinkpad x31 either.

---

### Post by campbellssource on 2007-11-12
This appears to be working on my x60s (to a certain extent).

I've changed two lines

```
# defoptions=quiet splash vga=791 ec_intr=0
```

and

```
kernel          /boot/vmlinuz-2.6.11-1-686 root=/dev/hda1 ro acpi_sleep=s3_bios
```

---

