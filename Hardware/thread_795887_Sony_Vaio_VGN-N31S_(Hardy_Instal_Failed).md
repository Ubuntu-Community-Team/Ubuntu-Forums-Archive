---
title: "Sony Vaio VGN-N31S (Hardy Instal Failed)"
date: 2008-05-15
forum: Hardware
---

### Post by victor9098 on 2008-05-15
Hi All,

Just thought I would post for anyone else with the same laptop.

I have used both 7.04 & 7.10 on this machine without any trouble, Ubuntu has been dream, compiz and everything else has worked perfectly.

But sadly I have not been able to upgrade to 8.04 Hardy Heron, there seems to be a problem with my 'ACPI', the problem has been filed at launchpad and you can get full details here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222864](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/222864)

Really hope this is sorted soon! On the plus side on my 3 year old Toshiba Equium EA60-199  8.04 installed first time. Compiz does not work but that is not an issue as everything else seems to be working fine.

---

### Post by ohnonotagain69 on 2009-03-30
This is probably too late for you now...but for others out there waiting for answers that never come, try installing with the -noacpi switch, then switching it back on again once everything works fine.

To turn ACPI back on, just edit the /boot/grub/menu.lst

ie.

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic **acpi=off noapic nolapic**
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=blah  ro quiet splash **acpi=off noapic nolapic**
initrd		/boot/initrd.img-2.6.24-21-generic

Delete bits in bold.

Hope this helps...

---

