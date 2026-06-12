---
title: "reboot problems"
date: 2008-07-19
forum: General Help
---

### Post by benste on 2008-07-19
Dear all, I created a video whihc shows my reboot.
PLease take a look into it and explain me what all these critical errors and abortions mean.

some seems to handle my wifi with the gnome network manager
others care about sony things which they don't find and than something with nvidia -
I've got no clue but i think that reboot would take much less time without these mistakes. (I disabled the usplash in grub to see why iit takes a long time)

I'll post the link to the youtube video asap (when it's fully uploaded)

[http://www.youtube.com/v/hwbVDOjrdjc]("http://www.youtube.com/v/hwbVDOjrdjc")
there is also something with lib or so

---

### Post by spiderbatdad on 2008-07-19
the information, i think, you are try to display is in the output of dmesg. That video is nearly impossible for me to see.

```
dmesg > ~/Desktop/dmesg.txt
```right click on that file after running the command in a terminal. Choose: "create an archive." Upload the archive here with the manage attachment tool below.

---

### Post by benste on 2008-07-19
thx for helping - i looked into the document - I didn't find any error as reported in shutdown or bootup

but you may be abel to help me with this file
mybe I've enough time next week to point out what the error say  - maybe a beter video (I was abel to read it with a bit of fantasy)

---

### Post by spiderbatdad on 2008-07-19
this looks like a problem:```
 ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
```

You can try to edit the file /boot/grub/menu.lst with the command:```
gksu gedit /boot/grub/menu.lst
```scroll down to the section:

```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.26-4-server
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.26-4-server root=UUID=##'s ro **acpi_apic_instance=2**
initrd		/boot/initrd.img-2.6.26-4-server
quiet
savedefault

```

edit the end of the line beginning with the word "kernel" to match the bold text above. If that doesn't work, you can try "noapic." So you would have: ro noapic

Reboot.

good luck.

---

### Post by benste on 2008-07-21
Here is the new one

I read my error mesages shown up on boot and power down,
after login out there is something with GDM and has table error

on boot up it seems like he's tring to isntall the nvidia kernel
but it's already  installed - and gives the error messagfe "alreadey installed"

please go on and let's solve all issues on reboot.

---

### Post by benste on 2008-07-21
There is another effect after your last try,
FN key + F5 is increasing brightness (the keys did never work before)
+ my special key S1 is doing the same, but normally FN + F6 should increase and Fn+ F5 deincrease.

Maybe you're able to help me here to - this is the first step for me using the FN Keys on a Sony Vaio which is qute difficult

---

### Post by benste on 2008-07-22
Nothing more?

---

### Post by benste on 2008-07-26
really no one or should I start a new thread?
there are several error messages left!
like
nvidia tries to install on bootup
gdm give ghash table or so errror on shutdown
network-manager gives several error messages while shutdown
...

---

