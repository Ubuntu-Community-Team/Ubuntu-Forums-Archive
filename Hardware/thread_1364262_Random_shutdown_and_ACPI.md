---
title: "Random shutdown and ACPI"
date: 2009-12-25
forum: Hardware
---

### Post by hejfelix on 2009-12-25
Running ubuntu 9.10

I experienced random shutdowns on my laptop. Disabling acpi with "acpi=off" in grub seems to fix the problem but that simply breaks my manual shutdown. When running ubuntu with acpi=off I cannot shutdown the computer, it goes through the entire shutdown process, displays some dark/gray vertical lines and hangs. After this I can simply click the power button and the computer turns off (no need to hold it for 4 secs like when forcing power down).

So, disabling random shutdowns for me breaks manual shutdowns.

Has anyone had luck fixing random shutdowns on ubuntu 9.10?

I really hope for help since I have searched the net wide and far and posted before without even a single comment or help to find :(

---

### Post by hejfelix on 2009-12-26
This seems to work for me:

[http://ubuntuforums.org/archive/index.php/t-1304987.html]("http://ubuntuforums.org/archive/index.php/t-1304987.html")

---

### Post by cpplinux on 2009-12-26
I have the same issue of random shutdown -- well, it is more like a sudden power-off -- after upgrading to 9.10. It is definitely not a hardware issue because it is fine when boot into windows. Is it a known issue? I wait two months to upgrade and 9.10 is still not stable. What a disappointment!

---

