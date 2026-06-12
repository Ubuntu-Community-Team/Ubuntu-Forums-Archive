---
title: "Slow startup after upgrading from hardy to ibex"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by dasistwas on 2008-12-17
Hi,

after upgrading from hardy to ibex, following delay occurs during boot time (dmesg > dmesg.txt):
```
[   15.306277] NET: Registered protocol family 17
[   87.752370] ACPI: WMI: Mapper loaded
[   88.762082] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
```

I am on a Mac Pro 8 core. Any help would be greatly appreciated.

Best regards,
David

---

### Post by joff13 on 2008-12-17
in the grub menu, edit the line (press e) you want to boot, delete splash and quiet so during boot sequence you're able to see what's going on.

perhaps you can identify the step that get stuck

---

### Post by dasistwas on 2008-12-17
Thanks for this hint. So I did what you told me to do and realized, that startup stopped long time during "Configuring network interfaces...."

So I looked again in the forums and discovered that I had to delete everything from /etc/network/interfaces.

Now everything is perfect.

Thank you!
David

---

### Post by AlanR8 on 2008-12-17
I've always found it best to back up my files and do a complete reinstall....

---

### Post by joff13 on 2008-12-17
> **dasistwas said:**
> Thanks for this hint. So I did what you told me to do and realized, that startup stopped long time during "Configuring network interfaces...."

So I looked again in the forums and discovered that I had to delete everything from /etc/network/interfaces.

Now everything is perfect.

Thank you!
David

Good news :D  ):P 
Cheers

---

### Post by sandy8925 on 2008-12-17
Yeah but it takes a lot of time and effort. What he did was way faster and easier.

---

