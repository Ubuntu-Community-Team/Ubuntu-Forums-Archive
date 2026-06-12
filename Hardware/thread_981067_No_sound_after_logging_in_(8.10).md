---
title: "No sound after logging in (8.10)"
date: 2008-11-13
forum: Hardware
---

### Post by kajer on 2008-11-13
I searched and searched, I could not find anything related to what I am experiencing...

I have a Toshiba Dynabook C9 (214LDEW) and it's a great laptop. I have had 7.10 on it for ages, and decided to install 8.10

8.10 was working up until I wanted to turn on bluetooth using the toshset utility. Turns out the toshset utility needs toshiba_acpi.ko in the kernel. Some genius decided to replace toshiba_acpi with tlsup and now the toshset acpi features are useless in 8.10

Okay, I installed a gutsy kernel with working toshiba_acpi module, and everything seemed to work great, except, I noticed I had no sound. The weirder part is that I got sound at the login window, but not after I login...

ideas?

---

### Post by kajer on 2008-11-13
nevermind, I re-installed and downgraded my kernel to 2.6.24-21-generic

toshiba_acpi works with toshset amd I have sound too!

---

