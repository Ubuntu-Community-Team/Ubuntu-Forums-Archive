---
title: "Grub Titles"
date: 2008-09-03
forum: General Help
---

### Post by dawynn on 2008-09-03
Aesthetic question here.

I keep a system with two releases of Ubuntu at all times -- now Intepid and Hardy.

My problem, and this is just an aesthetic problem, is with how grub menus get updated.  Every time I add a kernel, the system thinks it needs to relabel every single kernel on my system.

So, if a new kernel release comes out for Hardy, every kernel in the menu (including the Intrepid kernels) gets labeled as Ubuntu 8.04.  If a new kernel release comes out for Intrepid, every kernel in the menu (including Hardy's) gets labeld as Ubuntu 8.10.

I don't want to mess around in the actual code area where everything gets automatically updated.  But is there a way in the meta code above to indicate, for example, that 2.6.24 kernels should be labeled as "Hardy Heron" and 2.6.27 kernels should be labeled as "Intrepid Ibex"?

Please send along syntax if this is possible!

---

### Post by justleen on 2008-09-03
you can change the titles in /boot/grub/menu.lst

never had any problems after a update.. (well, apart from new entries being added)

---

### Post by dawynn on 2008-09-03
I'm familiar with menu.lst.  

menu.lst is separated into two sections.  There's a main section at the bottom that gets automatically updated every time a kernel is added.  There's also a meta-code section at the top that allows you to specify some attributes that should be set for each kernel.  By default, this meta-code section shows you how to set automagic boot parameters per kernel.  For instance, I can say that all kernels should use an acpi=force command.  I can also specify each kernel series to use a different drive partition for booting.

What I'm not sure about is how to use the meta-code settings to automatically set the titles that should be used for each kernel series.  I don't want to mess with the real menu listings, and I don't want to have to keep messing in the real menu listings every time a new kernel version comes out if the kernel version is in the same series as one I'm already using.  How should the syntax be formed in the meta-code area to let the automagic stuff properly name everything?

---

