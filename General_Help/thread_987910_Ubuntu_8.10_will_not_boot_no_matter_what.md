---
title: "Ubuntu 8.10 will not boot no matter what"
date: 2008-11-20
forum: General Help
---

### Post by mitchellthegreat on 2008-11-20
I have windows vista and I installed ubuntu from within it. Ubuntu was added to the vista bootloader and it the opens grub when I pick ubuntu. It used to send me to busybox, but I added the thing at the end of the kernel that keeps it from doing that. I started to boot again and it hung. The orange bar just kept bobbing. I swithched it to verbose and it hangs at "squashfs 3.3 by (some guy)" 


Help! I can't get into vista because of viruses and I would rather have ubuntu back.


Edit: forgot to say I checked the kernel again and the thing I added was gone, however it made no difference... I think

---

### Post by TeXtonyx on 2008-11-20
"I have windows vista and I installed ubuntu from within it."

That usually means that you installed with Wubi. That puts Ubuntu
into the Add/Remove Programs of Windows XP. Maybe it's just called
Programs with Vista. I think it is a file that expands.

That means if you can't boot Vista, then you can't Ubuntu. Do you 
have any unallocated space on your drive? If not, make a separate 
partition to install Ubuntu into. Use the Ubuntu live cd and pick
'install into largest continuous free space (guided)' which will
avoid any possible further complications for the fate of Vista. 
This will fix your busybox error and by default it will install 
Ubuntu into the MBR. If you wind up reinstalling Vista, then Vista
reinstalls itself to the MBR, ousting grub. Then you can either
reinstall grub again, or download a free program called Easybcd
and add Ubuntu back to Vista's boot menu (add it under Linux).

---

### Post by mitchellthegreat on 2008-11-20
well, I can get to vista, it's just extremely slow. I installed using something like wmenu. It made a ubuntu folder in my c drives folder. Ubuntu should work, but it doesn't for some strange reason. Is there a command I could put into the kernel?

---

### Post by mitchellthegreat on 2008-11-20
Nevermind, nothings wrong. I was just being impatient =P


This deserves the "dumbest moment of the year" award.

---

