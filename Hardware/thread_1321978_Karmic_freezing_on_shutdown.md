---
title: "Karmic freezing on shutdown"
date: 2009-11-10
forum: Hardware
---

### Post by otkaz on 2009-11-10
I just got a new laptop hp elitebook 8530p installed karmic 64bit on it. Installed the ati proprietary drivers and it would freeze on boot so I added the option acpi=ht to grub. Boots fine now and works great but when I shutdown it gets to system will now halt and freezes there till I hold down the power key. I downloaded the apm package from the repo but not sure how to configure it. also I have no battery indicator which I expected but is there anything I can do about it? How do I get apm to run my power management features? or is there a better option then apm to get shutdown and battery indicator working again? I would like to stick with the ati driver but I guess I dont have too if there is no other way to fix these issues.

---

### Post by apocalypse80 on 2009-11-10
Well everything works for me, but I fixed the ati driver differently.

For starters I booted to root terminal and ran "aticonfig --initial", followed by "aticonfig --acpi-services=off".
It threw an error message requiring me to manually edit xorg.conf, can't remember the error exactly.
After that I repeated the commands and it just worked, *without* touching grub.

I'm guessing that will also fix your other problems, since all are related to power management.

---

### Post by NexusZA on 2009-11-12
> **otkaz said:**
> I just got a new laptop hp elitebook 8530p installed karmic 64bit on it. Installed the ati proprietary drivers and it would freeze on boot so I added the option acpi=ht to grub. Boots fine now and works great but when I shutdown it gets to system will now halt and freezes there till I hold down the power key. I downloaded the apm package from the repo but not sure how to configure it. also I have no battery indicator which I expected but is there anything I can do about it? How do I get apm to run my power management features? or is there a better option then apm to get shutdown and battery indicator working again? I would like to stick with the ati driver but I guess I dont have too if there is no other way to fix these issues.

If you just run sudo aticonfig --initial it will throw an error about there not being an Xorg file. You need to actually run:

```

sudo aticonfig --initial -f

```

Once you have forced the ATI drivers to create an Xorg file, you can also force them (just to be sure) to use the new Xorg file by running:

```

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1 

```

THEN! You can now inform the graphics card that you do not want to use its power management, which is what is causing the boot and shutdown problems, by running:

```

sudo aticonfig --acpi-services=off

```

Good luck and hope that helps :)

---

### Post by otkaz on 2009-11-13
> **NexusZA said:**
> If you just run sudo aticonfig --initial it will throw an error about there not being an Xorg file. You need to actually run:

```

sudo aticonfig --initial -f

```

Once you have forced the ATI drivers to create an Xorg file, you can also force them (just to be sure) to use the new Xorg file by running:

```

sudo aticonfig --input=/etc/X11/xorg.conf --tls=1 

```

THEN! You can now inform the graphics card that you do not want to use its power management, which is what is causing the boot and shutdown problems, by running:

```

sudo aticonfig --acpi-services=off

```

Good luck and hope that helps :)

Worked great thanks!

---

