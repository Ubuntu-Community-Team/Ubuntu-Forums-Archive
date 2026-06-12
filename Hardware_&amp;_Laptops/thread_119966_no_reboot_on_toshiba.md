---
title: "no reboot on toshiba"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by Ana Carolina on 2006-01-20
Hi all,

After I had installed ubuntu 5.10 I started to have problems with reboot, it hungs in a black scream and doesn't restart anymore! :-(

I've looked for a fix and I found someting to change in the /boot/grub/menu.lst but unfortunatelly my menu.lst is now back to the original again... and I don't have reboot again :'(

So I tried to do 
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash reboot=h

or 

kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro no apic nolapic quiet splash 

But nohing works!!!! :-O

Can someone help me??? please!!!

Thanks, aninha

---

### Post by zasf on 2006-01-21
what video drivers are installed? When I installed ATI's drivers, reboot started to work properly..

---

