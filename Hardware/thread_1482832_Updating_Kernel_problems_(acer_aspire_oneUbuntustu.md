---
title: "Updating Kernel problems (acer aspire one/Ubuntustudio 9.04)"
date: 2010-05-14
forum: Hardware
---

### Post by Monomer on 2010-05-14
I'm having some problems going from 2.6.28-18-generic to 2.6.32xxx

I need to upgrade the kernel to support my Audio4dj USB interface. Patching alsa did not work (I'm still tinkering with that)

[http://www.pogo.org.uk/~mark/linuxdj/](http://www.pogo.org.uk/~mark/linuxdj/)


I've unpackaged the kernel files, they installed just fine. Updated grub and rebooted. 

From the grub load screen, I select my freshly loaded 2.6.32 kernel and it begins to load. I get a quick flash of an error message (pci error of some sort) and it then it reboots and I'm back to where I started.


I'm sort of new to linux still. This kernel did run on this machine before flawlessly. I migrated from 9.04 to 9.10 and quickly back as I was having issues, so this is a fresh install again.


For those wondering, this is purely a machine to run Xwax and various other studio programs. 




Help?

---

### Post by devilized on 2010-05-14
I had the same problem with the same kernel - and never recovered from it. I ended up backing everything up and starting fresh with 9.10. 

It's not to say that it's not possible to get working, but you're not the only one having that issue.

---

### Post by Monomer on 2010-05-14
9.10 didn't support my intel onboard graphics.

10.04 seems to use the kernel I need from the get-go. Rumour has it the intel card is supported.

I hear pulse audio is also more embedded, and most programs I use simply don't support it.  



rock and a hardplace, it seems.

---

### Post by devilized on 2010-05-14
Everything in 9.04 worked great for me until a kernel update. I almost went back, but eventually wrestled 9.10 into working (90% of the way anyway)

---

