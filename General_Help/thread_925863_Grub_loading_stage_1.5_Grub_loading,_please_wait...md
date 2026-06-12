---
title: "Grub loading stage 1.5 Grub loading, please wait..... error 18"
date: 2008-09-21
forum: General Help
---

### Post by newone1962 on 2008-09-21
Hello to everyone,

I just installed Ubuntu 8.04 desktop edition. The install went fine and I even got the updates
without any issues. After all is said and done, I get a message prompting me to restart.
Ubuntu seemed to shutdown ok, but upon restarting, I get the following message:

Grub loading stage 1.5 Grub loading, please wait..... error 18

After that, it just hangs and does nothing else.

So I'm wondering what is going on and how to fix this issue.

If anyone knows what I can do to resolve it, I'd appreciate some tips. 

Thanks in advance.

tgw

---

### Post by phidia on 2008-09-21
Probably the easy way to fix this is to grab the live cd and follow the [guide here]("http://linuxmint.com/wiki/index.php/How_to_repair_your_grub").

---

### Post by Thyssenkrupp on 2008-09-21
I had the very same problem when i was building my PC.

You need to insert the disc again, re-do the partitions except this time as your FIRST partition make 250mb of BOOT space.


to do that, make a normal partition and choose to munt it as /boot

then make the rest of your partitions as normal and it will work.

Jak

---

### Post by MichaelSM on 2010-01-19
I had this issue with an old PC box (500 mhz) and a 1999 BIOS trying to access a 160 gig HD. Same error.

Tried various mods to no avail......

In the end just gave up and bit the bullet. One Ritmo SATA/IDE/RAID pci card,  $20. It has its own little bios. Ctrl-F and it boots the hard drive automagically.

Beats stressing out with partitions, bios updates, etc.

Cheers.

Mike.:D

---

