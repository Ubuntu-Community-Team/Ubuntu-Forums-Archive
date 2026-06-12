---
title: "Ubuntu 8.10 Intrepid Ibex hangs on boot"
date: 2008-11-01
forum: General Help
---

### Post by kvcxn on 2008-11-01
I just upgraded to Intrepid Ibex from Hardy Heron and it seems to be hanging on boot (the progress bar makes its way about 20% through boot). The only way I can get it to continue is if I hold the power button on my laptop down for 1/2 a second or if I hold down a key.

In dmesg, the last output before the hang is:

```

hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected

```


If I hit any key once, the next lines that come up are:
```

ACPI: PCI Interrupt Link [LSIO] enabled at IRQ 23
pata_acpi 0000:00:09.0: PCI INT A -> LINK[LSI0] -> GSI 23 (level, low) -> IRQ 23
....
(continues to boot)

```

Any insight here?
I tried a clean install, same problem persists.

I have a HP Compaq Laptop (F761US Notebook).

---

### Post by spikenick on 2008-11-04
I am experiencing the same problem on my machine which is a dv6700CTO it has an AMD Turion64x2 with Nvidia 7150GO.. let me know if you find a fix, I am using the 32bit version since i need sun java to work right I know that might make a difference.

---

### Post by obsidianpoet on 2008-11-04
I have the exact same problem on my HP pavillion dv6700 as described above. Its workable just really annoying :)

---

### Post by Spartacus84 on 2008-11-04
I have the same problem, and it's starting to be really annoying.

EDIT: I'm running 8.10 32 bit on a Compaq Presario F756NR in case anyone cares.

---

### Post by Spartacus84 on 2008-11-05
Is it possible to write a script so it just holds the spacebar during boot? Would that fix the problem?

---

### Post by MakotoTheKnight on 2008-11-05
This bug is already [in the works.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247")  The fix is to add "acpi=noirq" to your /boot/grub/menu.lst (specify the kernel), which works fine.

---

### Post by jamesbyron on 2009-02-06
I have a Compaq Presario F700 and had the same problem. Here is how I fixed it:

Open a terminal window (Applications/Accessories/Terminal)
type sudo nautilus
enter your password
In the left hand panel, click File System
Navigate to the directory boot/grub/
Click on menu.lst to open it in a text editor
Find the line that starts with "kernel"
at the end of the line add a space and then "acpi=noirq"
save the file
close everything
reboot

That worked for me.

---

### Post by andyshedd on 2009-02-13
Thanks for the fix (I have a Compaq F700 also). Incidentally, I had the same problem with an install of Fedora 10 64 bit. Maybe it happens with the newer kernels?

---

