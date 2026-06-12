---
title: "Performance problems on laptop when powered"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by -NabLa- on 2006-11-14
This is a bizarre one. I have a Sony VAIO VGN-FS285M, with Kubuntu Edgy final installed. When plugged, the performance is very poor compared to that on Dapper: 3D and video are very choppy.

However, when unplugged, and running at 800 MHz, the perfomance is back to what it used to be when in Dapper: just great.

Any ideas?

---

### Post by -NabLa- on 2006-12-08
any ideas? yes? no?

---

### Post by zgornel on 2006-12-08
What happens if it is unplugged and running at full speed ?

---

### Post by -NabLa- on 2006-12-19
Sorry for taking so long, zgornel, I've been on holidays.

Laptop's performance when unplugged is just perfect, at full or low speed. Obviously the battery goes down really quick, and the processor performs faster if I set it up to max speed (1.7 GHz).

I also found out that if I boot with acpi disabled (acpi=off as a kernel parameter in grub), laptop's perfomance is as it should be as well. So this is probably an acpi issue.

The issue is only present when laptop is powered and ACPI is enabled at boot time.

Edit: I forgot to add another strange effect. If I fire up an app that requires some computing power and I let it run (like playing an MP3 in amarok), performance is good again! but as soon as I stop that process performance is crap. For the record, the CPU is set to "performance" on the power manager when laptop's powered. I get exactly the same behaviour if I set CPU to "powersave" (only difference is that CPU is running at 800 MHz). It seems to ignore any of the CPU dynamic modes: it just stays at max speed with crap performance. It doesn't ignore the dynamic mode when laptop's running on batteries.

I tried compiling by hand kernel 2.18.3, and the same thing happens.

This happens when managing acpi thru POWERNOWD (which is Ubuntu's default) or POWERSAVED. I prefer the last since it can manage screen brightness, but apart from that, they work the same to me.

---

### Post by zgornel on 2006-12-20
Killing the powernowd daemon solves the problem or only the acpi=off option solves it ?If killing the daemon does solve the problem, simply kill it when plugged and run it when unplugged.

---

### Post by -NabLa- on 2006-12-21
thanks, zgornel.

No, killing the daemon still yields the same results. Only difference is that screen brightness dimming doesn't work. Apart from that, with the daemon killed, if I unplug the laptop performance is good, if I plug it again performance is poor.

Edit: when I say killing, I mean /etc/init.d/powersaved or powernowd stop

---

### Post by -NabLa- on 2007-01-04
OK, solved, if someone has this problem they have to boot the kernel passing "nolapic noapic" to the kernel. Best tried first in grub (by editing the command line parameters of a given menu entry pressing "e" at boot time), and if it works for you, add it to /boot/grub/menu.lst

As an example, my grub entry would be:
```
title           Kubuntu
root            (hd0,5)
**kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda2 ro splash live *noapic nolapic***
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

Careful when upgrading kernel... those settings might disappear.

---

