---
title: "Problems with Toshiba Satelitte L series"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by dabear on 2005-06-10
I've been a user of linux on my laptop for a while now. Almost everything has gone great, except for one thing- the acpi. My machine has a phoenix bios, and as I have both read and experienced my self, this causes some problems. Ubuntu is on a dual boot with windows xp home (came with the pc) where the battery monitor behaves correctly. 
 in ubuntu, the gnome battery charge monitor only shows "system is running on battery power. Battery power is unknows" (or someting like that). 
So now I hope someone out there could help me out? What to do?

---

### Post by az on 2005-06-10
Does apm work?

---

### Post by dpacket on 2005-06-10
I have the same laptop, everything works fine except the battery status  :neutral:

---

### Post by dabear on 2005-06-11
[QUOTE=azz]Does apm work?[/QUOTE]
This model is very new, so it doesn't have apm, only a buggy (but working, in windows xp) apci.

---

### Post by dabear on 2005-06-19
Ok, I am bumping ths thread 'cause I really need this to work. 
I've now tried to patch the kernel with acpi4linux, but it just says the patch is already applied. So I guess the battery monitor mode isn't available for me:neutral: 

Please, if anybody has any idea at all, or has some relevant links I could visit to get acpi working, come with them :roll:

---

### Post by luca_linux on 2005-06-19
Is there any error in dmesg?

---

### Post by dabear on 2005-06-19
Dmesg throws alot out to the console; not sure what I should be looking for..

---

### Post by luca_linux on 2005-06-19
It looks like being good.
Are you sure you laptop doesn't have a smart battery as some Acer?

---

### Post by dabear on 2005-06-19
[QUOTE=luca_linux]It looks like being good.
Are you sure you laptop doesn't have a smart battery as some Acer?[/QUOTE] 
Sorry, but please explain what you mean by «a smart battery». 

The battery monitor in the preinstalled windows xp home OEM edition works, so I'm sure it **can** be possible in linux too. Only, I don't know how, and google-ing for many days haven't helped me a bit.

I've tried installing acpid, but it just comed out with the message
```

root@UbuntuLaptop:/home/bjorninge # acpid
acpid: can't open /proc/acpi/event: Device or resource busy

```

Also, /proc/acpi/ac_adapter and /proc/acpi/battery shows out empty.

---

### Post by luca_linux on 2005-06-19
[QUOTE=dabear]Sorry, but please explain what you mean by «a smart battery». 

The battery monitor in the preinstalled windows xp home OEM edition works, so I'm sure it **can** be possible in linux too. Only, I don't know how, and google-ing for many days haven't helped me a bit.

I've tried installing acpid, but it just comed out with the message
```

root@UbuntuLaptop:/home/bjorninge # acpid
acpid: can't open /proc/acpi/event: Device or resource busy

```

Also, /proc/acpi/ac_adapter and /proc/acpi/battery shows out empty.[/QUOTE]
 [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/)

Anyway, if I'm not mistaken, it should be a kernel module that enables the support for Toshiba laptops...search for it in /lib/modules/your_kernel_version/ and then try to load it with modprobe.

---

### Post by dabear on 2005-06-19
Yes, I know. I've tried that already, but since my latop has a phoenix bios and not a toshiba native, those two files (toshiba.ko and toshiba_acpi.ko) won't work
```

root@UbuntuLaptop:/home/bjorninge # modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.10-5-686/kernel/drivers/acpi/toshiba_acpi.ko): No such device
root@UbuntuLaptop:/home/bjorninge # modprobe toshiba
FATAL: Error inserting toshiba (/lib/modules/2.6.10-5-686/kernel/drivers/char/toshiba.ko): Input/output error
root@UbuntuLaptop:/home/bjorninge #


```
How do I then find out if the I have a smart battery, and if the latest patch at that page will work?

---

### Post by snop on 2005-06-20
Hi,

> How do I then find out if the I have a smart battery, and if the latest patch at that page will work?

Download the file at [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/) as luca_linux pointed. Read the README and see if your model is listed as a supported one.

You can also check your Windows control panel->system->hardware->device administration and see if there is something like "Smart Battery Driver" elsewhere. I own an Acer Travelmate 4000 an there's one.

You can also browse/search the [acpi mailing list](http://sourceforge.net/mailarchive/forum.php?forum=acpi-devel)  for some more information.

SnOp

---

### Post by dabear on 2005-06-20
[QUOTE=snop]Hi,



Download the file at [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/) as luca_linux pointed. Read the README and see if your model is listed as a supported one.

You can also check your Windows control panel->system->hardware->device administration and see if there is something like "Smart Battery Driver" elsewhere. I own an Acer Travelmate 4000 an there's one.

You can also browse/search the [acpi mailing list](http://sourceforge.net/mailarchive/forum.php?forum=acpi-devel)  for some more information.

SnOp[/QUOTE]
Thank you, I found that my toshiba satelitte series L laptop wasn't listed, but I did actually have a "smart battery". I am going to try the patch in the evening, but will it work on other than those acer laptops? Hope so..

---

### Post by dabear on 2005-06-20
Okey, so I've started with installing the intel iasl-compiler. But to use the iasl command, I've got to add "/usr/src/intelCompiler/acpica-unix-20050513/compiler" to $PATH . I've tried editing "/home/bjorninge/.bash_profile ", changing one of the last lines to 

PATH=~/bin:"${PATH}:/usr/src/intelCompiler/acpica-unix-20050513/compiler"
but it doesn't seem to work. Sorry for asking so much, but how to add to  $PATH?

---

