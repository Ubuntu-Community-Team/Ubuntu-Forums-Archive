---
title: "Installation aborted"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Zubenelgenubi on 2009-03-09
Recently aquired nasty virus that compromised windows XP to the extent that the machine regularly shut down without warning. Decided to give Linux a go but all attempts to install alongside XP have failed. When I attempt to reboot as per instructions I recieve the following error messages (even if I try safe mode)

Operation aborted
0.185820  ACPI Aborted because broken padding
1.580468  invalid compressed format (err=2)
1.645307  Kernel panic - not syncing VFS: Unable to mount root fs on unknown wn. block (8,1)

I guess the next step is reformatting the hard drive and flying solo with Linux but am worried the that problem maybe more complex and possibly terminal. 

Any tips?

Tks]

---

### Post by lindsay7 on 2009-03-09
I would be worried about the shut downs with windows, a lot of things could cause that. I am going to look for a post on a similar error code read out and post it for you when I find it.

---

### Post by lindsay7 on 2009-03-09
Not sure this will help at all but there some boot options on the live cd that may tell you somemore.


 Re: Complicated problem with Live CD. (wont boot, error's galore )
I just saw this in another post on a different problem, but maybe this would help.

On the live cd install disk when you start the program, one of the first screens you get has at the bottome a list of f keys (f1, f2 . etc) for alternate startup instructions. on the f key listed for other options, you should get these options:

ok, i went to other boot options, and it has 5 options of ACPI=OFF noapic nolapic edd=on Free Software Only

Maybe one of those options will get you going.

---

