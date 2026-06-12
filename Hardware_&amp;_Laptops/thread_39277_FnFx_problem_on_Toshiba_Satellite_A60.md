---
title: "FnFx problem on Toshiba Satellite A60"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by der_kaiser on 2005-06-04
I've installed the fnfxd and fnfx-client on my Toshiba Satellite A60.
The installation seems to end well, without errors. But when I run the fnfxd module, it gives me this message : 

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).


I've checked on Synaptic, nad the ACPI seems to be installed on my laptop.

Can anyone help me?

---

### Post by Skroob on 2005-06-04
[QUOTE=der_kaiser]I've installed the fnfxd and fnfx-client on my Toshiba Satellite A60.
The installation seems to end well, without errors. But when I run the fnfxd module, it gives me this message : 

fatal error: Could open /proc/acpi/toshiba/keys.

Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).


I've checked on Synaptic, nad the ACPI seems to be installed on my laptop.

Can anyone help me?[/QUOTE]
 Do you have toshiba_apci loaded?  Check the output of lsmod.

---

### Post by der_kaiser on 2005-06-04
I've checked lsmod and toshiba_acpi isn't loaded...
But sony_acpi does !!!!!!!

And when I try to modprobe toshiba_acpi it tells me : 

FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.10-5-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

---

### Post by Skroob on 2005-06-05
Doesn't look good:

> Another important note: This driver does not work on all Toshiba laptops, particularly those models which seem to have a BIOS or other firmware which was not developed by Toshiba itself. New reverse engineering work will have to be done on these machines, or Toshiba will have to disclose the necessary details. The error you will see in this case is:

$ modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi
(.../kernel/drivers/acpi/toshiba_acpi.ko): No such device

The information on this page is only applicable to the latest version of the driver. 


Source: [http://memebeam.org/toys/ToshibaAcpiDriver](http://memebeam.org/toys/ToshibaAcpiDriver)

---

### Post by der_kaiser on 2005-06-06
I've already read this page, but I still have hope to make this working (especially the key for switching between LCD screen and CRT or multimedia projector). 

Is there any other way to make these keys working?

---

### Post by der_kaiser on 2005-06-07
Really no idea for how to switch between the LCD screen and a multimedia projector?

---

### Post by Skroob on 2005-06-07
I saw on a toshiba list someone recommend this url to a user with the same error.  Maybe it will be of use to you.

[http://sourceforge.net/projects/omke](http://sourceforge.net/projects/omke)

---

