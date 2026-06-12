---
title: "hibernate stops working after installing Kubuntu-desktop"
date: 2005-04-04
forum: Hardware &amp; Laptops
---

### Post by Rebecca on 2005-04-04
I have the following problem:

Under Ubuntu 5.04 the hibernate function works perfectly, after installing kubuntu-desktop from the repository when I select hibernate the computer shuts down properly but craches on wake up.

I tried formatting the Hard Drive and doing a clean install of Kubuntu-desktop (without Gnome) but the same happens.

I am using a Toshiba M35x-s329.

Thanks.

---

### Post by bonifacio on 2005-04-04
Not a solution but might as well share it.  You had better luck on my laptop hibernates partly works the crucial part which is waking up is the problem,  it seems like it shutdowns previously then the bios password dialog appears and proceed to grub and does what seems to be a normal boot up sequence and then just went blank.  Suspend to RAM almost work but I noticed that when it wakes up my Wifi don't try to renew connection.  All of these BTW on a Gnome desktop.

My notebook btw is in the same family M35-S320.

---

### Post by Rebecca on 2005-04-04
Additional information:

There are the final two lines that the kernel displays before hanging:

Additional information:

The last two lines displayed by the kernel beafore hanging are:

ech1: coming out of suspend...
ACPI: PCI interrupt 0000:02:020[A] ->GSI22 (level,low) -> IRQ22


As I stated before the problem happens only when using KDE not in Gnome

---

