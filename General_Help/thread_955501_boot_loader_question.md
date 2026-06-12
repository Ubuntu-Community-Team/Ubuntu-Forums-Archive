---
title: "boot loader question"
date: 2008-10-22
forum: General Help
---

### Post by thirdeye420 on 2008-10-22
Hi all,

Okay, My HD is partitioned.  one partition has win-xp, the other ubuntu.  I had to reinstall win-xp yesterday.  When i boot up my computer now, there is no longer a screen coming up asking me which operating system I want to use.  Wondering if anyone out there could point me in the right direction to correcting this problem.  Help is very much appreciated.

thanks!

---

### Post by jnorthr on 2008-10-22
If you installed XP after you installed linux, it will have over-written the GRUB (grand unified bootloader) loader that asks you that question. You can reinstall the GRUB. Try to google for a HowTo that explains it.

---

### Post by thirdeye420 on 2008-10-22
how can I find out what my partition numbers are?  eg, (hd0,3)?

---

### Post by No-Neck on 2008-10-22
Boot up the Ubuntu LiveCD and open up a terminal. Type 'grub'.

Now type "find /boot/grub/stage1" and you will find out which partition contains GRUB.

Finally "root (hdx,x)" "setup (hdx)" 

Done. :)

There are actually plenty of guides on this though.

---

### Post by thirdeye420 on 2008-10-22
okay, this seems simple enough.  I just need to know the ID of the partition the bootloader is on, I don't need to know the ID of what win xp is on?

---

### Post by No-Neck on 2008-10-22
Nope, all you need to do is type those 4 commands into the terminal in the LiveCD. Assuming you install Windows in the same place as it was before, it should also be bootable. 

You haven't changed the configuration of GRUB, just overwritten the MBR which now points to NTLDR instead of GRUB.

---

### Post by bodhi.zazen on 2008-10-22
While you do not "need" to know your partitions, it is a very very good idea to understand your partitions as this prevents you from over writing the wrong partition.

Take a look at this link :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by thirdeye420 on 2008-10-22
I tried the above commands from the livecd and all I got were errors
grub> "find /boot/grub/stage1"

Error 27: Unrecognized command

---

### Post by bodhi.zazen on 2008-10-22
Do not use quotes ;)

```
find /boot/grub/stage1
```

---

### Post by thirdeye420 on 2008-10-22
I didn't

---

### Post by bodhi.zazen on 2008-10-22
Start again.

On the live CD , open a terminal

Enter```
sudo grub
```

You will now get the grub prompt, it looks like this> grub >

At the grub prompt type

```
find /boot/grub/stage1
```

Or you may need

```
find /grub/stage1
```

---

