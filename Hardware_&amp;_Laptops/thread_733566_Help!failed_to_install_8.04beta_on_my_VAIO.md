---
title: "Help!failed to install 8.04beta on my VAIO"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by tulanix on 2008-03-23
I try to install 8.04beta on my VAIO VGN-C22CH,but it can boot from livecd with these error:
[48.077466] ACPI:EC: acpi_ec_wait timeout,status=0,expect_event=1 
[48.077527] ACPI:EC: read timeout,command=128 

After I add "acpi=off",it can boot an install.But it cannot identify my battery.
Can anyone help me to solve this problem?I have used 7.10 for 3 month on my laptop very well before that.

---

### Post by Seeed on 2008-03-29
Same problem here with a Sony Vaio VGN-N31M...
I hope this gets fixed until the final version of Hardy.

---

### Post by father on 2008-03-31
Same problem with VGN-FE41series.

If no ac adapter is present system boots as usual.... You can plug AC immediately after booting process started.

Another method: I've just disable **noapic ** (not the acpi) F6, F6 at boot, and the VAIO is booting as normal.

In both cases the battery was identified by the system (Vendor: Sony Corp, Design  charge: 57,7 Wh)

I hope this helps.

But... (still) there are some problems, eg:  PCI: Failed to allocate mem resource #6:2000@c0000000 

> **tulanix said:**
> I try to install 8.04beta on my VAIO VGN-C22CH,but it can boot from livecd with these error:
[48.077466] ACPI:EC: acpi_ec_wait timeout,status=0,expect_event=1 
[48.077527] ACPI:EC: read timeout,command=128 

After I add "acpi=off",it can boot an install.But it cannot identify my battery.
Can anyone help me to solve this problem?I have used 7.10 for 3 month on my laptop very well before that.

---

### Post by rozhman on 2008-04-02
Same problem with vaio n385e.

---

### Post by IntuitiveNipple on 2008-04-11
Try removing the "quiet" option from the kernel command line. 

If you're using an installed system, do this in /boot/grub/menu.lst and maybe change the default koptions.

For the LiveCD, press "F6" when the menu appears, press "End" to get to the end of the command line, and then use back-space to delete the "quiet" option. Press Enter to continue to boot.

See [bug #191137]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137") "ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet' option is enabled"

---

### Post by rozhman on 2008-04-21
thnx dude

---

