---
title: "Ubuntu 64 and System Commander"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by bmoagu on 2009-02-06
I installed Unbuntu 64 under system commander 9 in its own partion. During installation I made sure that "install boot loader" was checked off as an advanced option. When I boot the computer System Commander shows me an Icon for a Linux installation but Ubuntu will not start because the boot loader is supposedly not installed. I reinstalled Ubuntu 64, again making sure the option to install the boot loader was checked.
Same problem. System Commander 9 otherwise correctly gives me the option to boot to the three versions of Windows installed on this machine. How do I check/reinstall the boot loader from the Ubuntu installation disc: is there a way to get to a command line for the Ubuntu equivalent of "fixmbr"?

---

### Post by cariboo on 2009-02-06
Yes there is an equivalent to fixmbr. Boot from the LiveCD, once you are at the desktop open a Applications-->Accessories-->Termianl and type

```
sudo grub
```

This will open the grub editor. At the prompt type:

```
find /boot/grub/stage1
```

This will result in something like this:

```
(hd0,0)
```

The first nuber is the disk number, and the second is the partition number. Grubs starts counting from zero, so the above example would be hard drive 1 partition 1. THe next step is to set the root disk:

```
root (hd0,0)
```

substitute the result you got from the find command for (hd0,0). THe next step is to write to the mbr:

```
setup (hd0)
```

note that only the disk number is used and not the partition number. the final step ist to type:

```
quit
```

at the prompt to exit the grub editor. You can now reboot. 

Note that grub will create a menu with the other OSs in the menu.

Jim

---

