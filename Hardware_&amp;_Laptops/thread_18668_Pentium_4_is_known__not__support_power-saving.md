---
title: "Pentium 4 is known _not_ support power-saving"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by gix on 2005-03-08
Hi all!

Last week I had some problems with the audio on my Toshiba satellite A60.
Search on this forum gave me some hints about kernel parameters ...
At first I've added "noapic"  to the kopt line on /boot/grub/menu.lst and .... wow! I could listen my ubuntu sing my music! but .... all the acpi was off!!! the main issue was the cpu fan! it was switched off!!!

So, after a better search, I modified the kopt with "acpi=on pci=noacpi"

now, I hope, everything goes well but ( there's always a "but" of course...  :-|  ) among the last boot messages I can see a new message (I'm quite sure that one week ago it didn't appear...) 


This processor "Mobile Intel(R) Pentium(R) 4 CPU 2.80 GHz" is known _not_ to support   power-saving.

and few lines below again a line marked by a red star that says:
CPU frequency scaling not supported

 ](*,) 

.... could anyone give me some help?
thanks
GiGi

---

### Post by gix on 2005-03-08
bad updates ... 
the couple of options "acpi=on pci=noacpi" seems to be still wrong and satisfy in alternated way...
at first boot the cpu fan is disabled...
I've to reboot to have it running correctly ...
(I've also tested  the "acpi=off apm=on" options ... same results...)
 :cry: 

some good links are welcome ... 
thanks
GiGi

---

### Post by gix on 2005-03-10
I've installed the kernel 2.6.10-4-686, added the option "acpi=on" and now all seems going well...
The fan turns on, the audio works and so the network (with pci=noacpi I've encountered some issues even if the eth0 was correctly detected and configured...)
I can't give any explanation but, hey, it works!
 \\:D/

---

