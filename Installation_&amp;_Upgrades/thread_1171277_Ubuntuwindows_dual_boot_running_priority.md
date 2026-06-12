---
title: "Ubuntu/windows dual boot running priority"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2009-05-27
I have Windows XP and Ubuntu 9.04 running in Dual Boot mode. What I want  to arrange is for Windows to be the default ( First System ) to load. At the moment Ubuntu is the default, loading first. Is there a simple way of changing the priority ??

---

### Post by ronparent on 2009-05-27
Use the terminal session command **sudo gedit** to involke the editor as administrator. Open file /boot/grub/menu.lst. Navigat to near bottom of file. There you will find the menu items along with loading instruction following each item for booting that item. Simply move the windows selection anlong with the associated lines following as a block to precede the 1st ubuntu entry. Save and on next boot windows will boot 1st by default.

---

### Post by Shazaam on 2009-05-27
StartupManager allows you to change boot priority using a gui. It can be installed with Synaptic. You can also edit this section...
```
default       0
```
in boot/grub/menu.lst to change which os loads first (count from 0).

---

### Post by pricetech on 2009-05-27
OR:
Edit menu.lst and change the entry "default" to "3" (or whatever your winders entry is).  Remember: the count starts at 0 not 1.

ALWAYS make a backup copy of the file before editing:  sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig  for example.

---

### Post by zubin71 on 2009-05-27
hope you`r problem`s been solved!

---

### Post by wkulecz on 2009-05-27
I'm not sure about startup manager as this is the first I'd head of it, but the other solutions mentioned in my experience break the next time the kernel updates.

If you are not booting from RAID array, adding savedefault to the boot stanzas (usually there automatically in the "OTHER" stanza, and making default "saved" instead of a number will make the last system used the default for next time.

Problem is the numbers change when the kernel updates as by defult the old kernels remain and are listed as boot options in case the update breaks your system.

Before you mess with /boot/grub/menu first, search for "re-installing grub", print out the instructions and keep them handy with your Live CD installer disk.  You'll thank me later :)

--wally.


--wally.

---

### Post by ronparent on 2009-05-27
The following by example is my own grub booting options:

## ## End Default Options ##
## Manually inserted options

title	Windows 7 rc - on hd2,1
rootnoverify	(hd0,1)
chainloader	+1

title	Windows XP - on sda
rootnoverify	(hd1,0)
map	(hd1)	(hd0)
map	(hd0)	(hd1)
chainloader	+1

## END Manually inserted options

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		e6b7739b-7050-4621-a1fb-6099d2608dcc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e6b7739b-7050-4621-a1fb-6099d2608dcc ro noapic nolapic quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		e6b7739b-7050-4621-a1fb-6099d2608dcc
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=e6b7739b-7050-4621-a1fb-6099d2608dcc ro noapic nolapic  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		e6b7739b-7050-4621-a1fb-6099d2608dcc
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

I doubt that it will 'break' the next time the kernnel is updated. Correction anyone?

---

### Post by raymondh on 2009-05-27
> **Dyffo said:**
> I have Windows XP and Ubuntu 9.04 running in Dual Boot mode. What I want  to arrange is for Windows to be the default ( First System ) to load. At the moment Ubuntu is the default, loading first. Is there a simple way of changing the priority ??

Hello Dyffo,

Attached is screenshot of my startup manager showing Vista as the default boot.  Is this what you were looking for?

If so, synaptic can be your friend :)  Search for startup manager and have a go.

Regards,

---

### Post by Dyffo on 2009-05-28
> **raymondhenson said:**
> Hello Dyffo,

Attached is screenshot of my startup manager showing Vista as the default boot.  Is this what you were looking for?

If so, synaptic can be your friend :)  Search for startup manager and have a go.

Regards,

):P)THIS IS THE ONE !!!!!!!! Brilliant and thanks - problem SOLVED.

---

