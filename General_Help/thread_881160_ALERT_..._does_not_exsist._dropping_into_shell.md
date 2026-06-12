---
title: "ALERT ... does not exsist. dropping into shell"
date: 2008-08-05
forum: General Help
---

### Post by BonOfTheDead on 2008-08-05
alright. i went to see how my computer was going, when i notice, its not on anymore. after booting it, i noticed that it wont boot. last time this happened, i spent an hour trying to figure it out. i ran ubuntu in recovery mode, and i got this error, or alert or what ever it is.


```
Begin: Waiting for root file system ...
Done.
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/dick/by-uuid/2a15d320-d882-409f-8819-af3f257e0526 does not exist. Dropping to a shell!
(initramfs)
```

first off, i have not idea what that means other than somethings wrong, and i have a very basic understanding of how to use commands.

so, anyone got any ideas? im stumped.

---

### Post by DagMan on 2008-08-06
I haven't run into this so I'm sort of guessing, but it looks like it's found your kernel, but after that it wasn't able to find the / partition.  
Anyhow, try this...
when you get to the bootloader screen, you'lle see the kernel that its about to boot,  If not, then hit escape and then youlle see it.  Once you're there hit the letter 'e'

Mine will look differant than yours, but it's still usefull to illustate what you'lee see as it will be similar.  Here's mine
```
title		Ubuntu 8.04, kernel 2.6.24-20-eeepc
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-20-eeepc root=UUID=ad6770d3-057b-4687-a92d-77f95b042b0a ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-eeepc
quiet
```
use the arrow key to go down to the line that says **kernel** and hit the letter 'e' (for edit) again.
the part that says this root=UUID=ad6770d3-057b-4687-a92d-77f95b042b0a
change it along the lines of the following..,
if you're / partition is the second partition on the first hard drive then it would be /dev/sda2
if it was the first partition on the first disk it would be /dev/sda1
if it was the first partition on the second disk it would be /dev/sdb1
so from the examples you can see that you ignore the /dev part and concentrate on the second part which is /sda1 /sda2 /sdb1 /sdb2 etc
once you figure out what to use substitute it for the big long ugly sting that says in my case UUID=ad6770d3-057b-4687-a92d-77f95b042b0a
and from the look of it, in your case probably UUID=2a15d320-d882-409f-8819-af3f257e0526
so instead of root=UUID=2a15d320-d882-409f-8819-af3f257e0526
you want for example  root=/dev/sda1 or root=/dev/sda2 or root=/dev/sdb1 or whatever applies.

You aren't making a permanent change by doing this.  If it works, then post again as to how to make the change permanent, otherwise it will go back to the same thing at every reboot.

If this does get you back in btw, then expect to have an automated filesystem check most likely followed by a mandantory reeboot, since this happened after some kind of crash, and as such be prepared to keep editing at startup until you get through your boot process.

Good luck, I hope I've guessed correctly what the problem is.

---

### Post by claudioItaly82 on 2009-11-23
Thanks a lot! It Works for me.

---

### Post by AnthonyI on 2009-11-25
I've had this exact same error after the update (it happened after II disconnected one of my hard drives).

I changed it to /dev/sda and it works now.

How do I make this change permanent?

---

### Post by esmerine on 2009-12-29
Tell tell tell us how to make things permanent!
It also saved me! :guitar:

---

### Post by ampedforay on 2010-01-28
Hi,
 
I added it to the menu.lst for the grub boot loader. This works for grub legacy. I'm not sure about grub 2 or lilo.

---

