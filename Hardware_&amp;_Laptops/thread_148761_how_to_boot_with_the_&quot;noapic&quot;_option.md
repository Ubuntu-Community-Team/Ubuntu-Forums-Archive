---
title: "how to boot with the &quot;noapic&quot; option?"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by techrush on 2006-03-22
there is a bug with my BIOS and apic in linux. my mahcine will periodically lock up unless i boot with the option noapic. ive done this before on other distros but it has been a while. i cant seem to remember where to add it to /boot/grub/menu.lst 

would appreciate if someone could jog my memory on how to add this boot option. thanks!

---

### Post by audax321 on 2006-03-22
There should be a line similar to this:
```

kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet splash
```


It miay be different for your kernel, but you should be able to just put noapic at the end so it looks like this:
```

kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet splash noapic
```

---

### Post by techrush on 2006-03-22
tried adding it there and it hangs....says its waiting for root file system........then nothing :(

---

### Post by audax321 on 2006-03-22
I did a Google search for grub noapic and came across this site:
[http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

It's for some double clock speed problem, so I'm not sure if it will work for you, but you might need the combination of options they have. Something like #3 (noapic acpi=off) might work?

The relevant section says:
```

If you have installed Ubuntu... If you have installed Ubuntu and you want to see if it works for you:

Turn on your computer and keep pressing "ESC" until you get to the GRUB menu.

Select your kernel with your keyboard arrows (DO NOT PRESS ENTER) and Press "e". Then you will see 3 lines:

root (hd0,0)
kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash
initrd	/boot/initrd.img-2.6.12-10-k7

Select the line which begins with the word "kernel" and press "e" to edit it.

Add one [ONLY ONE i.e. only 1) or only 2) ] of the following things at the end of the line:

1) noapic nolapic

so that it will look like this: kernel /boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapic

OR

2) noapic acpi=noirq
OR
3) noapic acpi=off
OR
4) noapictimer
OR
5) noapictimer irqpoll
OR
6) noapic acpi=off
OR
7) noapic acpi=noirq nolapic

Then get off the text field and press "b" to boot the kernel.

See if it works.

If Ubuntu DOESN'T boot, it hangs or you can't use your internet connection just reboot and follow the instructions again but try with option 2) or 3), 4), etc. until you solve your problem.

When you find the boot options which work for you [ 1), 2) or 3), etc. ] you have to set them permanently (because the options you have jsut set will only last until you reboot).

Follow the first part of the guide (the one about Ubuntu 64 bit) and put the options which work for you (e.g. "noapic nolapic") instead of "no_timer_check".

```

After you find out what options work, you can edit the menu.lst and add them as before to make them permanent.

---

### Post by techrush on 2006-03-22
weird....the noapic option works fine on the standard 386 kernel but it causes the 686 kernel to hang. geuss i will wait for a new kernel to come out and try again and just run the 386 kernel for now. is it that much of a performance hit to not use 686 kernel when your processor is 686 ?

---

### Post by audax321 on 2006-03-22
I doubt it since most of the software installed is pre-compiled from the repos. But, I think the 386 kernel has some kind of memory limitation (maybe a 1 GB?) where it just ignores anything higher.

---

