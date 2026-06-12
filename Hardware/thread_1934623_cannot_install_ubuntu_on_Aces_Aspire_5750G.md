---
title: "cannot install ubuntu on Aces Aspire 5750G"
date: 2012-03-02
forum: Hardware
---

### Post by a_m on 2012-03-02
Hi guys,

I am really struggling to install Ubuntu on a brand new Acer Aspire 5750G.
I have tried with several Ubuntu version (from 10.04 to 11.10, both 32bit and 64bit), both from CD and USB (built with Unetbootin). I always get an error message that sounds like this:

udevd[113]: '/sbin/modprobe -bv pci:V000010DEd00000DEAsv00001025sd00000505bc03sc00i00' [201] terminated bi signal 9 (Killed)

Since I've read that nvidia optimus may be the reason of the troubles, I tried to disable the nvidia graphic card from the bios (choosing "integrated" instead of "switchable") but it didn't help.

I can see that people usually have troubles with this 5750G, but at least they installed Ubuntu. I can't even find the way to install it! :(

Does anyone have any suggestion? Please, help me!

Thanks!
Andrea

---

### Post by mindwarp on 2012-03-03
The reason this is happening is because of the Nvidia Optimus  chipset which is not supported by Nvidia on Linux.  

To get it to install, when you boot up the CD hit F6 and select acpi=off  -- this should let you install it.

Once you get that far, if you want to enable your nvidia graphics (by default you will use intel) check out [http://sachithdhanushka.blogspot.com/2012/02/bumblebee-30-for-ubuntu-1110.html](http://sachithdhanushka.blogspot.com/2012/02/bumblebee-30-for-ubuntu-1110.html)

I have a 5742g that I had to do this with.  I also had to add a few options to grub.conf that started with i915.* but I don't believe they were required, just tweaks to make the startup screen appear.

---

### Post by Bucky Ball on 2012-03-03
> **mindwarp said:**
> 
To get it to install, when you boot up the CD hit F6 and select acpi=off  -- this should let you install it.



If that doesn't work, try hitting F6 then choose 'nomodset' instead. ;)

---

### Post by a_m on 2012-03-10
Thank you SO much!!! It worked :D

I found out that the easiest way is to diable the nvidia card in the bios (choosing "integrated" instead of "switchable"). This is extremely easy but, of course, this means to renounce to the nvidia card.
Thanks again!

---

### Post by Bucky Ball on 2012-03-10
Cool. Now you could get online, get your updates, go to 'Additional Drivers' (maybe 'Hardware Drivers' depending on release) and there should be an Nvidia driver in there but disabled. You could enable that and you should be right. 

Please mark thread as 'Solved' from thread tools to help others. ;)

PS: Which one worked, incidentally? acpi=off or nomodset?

---

