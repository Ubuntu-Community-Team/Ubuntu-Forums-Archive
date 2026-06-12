---
title: "Problems with ACPI on BenQ Joybook S73U"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by Seb1982 on 2007-04-09
Hi everyone!

I bought a new notebook a few days ago (BenQ Joybook S73U) and installed Ubuntu 6.10.

What i did not expect were problems with the ACPI functionality. Actually there are the following symtoms:

* When trying to shut down the system the computer does not turn off in the end. This means i have to hold the power button for a few seconds.
* Same problem with suspend to disc mode. Saving data works perfectly but the system does not shut down.
* The computer is able to enter standby mode but does not wake up.

:( :( :( !!!

I already tried to fix my ACPI implementation by editing and recompiling my DSDT file. But due to the fact that 23 warnings were returned i didn't have the heart to edit the file manually.

Another solution i found was adding 'acpi_os_name=\"Microsoft Windows\" acpi_serialize' to my menu.lst in GRUB. But this had no effect.

Does anyone know what might be wrong?

Thanks

Seb

---

### Post by Seb1982 on 2007-04-10
Due to the fact hat noone was able to help me i tried to edit the dsdt.dsl file myself. From 23 errors in the beginning there're now only two left. But i did not find a solution so far.

My computer returns this when compiling the file:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20060608 [Jun 29 2006]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  1146:             Method (_OSC, 5, NotSerialized)
Warning  1075 -                        ^ Reserved method has too many arguments (_OSC requires 4)

dsdt.dsl  1162:                             And (CAPB, 0xFFFFFFFC)
Warning  1104 -                                     ^ Result is not used, operator has no effect

ASL Input:  dsdt.dsl - 5135 lines, 180028 bytes, 2007 keywords
AML Output: dsdt.aml - 18210 bytes 570 named objects 1437 executable opcodes

Compilation complete. 0 Errors, 2 Warnings, 0 Remarks, 156 Optimizations
```


If anyone out there has ever edited anything by hand, pleeeaaaase help me!

Seb

---

### Post by Seb1982 on 2007-04-10
A summery of what i did:

```
sudo cat /proc/acpi/dsdt > dsdt.dat
iasl -d dsdt.dat
```

After that i tried to get rid of the compiler warnings. I comented out the second warning and irnored the first one. Next step:

```
iasl -sa dsdt.dsl
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u -k all
```

Shutting down still doesn't work. I there is any effect it is that it seems that the LED are more active when trying to wake the computer up from standby.

Does anyone of you have exprerience with updating the DSDT file?

Thanks

Seb

---

### Post by MrYoda on 2007-04-16
Hi,

were you able to solve the ACPI problems you encountered with the S73U?
I'm planning on buying the book and I too would like to run Ubunutu.

---

### Post by magicwind on 2007-05-01
Hi.  I have a Benq S73G laptop, and i'm suffering the same problem.  Anyway, I have tried FC6 and Ubuntu Feisty, but none seems to work correctly regarding poweroff.  I am wondering why Windows could take care of this problem but linux doesn't.  Is it a bug of linux, or a deficit in the hardware?

---

### Post by Pankrat on 2007-06-06
I have the same problem here with a BenQ Joybook S73U.

This corresponds to the following bug I think: [https://bugs.launchpad.net/linux/+bug/43961]("https://bugs.launchpad.net/linux/+bug/43961")

---

### Post by herrisan on 2007-07-12
Hello everyone,

there is a bugthread on kernel.org dueing to this problem.

[http://bugzilla.kernel.org/show_bug.cgi?id=8549](http://bugzilla.kernel.org/show_bug.cgi?id=8549)

The bug is already assigned, but unfortunately there is still a lack of information.

"Please attach the acpidump output and the content of /var/log/message."

Maybe someone could upload the files.

regards,
chris

---

