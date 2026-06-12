---
title: "Strange HP dv6636nr grub boot problem"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by schwascore on 2008-01-20
I'm having a rather strange issue with GRUB on my HP Pavillino dv6636nr.

I have the proper boot options saved in GRUB, but 90% of the time the first boot fails.  In order to get the system to boot, I follow these steps:

[LIST=1]
[*]Hit' ESC' at the GRUB menu during boot
[*]Hit 'e' to edit the boot options for my default kernel
[*]Hit 'e' to edit the second line of options
[*]delete and replace the last character on the line
[*]'ESC' to the main GRUB menu and hit 'Enter' to boot.
[*]profit???
[/LIST]

The strange part is that I am not actually changing any of the boot options, only deleting and immediately replacing one of the characters on the boot options line.

My current boot options allow the system to boot, but GRUB does not listen to them unless I go through the procedure above.

Any help would be greatly appreciated!

---

### Post by EXCiD3 on 2008-01-20
What exactly is the error you receive if any?

---

### Post by schwascore on 2008-01-20
No  error, it just hangs on boot.

If I watch the boot at a terminal, it only mentions that it can't find a splash image.

---

### Post by EXCiD3 on 2008-01-20
What is your operating system setup? (Dual boot, just ubuntu, etc?)

You can always try reinstalling grub from the livecd. This may not help any but its worth a shot. [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You did not experience any problems when installing it did you? Can you post the *exact* error that it displays about the splash image?

---

### Post by schwascore on 2008-01-20
I only have Ubuntu on the hard drive.

I am on my fourth re-install and every time it has the same problem.

The frustrating part is that my GRUB config works just fine, but only after I edit it before booting.  Every once in a while (about 10% of the time) the laptop boots just fine with no extra work needed.

---

### Post by EXCiD3 on 2008-01-20
Huh now that is weird. Have you tried Feisty or Hardy Alpha 3? I have absolutely no clue why modifying the parameters and replacing it with the exact same thing would allow it to boot. Have you checked your hard drive recently and have you reformatted the partitions each time you reinstalled?

If you are in a risky mood you could try using a differnet boot loader such as Lilo.

---

### Post by schwascore on 2008-06-28
Just for anyone searching, this problem was solved with the Hardy upgrade.

---

