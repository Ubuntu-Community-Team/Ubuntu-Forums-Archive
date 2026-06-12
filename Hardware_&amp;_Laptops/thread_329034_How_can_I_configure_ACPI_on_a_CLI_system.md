---
title: "How can I configure ACPI on a CLI system?"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by le_jawa on 2006-12-31
I've setup a command-line only server at home with Edgy Eft on an old PC I had laying around.  Since it won't receive heavy usage, and I want to keep the electric bill to a minimum here at home, I want to configure ACPI power management on the server to put the system to sleep when it's not in use.

So far, I have installed the following packages:
acpid
acpi
acpi-support
powermanagement-interface

The system is a PIII-450 that does support ACPI, but obviously, it's pre-Y2K.  I set acpi=force on the kernel command line in GRUB, as well as apm=off,  and lapic to force the detection of the APIC.  Looking at dmesg, everything looks fine (as far as I can tell) -- the APIC is detected and acpid is running.   /proc/acpi does exist and is populated, but there is no "thermal" directory and running acpi will complain about that and exit.

Also, power management is configured in BIOS.

That covers everything I can think of at this point, but so far it looks like the system never goes to sleep.  Does anyone here know of more I need to do to configure the system for power management?

Thank you,

Jason

---

### Post by nick4mony on 2007-01-09
Having a related issue.  

Have you seen this interesting advice?
[https://help.ubuntu.com/community/ACPIBattery](https://help.ubuntu.com/community/ACPIBattery)  It's about getting a custom DSDT file.

My differences are: I'm running a CLI-only system on a HP laptop (OmniBook XE3), and after 
```

apt-get install acpid acpi acpi-support    ## but not powermanagement-interface
```

and altering /boot/grub/menu.lst to add
```

kernel ... apm=off apic=force
```

I found three things:
[list]
[*] the 'lapic' option in grub didn't work - message from dmesg - Could not enable APIC!
[*] Another message from dmesg - ACPI: Looking for DSDT ... not found!
[*] The battery status always at 100%
[/list]

---

### Post by nick4mony on 2007-01-09
I should add, I'm using Edgy (server LAMP install) on the laptop.

---

### Post by le_jawa on 2007-01-22
Nick,

Thanks for the link; I'll take a look at that.  As for your messages, here's some  light I can shed on those:

*Could not enable APIC -- sounds like your system either doesn't have an APIC or has one the kernel doesn't recognize.  I'll post a link later to a compatibility list, but I don't remember it right off.
*DSDT not found -- I'm hitting that too.  I'll have to read up from that link you provided.
*Battery -- not sure there.  Probably related to the APIC message.

Anyway, thanks for contributing.  Hopefully I can give you a hand in return.

Jason

---

### Post by IntuitiveNipple on 2007-01-22
I'm using Edgy and investigating suspend/hibernate/resume issues on a notebook.

All the ACPI power control scripts are in **/etc/acpi/**. Suspend/resume parameters are defined in **/etc/default/acpi-support**.

Use  **/etc/acpi/sleep.sh** to suspend. To hibernate use **/etc/acpi/hibernate.sh**.

The scripts in **/etc/acpi/suspend.d/** are executed for suspend/hibernate, and those in **/etc/acpi/resume.d/** when resuming.
The files are named with a leading-number that controls execution priority in the same way as the regular rc.d start files are numbered.

I found removing all the scripts temporarily from **/etc/acpi/suspend.d/** and then adding them back one-by-one helped me identify and solve problems with the suspend/hibernate stage failing.

---

### Post by nick4mony on 2007-01-24
> **IntuitiveNipple said:**
> I'm using Edgy and investigating suspend/hibernate/resume issues on a notebook.

All the ACPI power control scripts are in **/etc/acpi/**. Suspend/resume parameters are defined in **/etc/default/acpi-support**.

Use  **/etc/acpi/sleep.sh** to suspend. To hibernate use **/etc/acpi/hibernate.sh**.

The scripts in **/etc/acpi/suspend.d/** are executed for suspend/hibernate, and those in **/etc/acpi/resume.d/** when resuming.
The files are named with a leading-number that controls execution priority in the same way as the regular rc.d start files are numbered.

I found removing all the scripts temporarily from **/etc/acpi/suspend.d/** and then adding them back one-by-one helped me identify and solve problems with the suspend/hibernate stage failing.

... Quite useful, thanks.

Another thing to do is to see where output is going from these various scripts, or execute them in a console.

Because the system is going to sleep, you may need to (as root) ...
```

/etc/acpi/sleep.sh >/a/file/of/your/choice.txt 2>&1

```
which will capture output into the file specified (alter /a/file/of/your/choice.txt to suit)

You may also have to alter the various resume.d scripts, to get their output to go somewhere sensible (urrgh a slight pain).

---

### Post by nick4mony on 2007-01-24
> **le_jawa said:**
> Nick,

*Could not enable APIC -- sounds like your system either doesn't have an APIC or has one the kernel doesn't recognize.  I'll post a link later to a compatibility list, but I don't remember it right off.


Jason,

Was this an APIC/ACPI specific link?  Or a Ubuntu Wiki link?

---

### Post by le_jawa on 2007-01-27
Nick,

Sorry it took me so  long to get back with this; I haven't been on the forums much lately.  Anyway, I have a couple of links for you:

[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt]("http://www.columbia.edu/%7Eariel/acpi/acpi_howto.txt")

is the "official" place for the FAQ with some info that may help you.  Unfortunately, it seems to be inaccessible right now; I keep getting "Forbidden" messages when I try to access it.  However, Google has a cached copy at 

[http://64.233.167.104/search?q=cache:jSW17bk70UcJ:www.columbia.edu/~ariel/acpi/acpi_howto.txt+acpi+linux+supported+bios&hl=en&gl=us&ct=clnk&cd=1&client=firefox-a]("http://64.233.167.104/search?q=cache:jSW17bk70UcJ:www.columbia.edu/%7Eariel/acpi/acpi_howto.txt+acpi+linux+supported+bios&hl=en&gl=us&ct=clnk&cd=1&client=firefox-a")

(The text may not show up right on that link, but it should still work.)
Try that and see if it has the info you need.  Good luck!

Jason

---

### Post by nick4mony on 2007-03-01
Thanks Jason.

If the cached copy at Google disappears, the Wayback machine is worth a try. [http://www.archive.org/](http://www.archive.org/)

---

