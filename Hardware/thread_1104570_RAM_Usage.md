---
title: "RAM Usage"
date: 2009-03-23
forum: Hardware
---

### Post by Phædrus2401 on 2009-03-23
This isn't a pressing issue, but I was wondering why Ubuntu uses more RAM booted normally off my hard drive on my desktop than it does booted off the LiveCD on a laptop.

As I understand it, the LiveCD loads most of the OS's main files onto the computer's RAM. Thus it would seem to me that when booted off the CD Ubuntu's RAM usage would be far greater than when booted off a hard drive. 

However, when I boot using the CD I normally see RAM usage at around 190 MiB--whereas when I boot off a hard disk the RAM stays at around 380 MiB, nearly twice that of the CD boot. This seems counterintuitive. It's not a matter of programs running--the only background program I've installed since I installed Ubuntu is Firestarter, and I can't imagine that that would have a 200 MB footprint.

Does anyone have any explanation for this?

---

### Post by agim on 2009-03-23
Mine does the opposite, the livecd always uses more ram for me.
Strange.

---

### Post by kpatz on 2009-03-23
How much RAM do you have?  Swap size?

I don't know if the RAM disk used by the live CD counts toward the RAM usage you're seeing or not.  Also, if you have a swap file on your HD now but didn't when you ran the live CD, there would be less RAM available, thus the disk cache couldn't grow as large (which is what most RAM is used for if it isn't need by programs).

---

### Post by Phædrus2401 on 2009-03-23
I've got 3GB of DDR2 RAM. I'm not sure about the swap file, as I don't know how to check that in Linux.

---

### Post by cariboo on 2009-03-23
The way Linux uses ram is different from the way windows uses it. The Linux kernel is designed to use most of the available RAM for buffers and cache. Unused ram is wasted ram.

Jim

---

