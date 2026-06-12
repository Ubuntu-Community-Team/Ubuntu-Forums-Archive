---
title: "Kernel Panic -not syncing IO-APIC on Dell Inspiron 6000"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by Jeff Gavett on 2007-01-14
Ubuntu has been chugging along quite faithfully for me on my Dell Inspiron 6000, so I decided to wipe my disk of my windows install and entirely devote myself to linux, as it were. However, I had forgotten the one strange problem I had. If i selected linux manually with the grub loader, before the time ran out, I would get a Kernel Panic -not syncing IO-APIC + Timer doesn't work error. If I let time run out, it went fine. I could also get it to boot by just trying 5 or 6 times.

Now, with a fresh install without the full menu, GRUB loads fast enough that I'm having this problem again. Is there any way to fix this issue? I would even settle for a few lines of code to simply delay GRUB's booting of Ubuntu, as that seems to have fixed the problem in the past.

---

### Post by Jeff Gavett on 2007-01-15
Can anyone help?

---

### Post by RandomJoe on 2007-01-15
If you're happy just having Grub wait a bit (or even forever, until you select something) just edit /boot/grub/menu.lst to enable the boot menu and extend the timeout time (or disable it).

In that file you will find:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

Set the timeout to however long you need, and if you want to see the menu comment out the hiddenmenu line.  (It defaults to hidden, I have commented it in mine as shown above.)

---

### Post by vandalous03 on 2007-01-15
I have the same problem on a different system.Any suggestions-solutions?
Please Help!

---

### Post by RandomJoe on 2007-01-15
The other option I thought of, does it boot properly if you add the "noapic" boot parameter?  I'm not sure what consequences that has, but it seems to be needed for a variety of systems...

---

### Post by Jeff Gavett on 2007-01-16
Bringing timeout seconds to 5 makes for a clean boot every single time. What a funny solution! Hope it helps some other people too.

---

### Post by SaberCat on 2007-12-29
I'm running ubuntu 7.04 on a Dell Dimension E521 and solved the start-up "Kernel Panic -not syncing IO-APIC" problem by adding 'noapic' to the kernel boot command in file /boot/grub/menu.lst:

kernel     /boot/kernel/vmlinux-2.6.20-16-generic root=UUID=4b8699f2-6f4d-4c8b-9d87-f5c80aafcec6 ro quiet splash **noapic**

Hope this helps others...

---

