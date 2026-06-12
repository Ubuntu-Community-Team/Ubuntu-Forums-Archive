---
title: "Cannot adjust screen brightness on laptop with Intel GM965/GL960"
date: 2010-12-19
forum: Hardware
---

### Post by flakeparadigm on 2010-12-19
I've updated to Maverick on my laptop and have been searching around since October and haven't found any working solutions. Both of my previous solutions that worked in earlier Ubuntu releases no longer work here in 10.10.

Here are my older solutions:
tan-***.***/blog/posts/technology/gateway-t-6345u-and-ubuntu-lucid
tan-***.***/blog/posts/technology/gateway-t-6345u-and-ubuntu

Any help would be awesome!
Thanks!

---

### Post by Kramer2010 on 2010-12-19
Had the same problem, but now fixed. See link below.

[http://livinginjava.blogspot.com/201...m-in-acer.html](http://livinginjava.blogspot.com/201...m-in-acer.html)

Seen this before but thought it only worked with ACER laptops.

I'm currently running windows 7 premium on a packard bell Easynote TJ68, with a pentium dual core T4400 @ 2.20 GHz and 4mb ram.

graphics card: Mobile Intel(R) 4 Series Express Chipset Family

---

### Post by Kramer2010 on 2010-12-19
> **Kramer2010 said:**
> Had the same problem, but now fixed. See link below.

[http://livinginjava.blogspot.com/201...m-in-acer.html](http://livinginjava.blogspot.com/201...m-in-acer.html)

Seen this before but thought it only worked with ACER laptops.

I'm currently running windows 7 premium on a packard bell Easynote TJ68, with a pentium dual core T4400 @ 2.20 GHz and 4mb ram.

graphics card: Mobile Intel(R) 4 Series Express Chipset Family

Link does not work, so i've pasted info below..

To those who have problem with brightness configuration after installing Ubuntu 10.10 and you are using Acer Aspire 4741, here's a solution for you:

sudo gedit /etc/default/grub

Change the line GRUB_CMDLINE_LINUX=""  into GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

Restart your linux

---

### Post by flakeparadigm on 2010-12-19
> **Kramer2010 said:**
> Link does not work, so i've pasted info below..

To those who have problem with brightness configuration after installing Ubuntu 10.10 and you are using Acer Aspire 4741, here's a solution for you:

sudo gedit /etc/default/grub

Change the line GRUB_CMDLINE_LINUX=""  into GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

Restart your linux

Sadly that did not work for me. =/

(PS. I believe that Acer actually makes Packard Bell. Along with Gateway, which is the brand of MY laptop.)

---

