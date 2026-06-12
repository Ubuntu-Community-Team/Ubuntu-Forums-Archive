---
title: "Solution: Fix suspend keyboard error"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by Qaz on 2005-05-19
I had a problem with suspend on my laptop. Suspend worked with apm, but after resume the keyboard was "crazy". Pressing a key resulted in a repeted pattern of other characters.

After searching this and other forums I found no working solution. The problem is that the keyboard driver do not reset itself on resume. The ubuntu kernel has almost everything kompiled as modules, except the ps/2 keyboard drivers.

Well, a solution that works for me is to recompile the kernel with i8024 and atkbd as modules. 

I used the ubunto kernel source-package. The drivers is located under devic drivers/input device support/ (using make menuconfig). Change "i8042 pc keyboard controller" and ""AT keyboard support"  to <m> (for module).

Then build the kernel using the steps in [http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto)

Add  i8024 and atkbd to /etc/modules (i8024 first)

Then edit your suspend/resume scripts to rmmod and modprobe these.
For apm my scrip looks like:

03pskey:
```
#!/bin/sh
# Preserve the system clock around suspend/resume.

case "${1},${2}" in
(suspend,*)
    rmmod atkbd
    rmmod i8042
    ;;
(resume,suspend)
    modprobe i8042
    modprobe atkbd
    ;;
esac

exit 0
``` 

It's lookated in /etc/apm/resume.d and /etc/apm/suspend.d/ . It should work if you put it in /etc/apm/event.d instead (and that would be more correct I guess.


It might help someone :).

---

### Post by Zelut on 2005-05-19
Thanks for that post, I'm sure I'll use it in configuring my notebook.  My problem however is the suspend altogether.  If I close my notebook it goes into suspend and will shutdown after being lifted again.  I'm not familiar with the suspend settings but if you have a solution for this I would GREATLY appreciate it.

---

### Post by Qaz on 2005-05-19
[QUOTE=kuyaedz]Thanks for that post, I'm sure I'll use it in configuring my notebook.  My problem however is the suspend altogether.  If I close my notebook it goes into suspend and will shutdown after being lifted again.  I'm not familiar with the suspend settings but if you have a solution for this I would GREATLY appreciate it.[/QUOTE]
 I got suspend to work at all by using apm instead.

I use kernel argument acpi=off apm=on

and disabled the acpid and acpi-support in /etc/inin.d/

I also added apm in /etc/modules/

---

### Post by Zelut on 2005-05-19
could you give me some steps on how to set it up as you've done?  I'm not familiar with suspend or power management under linux at all but I'd sure appreciate a quick HOW-TO if you could.

I've love to be able to close my notebook without it shutting down!

---

### Post by Strife on 2005-05-20
I second. A more in-depth HOWTO would be a good resource for everyone having problems getting ACPI to work... Even us seasoned Linux pros who have simply never used Linux on a laptop up until now :)

---

### Post by Qaz on 2005-05-21
[QUOTE=kuyaedz]could you give me some steps on how to set it up as you've done?  I'm not familiar with suspend or power management under linux at all but I'd sure appreciate a quick HOW-TO if you could.

I've love to be able to close my notebook without it shutting down![/QUOTE]
 I don't know, I'm very far from any power management expert. Until a few weeks ago I had never cared at all (was using gentoo on my laptop, an old install, on wich suspend "just worked". I could write down how it's configured on my machine, but I guess problems with hardware malfunktion after suspend is very case specific.

---

