---
title: "Disabled ACPI on Toshiba A105-2051, solved the problem, but now Ubuntu runs slow"
date: 2010-10-04
forum: Hardware
---

### Post by diablo75 on 2010-10-04
Someone I know has a Toshiba A105-2051 laptop that we put Ubuntu on a while back and they are very pleased with it.  Except from the beginning we had these two problems:

1.  Wireless adapter would randomly fail a few minutes after using the laptop.

2.  USB Mouse (Wired or Wireless) also randomly fail.

When either of these issues happen, the only way to resolve it was to restart the whole system.

As an experiment I decided to edit /etc/default/grub and disable ACPI.

The good news is this actually solved the above two problems.  The bad news is it caused a bigger one:  Poor system performance.

So I'd like some help trying to recreate the problem, find all the right log files that have something to say about these glitches, and hopefully find something less broad solution than disabling ACPI so hopefully this person can use their system without hardware glitches and wish good performance.

I figured the first step would be to enable ACPI again and wait for the problems to occur again.  But what next?  What all can I do in an effort to nail down a good diagnosis to solve the problem?

---

