---
title: "Hard Drive Recovery"
date: 2013-05-13
forum: Hardware
---

### Post by olnik on 2013-05-13
So basically my girlfriend was running 64bit Windows 7 on her laptop, and it crashed and wouldn't boot. So I said I'd try and fix it and accidently made it worse,(**her hard drive is now in my desktop computer running 64 bit ubuntu 13.04**) she had a huge amount of important photos. I recovered most of the data on to an image file, but shortly after the hard drive has become completely unmountable all together.

When I open **'Disks**' all that shows up is '**Hard Disk**', with all model, size, etc being dashed out. In fact the only other informatio is it's location which is /dev/sdb. There is no option to format or even run any kind of diagnostics. Fdisk doesn't recognise it either. 

Any help with how to get this back to working order would be much appreciated, or just someone with high computer knowledge to tell me the hard drive is screwed. Don't really want to fork out £40 to buy her a new hard drive... 

Thanks in advance, James.

---

### Post by tgalati4 on 2013-05-13
There's a pdf you can search for on the web:  200 ways to revive a hard drive.  My guess is that it was failing--as opposed to Windows balling itself up or a virus.  It lasted just long enough for you to install Ubuntu on it, but then failed in a permanent fashion.

If *fdisk* can't see it and the kernel can't mount it, then there is not much you can do.  Install* smartmontools* and see if you can read the SMART parameters.  Modern drives store their errors and that would give you a clue as to what was failing and for how long.

Your ex-girlfriend appreciates your efforts.

---

### Post by olnik on 2013-05-14
Thanks, I'll check it out!

---

