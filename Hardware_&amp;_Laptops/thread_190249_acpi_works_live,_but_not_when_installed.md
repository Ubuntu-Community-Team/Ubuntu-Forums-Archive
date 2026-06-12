---
title: "acpi works live, but not when installed"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by theory_prof on 2006-06-06
Riddle me this: Before I installed the live CD acpi work quite well: There is a directory /proc/acpi with all kins of battery information and so forth, and the battery monitor 
show correctly whether the machine is plugged in or not.

NOW: After I install Ubunto to my hard drive and the do a regular boot (i.e now not
from the live CD, but from the had drive) then there is no acpi support whatsoever! 
No /proc/acpi and the battery symbol reports incorrectly.

The question is: How can it be that when I try the live CD this feature works fine
(proving that this feature can work in principle) and the fron teh hard drive it does not work?
Is there a difference when you install?

---

### Post by blip on 2006-06-06
This may or may not help but I had a similar problem when I was trying to do a fresh install of xubuntu on my laptop.  Under the live CD my PCMCIA ethernet adapter was automatically configured but when I installed xubuntu on to the harddrive it wasn't.  Now I'm sure I could have manually set it up, but the problem irritated me so I tried installing from the alternate (non-live) ISO and it worked perfectly.

As for what caused this problem... And if it is at all related to yours... I can't really say.  :cool:

---

### Post by theory_prof on 2006-06-08
Thanks.

First, let me say that for Dapper Drake the install CD and the live CD are one and the same for PC desktop.... You first load the live CD and then the installer is 
there on your live desktop as a clickable icon.

Now, I finally found the problem. There is a checksum issue with ACPI not allowing the kernel to enable ACPI support for this machine, the ACER C100 travelmate. The live CD  seems to have some workaround which the installed version does not. 

There is a patch availble which might solve the problem., but it looks a bit complicated. 
See [http://gentoo-wiki.com/HARDWARE_Acer_Travelmate_C100](http://gentoo-wiki.com/HARDWARE_Acer_Travelmate_C100) for all the gory details.
You would have to modify one file in the kernel source and then recomile and hope this all does compile...

It's certainly not for humans, unless you are a OS specialist ;-)

Perhaps, this "for humans" distribuion could have this patch available in future releases...?
Maybe Neson Mandela can advocate...

---

### Post by theory_prof on 2006-06-08
BTW, which install CD exactly do you mean....? The one called "server CD"...

---

