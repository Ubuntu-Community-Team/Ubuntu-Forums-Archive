---
title: "Compaq Presario f560us  (AKA) F500"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by marc66thomas on 2007-09-17
I have Feisty booting and running but have two smaller issues
1. video and sound only seem to play smoothly if I move the mouse rapidly. (i think the os is throttling the cpu up when I move the mouse.)  
I read a post on disabling CPU speed but don't understand that "Disable the service "cpuspeed" according to you distributions instructions."

2. video setting are no responding as expected: under system, administration, Screens and graphics,  I put in my password, and I get "I  you need to have administrative rights to change all screen settings" as if I typed my password incorrectly. I have done this a number of times and typed my password correctly. The screen is not detecting the other monitor and doesn't allow me to make any changes. but it does show the nvida driver in use.
here is the grub settings for this laptop that boot and run 

title		Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-11-generic root=UUID=598aaa58-bab8-4c01-96f9-8fda1a297d72 ro quiet splash noapic irqpoll acpi=off
initrd		/boot/initrd.img-2.6.22-11-generic quiet

I'd appreciate a little direction or information on either or both issues

---

### Post by Slothbert on 2007-09-20
I have the same Issue on my computer. Dell Dimension XPS T600r

---

### Post by zutronius on 2007-09-21
How did you manage to get Ubuntu working on the F500. I have been trying for over two weeks to get Ubuntu Studio running and have had no luck whatsoever. If you could let me know what you did to get it working, I would REALLY appreciate that.

---

### Post by marc66thomas on 2007-09-21
> **zutronius said:**
> How did you manage to get Ubuntu working on the F500. I have been trying for over two weeks to get Ubuntu Studio running and have had no luck whatsoever. If you could let me know what you did to get it working, I would REALLY appreciate that.

Ok I dont know "Ubuntu Studio" but here is what I did.
Updated all drivers and bios from Compaq website (don't know if it matters much)
Using the Ubu 7.10 i386i desktop intel CD image [https://wiki.ubuntu.com/GutsyGibbon/Tribe6/Kubuntu?highlight=%28download%29%7C%28gutsy%29](https://wiki.ubuntu.com/GutsyGibbon/Tribe6/Kubuntu?highlight=%28download%29%7C%28gutsy%29) . Made CD. Loaded CD using the post from some smart folks [http://ubuntuforums.org/showthread.php?t=504255&highlight=compaq+Presario+F500](http://ubuntuforums.org/showthread.php?t=504255&highlight=compaq+Presario+F500)

Modified Grub to: 
title Ubuntu gutsy (development branch), kernel 2.6.22-11-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-11-generic root=UUID=598aaa58-bab8-4c01-96f9-8fda1a297d72 ro quiet splash** noapic irqpoll acpi=off**
initrd /boot/initrd.img-2.6.22-11-generic quiet

Ran update manager and it boots each time. 
I also have started using the Nvidia restricted drivers.. after the updates...  I haven't got wireless working yet, but I believe that if I follow the thread listed above (removing acpi=off) from the grub menu.lst file It should be golden. 
**BIG PS** this is the ISO for the (development branch) of Gutsy Gibbons and not a stable or official built yet (lots of daily updates and bug fixes.) That said it's fully functional for me, and the bug fixes already have improved usability issues.

PPS this is somewhat off thread topic. Hope it helped you or someone else.

---

### Post by marc66thomas on 2007-09-21
sorry duplicate

---

