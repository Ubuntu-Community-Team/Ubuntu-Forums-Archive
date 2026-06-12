---
title: "Brightness problem in Ubuntu 9.10 on Acer Extensa 5235"
date: 2010-01-22
forum: Hardware
---

### Post by Robert Vlach on 2010-01-22
Hello Ubunters :-)

I am trying to find a solution for a nasty ergonomic problem on my new laptop Acer Extensa 5235 running Ubuntu 9.10. It has Intel GMA 4500M graphic card inside with 32/64/128 MB shared memory and I also had problems with black screen during and after installation, that were solved by adding i915.modeset=0 boot option. The present problem is this:

**I cannot set the screen brightness, nor in Ubuntu, nor using laptop's Fn keys.** By default, Ubuntu sets brightness to maximum value and it cannot be adjusted, which is very unpleasant and after few hours of work it gives me a head-ache and my eyes are burning.

After pressing the brightness Fn keys in Ubuntu, the brightness bar appears, but no matter the value, screen brightness won't change anyway. Besides, the brightness Fn keys are switched. By pressing more it decreases the bar value and vice versa.

The only way to adjust brightness is by pressing Fn keys in GRUB (obviously an BIOS functionality, keys are still switched, but working). But after one restart, Ubuntu sets the brightness back to maximum value.

Is there a way to fix Ubuntu brightness support on my laptop OR at least change the default brightness value to more pleasant level?

Thanks in ahead for your advice,

Robert

---

### Post by jayamohan on 2010-01-28
I too had this problem. After searching for more than 1 day I came across a post that suggested to append acpi_osi='Linux' to the kernel boot options in grub. Suggestions are to edit the grub screen (hitting the key 'e' when grub loads) for the corresponding kernel and append acpi_osi='Linux'. There are chances that bright and dim controls could be reversed (function-down arrow key combination could increase the brightness than dimming). Googling acpi_osi=Linux would give plenty of information. If it works dont forget to make it permanent by editing /etc/default/grub for grub2 or menu.lst for Grub. Hope this solves your issue (it did for me). Happy ubuntuing :eek:

---

### Post by Robert Vlach on 2010-01-28
Thanks to you, jayamohan, I am one step closer to solution! :-)

I have tried and applied your solution and Fn keys are now **working** in Ubuntu (in reversed order though).

The ultimate problem is that Ubuntu won't remember brightness setting after restart (yes, I have edited and updated grub settings).

Any idea, how to make Ubuntu remember the brightness settings? I have googled it but without success...

Robert

---

### Post by veda87 on 2010-01-28
I don't know about acer but the smae problem exists in dell 1555 too.. 

If you need, you can better check this link[http://ubuntuforums.org/showpost.php?p=7541070&postcount=24]("http://ubuntuforums.org/showpost.php?p=7541070&postcount=24")

It might help you...

---

### Post by Robert Vlach on 2010-01-28
Thanks veda, but that solution is probably way over my Ubuntu/Linux experience. I am new to all this, you know ;) I am afraid that if anything goes wrong in that process I might not be able to repair it... Thank you for your suggestion, I hope to find something easier sooner or later... Robert

---

### Post by drdanielfc on 2010-01-28
I'm using mint but system>preferences>power management has a screen brightness setting that works for me

---

### Post by Robert Vlach on 2010-01-29
Heureka! It works for me too, you're an angel :KS

---

### Post by drdanielfc on 2010-01-29
haha i always go through all the settings on a new install :-p

---

### Post by gbrubal on 2010-06-25
Hi, im sorry to bring this back from the dead, but im having the original problem posted here on a pavillion dv3 with intel gma 4500HD (running karmic) and the solutions did not work for me. Not the grub mod, nor the power management preference. Is it some driver at fault here? What to do?

Thanks in advance

---

