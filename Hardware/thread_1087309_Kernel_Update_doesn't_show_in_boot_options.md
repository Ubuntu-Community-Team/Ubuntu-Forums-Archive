---
title: "Kernel Update doesn't show in boot options"
date: 2009-03-04
forum: Hardware
---

### Post by slammed87d21 on 2009-03-04
I just updated my kernel from 2.6.27-11 to 2.6.27-13. When I boot up, I do not see the new kernel as a boot option. It isn't showing up in  /boot/grub/menu.lst either. It shows in Synaptic it's installed. Anyone have this problem before?

---

### Post by slammed87d21 on 2009-03-06
Anyone?

---

### Post by taurus on 2009-03-06
When you upgraded a kernel, there should be a pop up window asking you if you want to keep the old /boot/grub/menu.lst or use the new one.  I guess you picked the original version.  Therefore, you need to edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and copy the entry for the old kernel before the others.  Then, replace the version **2.6.27-11** with **2.6.27-13** for the new kernel.

Save it and reboot.

If not sure, just post your /boot/grub/menu.lst and the output of this command.

```
ls -la /boot
```

---

### Post by sdennie on 2009-03-06
The update-grub program can automatically regenerate menu.lst based on the kernels installed in /boot.  Try:

```

sudo update-grub

```

See the update-grub man page for more information.

---

### Post by bgiannes on 2009-03-18
i just installed 9.04, and selected the keep menu.lst option  Doh!

so....
i try to run

sudo update-grub

it looks like it works but don't update /boot/grub/menu.lst ?!

i had to manual edit the menu.lst file to add the new kernel

i check and there is no other menu.lst on my HD?

if i 

sudo mv /boot/grub/menu.lst /boot/grub/menu.old.lst

then 

sudo update-grub

it seems to make a good file...

what's going on, is this normal?

---

### Post by sdennie on 2009-03-18
Sounds like a bug in an alpha release of an OS.  ;)

---

