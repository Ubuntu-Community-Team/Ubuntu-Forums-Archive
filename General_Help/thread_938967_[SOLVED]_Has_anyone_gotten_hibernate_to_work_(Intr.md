---
title: "[SOLVED] Has anyone gotten hibernate to work? (Intrepid/Hardy)"
date: 2008-10-05
forum: General Help
---

### Post by Vietman on 2008-10-05
It gives me "error reading swap device" and then show some green blocks on the screen.

On reboot, it hard crashes...have to recover from a previous boot.

Is there any way to safely hibernate in Ubuntu?

---

### Post by Ptero-4 on 2008-10-05
Check that you have a swap partition in your HD, and then check that you have the "resume=/dev/*swapdevice*" in the default "kopt" entry in your /boot/grub/menu.lst file.

---

### Post by fragos on 2008-10-05
Make sure your swap space is at least as big as your memory size. Hibernate stores your memory image in swap.

---

### Post by MaxIBoy on 2008-10-05
I recommend making it twice as big.


Hibernate works just fine on my laptop. On my desktop it can be a problem.

---

### Post by Vietman on 2008-10-05
I tried your suggestion, Ptero-4. Now it's giving me beeping and/or lockups when I boot.

I've tried [this fix]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html#comment-146615") too, but it's not reliable.

My memory is 2 gigs, and my current swap is 3. Ironically, I had been able to hibernate once back when it was only 2, with that aforementioned fix. Is there a bios setting I might be missing?

---

### Post by Vietman on 2008-10-05
After some extensive Googling, I managed to get it to work! Thanks for the tip, Ptero-4, that was a part of the total solution.

Honestly, I don't remember all the steps I did to fix this, but here are some of the references that helped (what didn't help was that optional hibernate / uswsusp package that just created more problems):

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)
[http://lists.tuxonice.net/pipermail/tuxonice-users/2008-February/000151.html](http://lists.tuxonice.net/pipermail/tuxonice-users/2008-February/000151.html)

I don't remember if there was anything else. At any rate, it's fixed.

Sweet...now I don't have to run away to another distro like PCLinuxOS. Yet. ;)

---

### Post by blackpaw on 2008-12-01
Hello!

Vietman, would you post some information on your system, please?
Motherboard chipset, harddrives, etc?
AGP graphics card or PCI express? (because of the AGPgart)
Ubuntu version and if it's i386 or x86_64?

I am fighting with suspend/hibernate, too.. even tried to compile tuxonice (suspend2) into the kernel but somehow I failed because of xen (not entirely sure, yet what this is...)

Ubuntu 8.10 was by far the easiest and smoothest installation EVER if it wasn't for suspend/hibernate. 

cheers,



Andreas

---

### Post by aromo on 2009-03-24
Hi, I used to have a ThinkPad R40 with Hardy. I upgraded to Intrepid and hibernation didn't work so I went back to Hardy.

Now I have a R51 with Ibex and was getting the same problem. As suggested in this thread, I edited the /boot/grub/menu.lst file, under additional options added the following line and it did the trick:

resume=/dev/sda5


Where /dev/sda5 is my swap partition (I figured that out with fdisk -l)

Look forward for Jaunty.

Thanks!

---

