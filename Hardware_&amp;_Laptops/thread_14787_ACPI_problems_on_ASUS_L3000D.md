---
title: "ACPI problems on ASUS L3000D"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by spider7378 on 2005-02-09
Hi!

I'm new to Ubuntu-Linux and hope you can help me. I tried to install Ubuntu from Installation-CD, but after a few seconds the installation hangs. After trying out a little bit, i booted the kernel with acpi=off and installation worked perfectly. 

Now Ubuntu runs, but only without ACPI. Everytime I try booting with kernel-option acpi=on, systems hangs after 

  Starting Ubuntu...

Any suggestions how to solve my problem?

---

### Post by knappen on 2005-02-10
Have you checked your BIOS settings?

---

### Post by spider7378 on 2005-02-11
Yes!

The problem seems to be in the precompiled ubuntu-kernel. I compiled my own kernel yesterday, now ACPI works!! :) Maybe some of the ubuntu/debian-patches won't work with my chipset.

---

