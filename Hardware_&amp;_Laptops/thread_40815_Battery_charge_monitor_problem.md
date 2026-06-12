---
title: "Battery charge monitor problem"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by dpacket on 2005-06-10
well I have a problem with the Battery charge monitor, is says always status unknown, my laptop is a toshiba satellite. is there a way to make it work?

---

### Post by blind0wl on 2005-06-21
Can you post the output of dmesg?

Do you have /etc/init.d/acpid running?

Can you post the output of: ```
cat /proc/acpi/battery/BAT1/state
```

Also can you check whether ac and battery are being loaded as modules?
Try: ```

lsmod

```

if their not there type:
```

modprobe ac
modprobe battery
```

If that works, add the two modules ac and battery to your /etc/modules file.

HTH

Blindy

---

### Post by briguy on 2005-06-26
I had the same problem on my Gateway 200x laptop.  It is quite possibly that your laptop model has a buggy DSDT table (Windows is more forgiving than linux which is why it probably works for that OS).  The easiest way to fix it under Ubuntu is to patch the DSDT table via initrd (instructions available [here](http://gaugusch.at/kernel.shtml)  with a DSDT table from [here](http://acpi.sourceforge.net/dsdt/index.php)   .  The Ubuntu kernel is already patched to accept the initrd fix, so you can skip that step.

The only catch is you have to patch the initrd every time Ubuntu updates the kernel, this is easy if you put the last steps into a script that you can run when this happens.  My script looks like this:

mkinitrd -o /boot/initrd.img-`uname -r`
echo -n "INITRDDSDT123DSDT123" >> /boot/initrd.img-`uname -r`
cat DSDT.aml >> /boot/initrd.img-`uname -r`

Hope this helps!

---

### Post by dpacket on 2005-06-26
[QUOTE=blind0wl]Can you post the output of dmesg?

Do you have /etc/init.d/acpid running?

Can you post the output of: ```
cat /proc/acpi/battery/BAT1/state
```

Also can you check whether ac and battery are being loaded as modules?
Try: ```

lsmod

```

if their not there type:
```

modprobe ac
modprobe battery
```

If that works, add the two modules ac and battery to your /etc/modules file.

HTH

Blindy[/QUOTE]
 the Output is 

> dpacket@krypton:~$ cat /proc/acpi/battery/BAT1/state
cat: /proc/acpi/battery/BAT1/state: No such file or directory
dpacket@krypton:~$


---

### Post by luca_linux on 2005-06-27
Load toshiba*.ko modules. Check the exact name before typing the command "modprobe".

---

