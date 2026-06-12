---
title: "ASUS ACPI Support problem"
date: 2009-08-31
forum: Hardware
---

### Post by *SnZ on 2009-08-31
Hello,

I have problem with acpi support in my notebook.

Asus A6000 Series : A6Km (A6q00km)
Ubuntu 9.04 (2.6.28-15-generic)

I have tryed changing DSDT, with: [http://acpi.sourceforge.net/dsdt/view.php?id=671](http://acpi.sourceforge.net/dsdt/view.php?id=671)  , but no luck...

I did:

sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u -k $(uname -r)

Then reboot, without acpi=off, and screen froze.

I can start with acpi-off parameter, but this is not sollution.

Please help me!

---

### Post by Yellow Pasque on 2009-08-31
Doesn't Asus claim to support Linux? You might try getting support from them.

---

### Post by *SnZ on 2009-08-31
Tryed, searchung at Asus boards, also maked topic but no luck with this acpi.

Please someone reply


//NVM SOLVED!!

---

### Post by Tares on 2009-12-19
Can you write here how you solved this problem ?

---

