---
title: "LiveCD shuts off my laptop"
date: 2009-11-12
forum: Hardware
---

### Post by Ciylana on 2009-11-12
When I boot from the ubuntu x86_64 livecd (or gentoo or freebsd actually) the laptop will run just fine for a random amount of time then shut itself off. No warnings, temp never goes over 40-50c (I have been watching, my first thought), just shuts off like I held the power button down. Booting with noapic has no effect.

The weird thing is windows runs just fine for hours and hours, but linux for no more than 30 mins, I cant even get through an install.

Any ideas?

---

### Post by Bunnybugs on 2009-11-12
> **Ciylana said:**
> When I boot from the ubuntu x86_64 livecd (or gentoo or freebsd actually) the laptop will run just fine for a random amount of time then shut itself off. No warnings, temp never goes over 40-50c (I have been watching, my first thought), just shuts off like I held the power button down. Booting with noapic has no effect.

The weird thing is windows runs just fine for hours and hours, but linux for no more than 30 mins, I cant even get through an install.

Any ideas?


Did you try to install with Wubi.exe from windows? just see what happens than;)

Wubi doesn't edit your partitions... it just creates a file that Ubuntu checks like it's hard drive!

---

### Post by Ciylana on 2009-11-12
> **Bunnybugs said:**
> Did you try to install with Wubi.exe from windows? just see what happens than;)

Wubi doesn't edit your partitions... it just creates a file that Ubuntu checks like it's hard drive!

I want to remove windows completely. I don't use it.

---

### Post by wojox on 2009-11-12
Try turning off apm: [https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

Windows has full support for acpi, that's why there's no problem there.

---

### Post by Ciylana on 2009-11-12
> **wojox said:**
> Try turning off apm: [https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

Windows has full support for acpi, that's why there's no problem there.

Will the systems fans and cpu freq scaling still work, or could it fry my system>
Thanks.

---

### Post by Ciylana on 2009-11-12
Also, another quick question. Does that mean Linux doesnt have full support for acpi?

---

