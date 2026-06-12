---
title: "Laptop keyboard &amp; touchpad occasionally lock up"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by atrus on 2008-02-18
my laptop's ps2 keyboard and touchpad occasionally stop working completely, usually with a key stuck repeating. It always happens simultaneously, and completely stops me from using the machine.

I can plug in an external mouse to hit suspend & resume  (provided that the stuck key isn't a modifier like ALT, which usually prevents me from clicking on buttons), at which point everything works right again. i'm sort of lost as to what to investigate.

Any ideas would be greatly appreciated.

I'm on a Levono 3000 N100 0768DDU laptop.

---

### Post by s0ullight on 2008-03-01
i have a kind of same problem just started today
my keyboard and touchpad just stopped working after a reboot
they work during grub and the bootscreen of an inserted bootable cd
after that it doesn't work anymore 
the shift lock butten light doesn't work 
opening shells won't work
but i noticed one thing: at the recoverystart they work
can someone plz help?

---

### Post by s0ullight on 2008-03-01
hey found a good way to solve it :D
just edit the boot options and add noacpi
it worked fine for me ;]

---

### Post by rahaman.naik on 2008-03-14
> **s0ullight said:**
> hey found a good way to solve it :D
just edit the boot options and add noacpi
it worked fine for me ;]
Hi S0ullight,
    i am also facing the same problem on Lenovo 3000 laptop. i have windows and ubuntu on my notebook. But once i boot up the keyboard didnt' get detect by the Ubuntu ... and once i reboot it the keyboard and touch pad works fine. can you pls give me the path and file name where did you edit the file? waiting for your reply.

Did you edit this file /boot/grub/menu.lst ??

 Thanks in advance.

---

