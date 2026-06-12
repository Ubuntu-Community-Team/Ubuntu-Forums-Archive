---
title: "Restore BIOS with Knoppix?"
date: 2008-08-14
forum: Hardware
---

### Post by techdude300 on 2008-08-14
Hi All,

I was dual booting Vista and Ubuntu. I was using Ubuntu to type up a summer book report, and then it froze. I hard reset the computer, and now my Dell Inspiron 1501 can't find the hard drive and won't boot. It can't seem to boot from the Ubuntu live cd either. But it works fine booting Knoppix. I know that you can update the BIOS with Ubuntu, but is there a way to do this with Knoppix?

Thanks in advance for any help.

---

### Post by techdude300 on 2008-08-14
bump =0

---

### Post by techdude300 on 2008-08-14
Something else I forgot to mention: I can only boot Knoppix by typing:

knoppix acpi=off noapic pci=bios

Ubuntu live cd freezed at 100% at the "loading linux kernel" screen.

---

### Post by techdude300 on 2008-08-14
bump.........

---

### Post by techdude300 on 2008-08-14
I'm desperate. I'll wipe my entire drive if that's what it takes.

...bump...

---

### Post by damis648 on 2008-08-14
Adding the boot option "acpi=off" I believe would make it impossible to update the BIOS from Knoppix. What I would do is boot into the BIOS options and see what happens if you look for the attached drives, probably in the page where you select master/slave. Set it to auto for all. Make sure you have "Plug and Play OS" checked. Now, I know my XPS has the BIOS option, check the CMOS POST options. I know I have the option to always do a full or quick POST. Set it to always to a full POST, and try booting Ubuntu again. Let us know how it turns out. :popcorn:

PS. Please stop bumping so much! Maybe once if you post has gone over 14 hrs is my rule of thumb.

---

