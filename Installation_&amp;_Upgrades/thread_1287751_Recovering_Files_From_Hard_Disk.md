---
title: "Recovering Files From Hard Disk"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by yogiman_uk on 2009-10-10
Hi

Got a problem, my brother did an update on his 8.10 and it has caused a problem with the hard disk, thus Ubuntu will not boot.

So I am preparing to reinstall the computer for him.

He wants his files from his home directory so I booted with a live CD hoping to copy his files off be fore reinstalling the machine.

Unfortunately some of the files appear to be locked as it won't let me copy them, they have a small orange dot on them with a X in it.

Attempting to copy them results in failure.

I have looked at the permissions and it says I don't have permission to change the permissions.

Can anyone tell me if it is possible to make Ubuntu logon to that drive with the original username and password or to take control of those files so that I can copy them.

Thanks for any help.

Regards


Yogiman!

---

### Post by prshah on 2009-10-10
> **yogiman_uk said:**
> 
Unfortunately some of the files appear to be locked as it won't let me copy them, they have a small orange dot on them with a X in it.


You can copy/access them using "sudo" (SuperUser); or if you prefer the GUI method, press Alt+F2, and give the command ```
gksudo nautilus
```

Note that using Nautilus in Super User mode is generally not recommended, but you should be fine in Live CD mode.

---

### Post by yogiman_uk on 2009-10-10
Thank you for the reply, I knew some genius would have the answer.

Regards


Yogiman!

---

### Post by JohnESimpson on 2009-11-14
> **prshah said:**
> You can copy/access them using "sudo" (SuperUser); or if you prefer the GUI method, press Alt+F2, and give the command ```
gksudo nautilus
```Note that using Nautilus in Super User mode is generally not recommended, but you should be fine in Live CD mode.

You may have just saved my Ubuntu life. THANK YOU.

---

