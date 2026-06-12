---
title: "NEC Versa P440 Suspend-To-RAM"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by desplesda on 2005-06-13
I've got an NEC Versa P440 laptop running Hoary. Right now it's got a problem with going to sleep.

Putting it to sleep works perfectly. Getting it to wake up's tricky. I'm currently dual booting it with WinXP to make sure it's not a hardware problem - it's not, suspend works fine and I wake it up with the power switch.

Here is my process:
1. Put it to sleep, either by running /etc/acpi/sleep.sh or echo -n "mem" > /sys/power/state
2. Laptop goes to sleep; power is shut off and the 'suspended' LED glows
3. Flick the power switch to wake it up
4. Power resumes, fan is active, but the screen does not turn itself back on and the system appears to be completely nonresponsive. I have to hold the power button and force it to turn off before I can use it again.

Has anyone had similar trouble?

---

### Post by RedMars on 2005-06-13
Yes, I have the same problem with my ASUS W3N notebook. I suspect it is caused by buggy ACPI implementations in the notebook, the Linux kernel or both...

---

