---
title: "Bluetooth on Toshiba Sattelite A200"
date: 2008-05-09
forum: Hardware
---

### Post by dkrig on 2008-05-09
Hello.

I'm running Ubuntu 8.04 (hardy) on my notebook and having troubles using Bluetooth device

lshw output:
```
    description: Notebook
    product: Satellite A200
    vendor: TOSHIBA
    version: PSAECE-01Q00ERU
```

When I'm trying to run *toshset* I get this error message:
```
$ sudo toshset 
required kernel toshiba support not enabled.
```

I tried to add toshiba to linux kernel by this failed too
```
$ sudo modprobe toshiba
FATAL: Error inserting toshiba (/lib/modules/2.6.24-16-generic/kernel/drivers/char/toshiba.ko): No such device
$ sudo modprobe toshiba_acpi 
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

```

But both this modules exists:
```
$ modinfo toshiba
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/char/toshiba.ko
description:    Toshiba laptop SMM driver
author:         Jonathan Buzzard <jonathan@buzzard.org.uk>
license:        GPL
srcversion:     B885CD59F96ACE3E75AE5BA
depends:        
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           fn:User specified Fn key detection port (int)

$ modinfo toshiba_acpi 
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/acpi/toshiba_acpi.ko
license:        GPL
description:    Toshiba Laptop ACPI Extras Driver
author:         John Belmonte
srcversion:     6E5478CEC2044193389600F
depends:        
vermagic:       2.6.24-16-generic SMP mod_unload 586 
parm:           hotkeys_over_acpi:uint
parm:           hotkeys_check_per_sec:uint

```

Please help me make bluetooth to work.
This is the only device I cannot run on Ubuntu after migration from Windows Vista.

Thanks

---

### Post by dkrig on 2008-05-09
Ha

looked at kernel messages using *dmesg* and found very interesting thing:
```
[ 2366.639508] toshiba: not a supported Toshiba laptop
```
This log message was added just after I tried *sudo modprobe toshiba* command.

Very strange...

---

### Post by Paresh on 2008-11-04
I'm having the same problem with my Tecra A9.

I am running on Intrepid with kernel version 2.6.27-7

the strange thing is that when I boot into kernel 2.6.24-21, I can switch bluetooth on with
> toshset -bluetooth on
and it all works (detects and pairs with devices, transfers data)

The same command on 2.6.27-7 results in this error message:
> required kernel toshiba support not enabled

anyone know how I can enable this?  I am slightly more avanced than a noob on linux, so any help would be much appreciated.

---

### Post by Ghilteras on 2008-11-08
i have exaclty the same problem

there are no modules of omnibook to use on my 2.6.27-7 intrepid kernel, same thing for toshset cause "required kernel toshiba support not enabled."

so my bluetooth adapter cannot be switched on in ubuntu, the only way to make it visible is to boot into vista (where i can easily switch it on) and then reboot in ubuntu

this workaround works as long as i dont shutdown, after that i have to repeat the workaround (boot vista, reboot ubuntu)

anyone managed to solve this?

---

### Post by Paresh on 2008-12-02
[This link]("http://ubuntuforums.org/showthread.php?t=986075") worked for me

It means compiling modules for the kernel, so only follow this if you are confident

Paresh

---

