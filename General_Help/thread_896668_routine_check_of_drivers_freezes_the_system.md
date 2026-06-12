---
title: "routine check of drivers freezes the system"
date: 2008-08-21
forum: General Help
---

### Post by wolandt on 2008-08-21
hi, i have toshiba satellite a60 laptop. after 50th booking the system does the routine check of drivers and it freezes after several seconds. i reinstalled ubuntu and it happens again. what can does the problem? alternatively how to make ubuntu to stop doing the checks?
waiting for help...
wolandt

---

### Post by Thingymebob on 2008-08-21
Its a routine check of drives (filesystems) are you sure the system is hanging (is the hdd ligh active?) It can take a while particularly if the system wasn't shut down properly or unlean filesystems

When you grub screen pops up press e to edit the boot option and remove the words **quiet** and **splash**. You'll then see all the system messages as you machine boots and a progress indication of the filesystem checks.

you need to edit your fstab to disable the checks, but it isn't advised

---

### Post by wolandt on 2008-08-26
Thanks for the response, the system is definitely hanging. i do not quite understand how to edit the boot options,can you explain it better? what kind of screen pops up do you mean? can you also explain how to edit fstab? i know it is not recommendable but possibly is my only option to make the machine working properly.

---

### Post by aminalid on 2008-09-09
Hi,
I have the same problem with the same laptop (fresh installation of Ubuntu Hardy), hard drive is active (indicator always on, not blinking) but leaving the system for 3-4 hours didn't change anything. The percentage of routine check is not updated after 3%. And some glitches appear on the boot splash screen.

I can press Esc to cancel the procedure during the first seconds, and boot normally.

Does this mean that i have a hard drive problem?
Is there a way to preform full disk check after booting?

Thanks!

---

### Post by Thingymebob on 2008-09-09
Sorry been away for a couple of weeks.

try adding noapic to your boot options.

(at boot when you see the message)
***Grub Loading stage 1.5 ....***
press escape

press **e** to edit the default boot option,
edit the kernel line and add ***noapic*** to the end of it

If that works then you will need to edit your /boot/grub/menu.lst so as the option is always passed
```

gksudo gedit /boot/grub/menu.lst

```

find the section that reads
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

```

add **noapic** after the ***'defoptions='*** part

save and close

now update grub:
from a terminal type:
```

sudo update-grub

```

---

### Post by aminalid on 2008-09-12
Adding no noapic improved the situation a bit, the check advanced now up to 20 - 30 % but then hang again. I didn't leave it for hours though.

I tried to remove Quiet and Splash from the kernel line in grub, and it worked. The check passed in a small amount of time.

I removed noapic from the kernel line again, and now will wait till another routine check will be forced (i don't know how to force it manually)

So basically i suspect that removing the Quiet and Splash fixed this problem...

---

### Post by aminalid on 2008-09-17
> **aminalid said:**
> 
So basically i suspect that removing the Quiet and Splash fixed this problem...

Ok, the check is working without the noapic, removing Quiet and Splash from the kernel line did solve the issue for me.

---

