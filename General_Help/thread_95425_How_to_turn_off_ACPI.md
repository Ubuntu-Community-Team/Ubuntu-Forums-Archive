---
title: "How to turn off ACPI?"
date: 2005-11-26
forum: General Help
---

### Post by Megatog615 on 2005-11-26
Ok, I get the errors "Error inserting fan", and "Error inserting thermal". This is obviously due to ACPI not working on my computer(it's rather old). Is there a way to turn it off **after** installation?

---

### Post by crane on 2005-11-26
[QUOTE=Megatog615]Ok, I get the errors "Error inserting fan", and "Error inserting thermal". This is obviously due to ACPI not working on my computer(it's rather old). Is there a way to turn it off **after** installation?[/QUOTE]
 Edit your menu.lst file located at /boot/grab/menu.lst
Just addit to the kernel line like below.

Make it look like this:

title		Ubuntu, kernel 2.6.12-10-k7-smp 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda3 ro [color=blue]noacpi[/color]  quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7-smp
savedefault
boot

I would also check you bios. there may be an option to cut it off there as well.

---

### Post by _bacon_ on 2005-11-29
I just "apt-get remove acpi laptop-mode". Scary but it works.

---

### Post by ryan7107 on 2006-01-04
I tried both suggestions, and no luck. I also tried acpi=off and pci=noacpi. Still get the same two error messages, inserting thermal and inserting fan. Were you guys using 5.10? Maybe I only see these because I not using a boot splash?  They do not seem to be causing any problems, just bug me to no end.  If anyoneknows a solution, I'd be very grateful.

---

### Post by crane on 2006-01-04
You could also try using 
noapic nolapic in your grub line;


kernel /boot/vmlinuz-2.6.12-10-k7-smp root=/dev/hda3 ro noapic nolapic quiet splash

Also have you checked your bios?

---

