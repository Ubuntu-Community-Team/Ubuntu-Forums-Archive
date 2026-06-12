---
title: "[SOLVED] Won't start up unless holding down a key"
date: 2008-11-13
forum: General Help
---

### Post by wobblyheadedjon on 2008-11-13
When Ubuntu is loading (Ubunto logo, orange status bar) the bar will not progress, nor will it load if I just let it sit there.

any help?

Ubuntu Intrepid Ibex

---

### Post by prshah on 2008-11-13
> **wobblyheadedjon said:**
> When Ubuntu is loading (Ubunto logo, orange status bar) the bar will not progress, nor will it load if I just let it sit there.

What kind of keyboard? USB? Wireless? Bluetooth?

---

### Post by wobblyheadedjon on 2008-11-13
Its a laptop keyboard.

---

### Post by geirha on 2008-11-13
A possible work around in this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247)

---

### Post by wobblyheadedjon on 2008-11-13
looks like that is the sol'n, but I don't know what they mean by "booting w/ nolapic"

Thanks so much for the help so far.  Looks like when i get that part, I'm good to go.

---

### Post by unutbu on 2008-11-13
Along with the boot options mentioned in geirha's post (acpi=noirq, hpet=disable, nolapic), you might also want to try booting with the temporary boot option 'irqpoll'.

See [http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4) for how to boot with kernel boot options. 

If it works, the link above also has instruction on how to make the boot option permanent.

Please keep us posted on how it goes.

---

### Post by wobblyheadedjon on 2008-11-13
Well, i used that link to figure out how to edit the boot temporarily.

Thus far I've added acpi=noirq and nolapic tothe end of the kernel line to no avail

will try the other options and update.  thanks again.

---

### Post by wobblyheadedjon on 2008-11-13
Okay, I failed at the temporary boot thing.  I wasn't pushing b to boot, i was going back and booting w/o the changes.

However, I did it correctly with "nolapic" added and i got an error:
.0376070 BIOS bug, Local APIC #0 not detected!

So I tried again w/ the acpi=noirq, booted 2 times that way, and it worked just fine.

Thanks all!

---

### Post by wobblyheadedjon on 2008-11-13
Added it to the permanent boot file and works like a charm.

once again, thanks.

solved!

---

